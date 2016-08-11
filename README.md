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
