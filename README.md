# aws-snowball
## Create a Job
- https://docs.aws.amazon.com/snowball/latest/ug/create-job-ug.html
## Upload data
### Generate a list
1. Install the tool
```commandline
git clone git@github.com:aws-samples/snow-transfer-tool.git
cd snow-transfer-tool/
./install.sh 
```
2. Generate list of files for each device
```commandline
snowTransfer gen_list --src ~/snow --filelist_dir /tmp/output --partition_size 5GB --device_capacity 80TB --log_dir /tmp/lpg
```
###  snowball client
```commandline
curl -O https://snowball-client.s3.us-west-2.amazonaws.com/latest/snowball-client-linux.tar.gz
tar xvfz snowball-client-linux.tar.gz
cd snowball-client-linux/bin
./snowball start -i 192.0.2.0 -m /Downloads/JID2EXAMPLE-0c40-49a7-9f53-916aEXAMPLE81-manifest.bin  -u 12345-abcde-12345-ABCDE-12345
```

### Upload data from list
```commandline
for i in `awk '{print $1}' /tmp/output/device_10.00MiB_2/fl_51FZOH_2.txt`;do snowball cp --recursive $i s3://MyBucket/Logs;done
```
