| Error | Solution |
|-------|----------|
|ERROR org.apache.bookkeeper.bookie.Bookie - Not all the new directories are empty. New directories that are not empty are: [data/standalone/bookkeeper0/current, data/standalone/bookkeeper0/current]|sudo rm /var/lib/docker/volumes/pulsar_lab_pulsar_data/_data/standalone/bookkeeper0/current/ -rf|
