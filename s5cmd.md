### run docker image
```shell
docker pull peakcom/s5cmd
docker run --rm -v ~/.aws:/root/.aws -v /mount_local:/mnt peakcom/s5cmd cp --storage-class=DEEP_ARCHIVE /mnt/test_file s3://<bucket>
```


### Build and run docker locally
```shell
git clone https://github.com/peak/s5cmd && cd s5cmd
docker build -t s5cmd .
docker run --rm -v ~/.aws:/root/.aws -v /mount_local:/mnt s5cmd cp --storage-class=DEEP_ARCHIVE /mnt/test_file s3://<bucket>
```

### upload from a list
```shell
docker run --rm -v ~/.aws:/root/.aws -v /mount_local:/mnt --entrypoint /bin/sh s5cmd -c 'for i in `cat /mnt/list.txt`; do /s5cmd cp /mnt/$i s3://<bucket>/; done'
```