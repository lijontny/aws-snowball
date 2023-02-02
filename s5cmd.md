# run docker image
$ docker pull peakcom/s5cmd
$ docker run --rm -v ~/.aws:/root/.aws -v /mount_local:/mnt peakcom/s5cmd cp --storage-class=DEEP_ARCHIVE /mnt/test_file s3://<bucket>


# Build and run docker locally
$ git clone https://github.com/peak/s5cmd && cd s5cmd
$ docker build -t s5cmd .
$ docker run --rm -v ~/.aws:/root/.aws -v /mount_local:/mnt s5cmd cp --storage-class=DEEP_ARCHIVE /mnt/test_file s3://<bucket>