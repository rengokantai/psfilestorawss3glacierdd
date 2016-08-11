# psfilestorawss3glacierdd
######8 Upload to s3
naming criteria:
can contain lowercase letters, numbers ,periods and hyphens  
must start with number or letter  
must 3-32,no ip address  
not end with hyphen  
cannot contain two adjacent periods  
dashes cannot next to periods  
######create metadata
Key: x-amz-meta-location Value:Sydney
######9 Using powershell 
```
$photo = ".\ke.jpg"
$key = "images/ke/jpg"
Write-S3Object -BucketName ke -File $photo -Key $key -CannedACLName authenticated-read -StorageClass STANDARD_IA -Metadata @{location = "NewYork"}
```
######10
only install awssdk, s3
```
Install-Package AWSSDK.S3
```
######11
strategy:reverse object ID
```
11
12
13
```
chnage to
```
11
21
31
```
to reduce burst
######14
```
$psversiontable
```
```
S3-GetObject -BucketName ke -Key 123 
```
download a image:
```
Copy-S3Object -BucketName ke -Key 123 -LocalFile c:\ke.jpg
```
######16
caching. create another bucket to store thumbnail images.  
If thumb exists: redirect to thumbnail bucket. else do image resizing.
some methods in c#
```
var segments = str.Split('/').ToList();
segments.Insert(2,$"{a}x{b}");
return string.Join("/",segments);
```
test whether object exist in a bucket
```
public async Task<bool> ImageExists(string bucketName,string objectKey){
try{
GetObjectMetadataRequest request = new GetObjectMetadataRequest{
BucketName= bucketName,Key=objectKey};
}catch(AmazonS3Exception){
return false;
}
}
```
