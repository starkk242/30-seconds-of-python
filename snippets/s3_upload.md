---
title: s3_upload
tags: utility,aws
---

Snippet to upload file to a s3 bucket

- This function will use the boto3 library to connect and transfer files to s3 bucket.
- In the upload_files function there is two other function used for one used to fetch bucket name second for uploading file.
- Just by providing the file directory this function will upload the file to bucket which is available on s3 server.
- This will only work if only one bucket is present on the s3 server
- Before using this snippet execute command pip install boto3 for dependencies
- Insert access and secret keys in the snippet.

```py
def upload_files(file_path):
    import boto3

    def get_bucket():
            for bucket in s3.buckets.all():
                    return (bucket.name)

    def send_file(file_name,file_dir):
            #s3.create_bucket(Bucket= bucket_name) # For creating bucket
            s3.Object(bucket_name,file_name).upload_file(Filename=file_dir)

    s3 = boto3.resource(
        service_name='s3',
        endpoint_url = 'https://s3.eu-central-1.wasabisys.com', # Access Endpoint of s3 server, Provided link is for wasabi
        aws_access_key_id='', # Access Keys for the bucket
        aws_secret_access_key='' # Secret Keys for the bucket
    )

    bucket_name=get_bucket()
    
    send_file(file_path,file_path)
```

```py
upload_files(file_dir)
```
