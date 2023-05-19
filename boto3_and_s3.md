### S3
CRUD stands for create read update and delete


- In your python terminal enter the code your folders are in using the `cd` commnad

- Once you have entered your file, run the code ` pip install awscli`

- Once you have installed your awscli you can check if it has installed by looking at the pyhton packages you should see `awscli`

- To configure the awscli run the code `aws configure`

-It will then ask you to enter your; access key, secret access key, region and format

-This should then allow you in, to see all the buckets

- Once your in run the command `aws s3 ls`

- this code will allow you to see all your buckets.

- to move a file to the bucket `aws s3 cp sampletext.txt s3://name of file`

- to download the conetnts of a bucket `aws s3 sync s3:/name of file s3_downloads`

- to delte a file in a bucket `aws s3 rm s3:/name of file/name of file to delete`

- to delete a bucket ` aws s3 rb s3://name of file`

- to delet everything in a bucket `aws s3 rm s3://name of file`


### boto3

-to install boto3 in the terminal run the command `pip install boto3`

- next moving into the python terminal run the command 
`import boto3` to allow you to have acces to the files
` s3 = boto3.resources("s3)` to connect
`for bucket in s3.buckets.all():`
    print(bucket.name)` to access buckets
    
![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/4a0bce96-c155-455e-8f4a-ddd10998708b)


- this command allows you to create a bucket
`import boto3
`s3 = boto3.client("s3")`
`bucket_name = s3.create_bucket(Bucket = "insert your folder name", CreateBucketConfiguration={"LocationConstraint": "eu-west-1"})`
`print(bucket_name)`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/5a41cbc1-705d-4b51-aa4d-4e400eaf51cd)


- thiss command allows you to upload to a bucket
`import boto3`
`connect to s3`
`s3 = boto3.resource("s3")`
`data = open("filename", "rb")`
`s3.Bucket("folder name").put_object(Key="filename", Body=data)`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/887d2c3c-9b87-4569-8262-a1da9666cfb9)


- this command allows you to download from a bucket
`import boto3`
`s3 = boto3.client("s3")`
`s3.download_file("folder name", "file name", "new file name")`
`print(s3.download_file)`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/4991a16f-3f48-441c-aa5f-e48cb9e4c429)

- this command allows you to delet from a bucket as you cant delete a bucket without deleting the contents in the bucket first
`import boto3`
`s3 = boto3.resource("s3")`
`s3.Object("folder name", "file name").delete()`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/6f24cf56-b4c2-4ebb-88d4-3bd1ce12082c)


- this command allows you to delete a bucket
`import boto3`
`s3 = boto3.resource("s3")`
`bucket = s3.Bucket("folder name")`
`response = bucket.delete()`
`print(response)`

![image](https://github.com/MarwahClark/tech230_AWS/assets/133018482/802606b8-2564-4a40-a379-616de154209c)


you can double check if the file has deleted by using the acces code
