# Very simple benchmark for web applications

## Parameters:

1 - server address

2 - times to repeat the test(**default: 10**)

3 - time(in seconds) to run each test(**default: 2**)

## Example

With default parameters

```bash
benchmark http://localhost:8000/
```

Repeat the tests 5 times

```bash
benchmark http://localhost:8000/ 5
```

Repeat the tests 5 times and run each test for 10 seconds

```bash
benchmark http://localhost:8000/ 5 10
```

## Function code

```bash
function benchmark() {
  address=${1}
  repeat=${2:10}
  run_benchmark_step_for=${3:-2}
  export sum=0;
  export total=0;
  export max=0;
  export min=0;
  for i in $(seq 1 ${repeat}); do
    hits=$(siege -b -c 100 -t ${run_benchmark_step_for}S ${address} |& grep -iE "^transactions:" | awk '{print($2)}') && \
    echo "${hits} hits"
    sum=$(echo ${sum}+${hits} | bc) && \
    total=$(echo ${total}+1 | bc)
    # Save the max to calculate the median
    if [[ "${hits}" > "${max}" ]]; then
      max=${hits}
    fi
    # Save the min to calculate the median
    if [[ "${hits}" < "${min}" || "${min}" == 0 ]]; then
      min=${hits}
    fi
  done
  echo "average: " $(echo ${sum} / ${total} | bc)
  echo "median: " $(echo "( ${max} + ${min} ) / 2" | bc)
}
```
