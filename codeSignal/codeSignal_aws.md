# CODESIGNAL COURSE PATH "Mastering Cloud Engineering with AWS and Python" NOTES

- https://codesignal.com/learn/paths/mastering-cloud-engineering-with-aws-and-python
- https://codesignal.com/learn/course-paths/31

5 Courses:
1. [Introduction to AWS SDK for Python](https://codesignal.com/learn/courses/introduction-to-aws-sdk-for-python)  -- 4 lessons
2. [Mastering Amazon S3 with AWS SDK for Python](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python)  -- 5 lessons
3. [Introduction to DynamoDB with AWS SDK for Python](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python)  -- 6 lessons
4. [Mastering Messaging with AWS SDK for Python](https://codesignal.com/learn/courses/mastering-messaging-with-aws-sdk-for-python)  -- 5 lessons
5. [AWS Secrets Management with AWS SDK for Python](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python)  -- 5 lessons

## [Course 1: Introduction to AWS SDK for Python](https://codesignal.com/learn/courses/introduction-to-aws-sdk-for-python)

### [Lesson 1: Boto3 Essentials: Managing AWS Resources with Python](https://codesignal.com/learn/courses/introduction-to-aws-sdk-for-python/lessons/boto3-essentials-managing-aws-resources-with-python)
- https://codesignal.com/learn/lesson/1984

- boto: python AWS SDK

- for safety of creds: use env vars, AWS config files, or AWS IAM roles
  - generate creds thru AWS Mgmt Console in IAM section
  - if using AWS SSO: temporary creds can be obtained to access AWS services

#### Initiating Secure Sessions

practice 1 demo script: list of services and resources
```py
import boto3

# Create a Boto3 session
session = boto3.session.Session()

# List all available services under client interface
client_services = session.get_available_services()
print("Available services with client interface:")
for service in sorted(client_services):
    print(service)

# List all available services under resource interface
resource_services = session.get_available_resources()
print("\nAvailable services with resource interface:")
for service in sorted(resource_services):
    print(service)
```

output:
```  
Available services with client interface:
accessanalyzer
account
acm
acm-pca
alexaforbusiness
amp
amplify
amplifybackend
amplifyuibuilder
apigateway
apigatewaymanagementapi
apigatewayv2
appconfig
appconfigdata
appfabric
appflow
appintegrations
application-autoscaling
application-insights
applicationcostprofiler
appmesh
apprunner
appstream
appsync
arc-zonal-shift
artifact
athena
auditmanager
autoscaling
autoscaling-plans
b2bi
backup
backup-gateway
backupstorage
batch
bcm-data-exports
bedrock
bedrock-agent
bedrock-agent-runtime
bedrock-runtime
billingconductor
braket
budgets
ce
chatbot
chime
chime-sdk-identity
chime-sdk-media-pipelines
chime-sdk-meetings
chime-sdk-messaging
chime-sdk-voice
cleanrooms
cleanroomsml
cloud9
cloudcontrol
clouddirectory
cloudformation
cloudfront
cloudfront-keyvaluestore
cloudhsm
cloudhsmv2
cloudsearch
cloudsearchdomain
cloudtrail
cloudtrail-data
cloudwatch
codeartifact
codebuild
codecatalyst
codecommit
codedeploy
codeguru-reviewer
codeguru-security
codeguruprofiler
codepipeline
codestar
codestar-connections
codestar-notifications
cognito-identity
cognito-idp
cognito-sync
comprehend
comprehendmedical
compute-optimizer
config
connect
connect-contact-lens
connectcampaigns
connectcases
connectparticipant
controltower
cost-optimization-hub
cur
customer-profiles
databrew
dataexchange
datapipeline
datasync
datazone
dax
detective
devicefarm
devops-guru
directconnect
discovery
dlm
dms
docdb
docdb-elastic
drs
ds
dynamodb
dynamodbstreams
ebs
ec2
ec2-instance-connect
ecr
ecr-public
ecs
efs
eks
eks-auth
elastic-inference
elasticache
elasticbeanstalk
elastictranscoder
elb
elbv2
emr
emr-containers
emr-serverless
entityresolution
es
events
evidently
finspace
finspace-data
firehose
fis
fms
forecast
forecastquery
frauddetector
freetier
fsx
gamelift
glacier
globalaccelerator
glue
grafana
greengrass
greengrassv2
groundstation
guardduty
health
healthlake
honeycode
iam
identitystore
imagebuilder
importexport
inspector
inspector-scan
inspector2
internetmonitor
iot
iot-data
iot-jobs-data
iot1click-devices
iot1click-projects
iotanalytics
iotdeviceadvisor
iotevents
iotevents-data
iotfleethub
iotfleetwise
iotsecuretunneling
iotsitewise
iotthingsgraph
iottwinmaker
iotwireless
ivs
ivs-realtime
ivschat
kafka
kafkaconnect
kendra
kendra-ranking
keyspaces
kinesis
kinesis-video-archived-media
kinesis-video-media
kinesis-video-signaling
kinesis-video-webrtc-storage
kinesisanalytics
kinesisanalyticsv2
kinesisvideo
kms
lakeformation
lambda
launch-wizard
lex-models
lex-runtime
lexv2-models
lexv2-runtime
license-manager
license-manager-linux-subscriptions
license-manager-user-subscriptions
lightsail
location
logs
lookoutequipment
lookoutmetrics
lookoutvision
m2
machinelearning
macie2
managedblockchain
managedblockchain-query
marketplace-agreement
marketplace-catalog
marketplace-deployment
marketplace-entitlement
marketplacecommerceanalytics
mediaconnect
mediaconvert
medialive
mediapackage
mediapackage-vod
mediapackagev2
mediastore
mediastore-data
mediatailor
medical-imaging
memorydb
meteringmarketplace
mgh
mgn
migration-hub-refactor-spaces
migrationhub-config
migrationhuborchestrator
migrationhubstrategy
mobile
mq
mturk
mwaa
neptune
neptune-graph
neptunedata
network-firewall
networkmanager
networkmonitor
nimble
oam
omics
opensearch
opensearchserverless
opsworks
opsworkscm
organizations
osis
outposts
panorama
payment-cryptography
payment-cryptography-data
pca-connector-ad
personalize
personalize-events
personalize-runtime
pi
pinpoint
pinpoint-email
pinpoint-sms-voice
pinpoint-sms-voice-v2
pipes
polly
pricing
privatenetworks
proton
qbusiness
qconnect
qldb
qldb-session
quicksight
ram
rbin
rds
rds-data
redshift
redshift-data
redshift-serverless
rekognition
repostspace
resiliencehub
resource-explorer-2
resource-groups
resourcegroupstaggingapi
robomaker
rolesanywhere
route53
route53-recovery-cluster
route53-recovery-control-config
route53-recovery-readiness
route53domains
route53resolver
rum
s3
s3control
s3outposts
sagemaker
sagemaker-a2i-runtime
sagemaker-edge
sagemaker-featurestore-runtime
sagemaker-geospatial
sagemaker-metrics
sagemaker-runtime
savingsplans
scheduler
schemas
sdb
secretsmanager
securityhub
securitylake
serverlessrepo
service-quotas
servicecatalog
servicecatalog-appregistry
servicediscovery
ses
sesv2
shield
signer
simspaceweaver
sms
sms-voice
snow-device-management
snowball
sns
sqs
ssm
ssm-contacts
ssm-incidents
ssm-sap
sso
sso-admin
sso-oidc
stepfunctions
storagegateway
sts
supplychain
support
support-app
swf
synthetics
textract
timestream-influxdb
timestream-query
timestream-write
tnb
transcribe
transfer
translate
trustedadvisor
verifiedpermissions
voice-id
vpc-lattice
waf
waf-regional
wafv2
wellarchitected
wisdom
workdocs
worklink
workmail
workmailmessageflow
workspaces
workspaces-thin-client
workspaces-web
xray

Available services with resource interface:
cloudformation
cloudwatch
dynamodb
ec2
glacier
iam
opsworks
s3
sns
sqs
```

practice 2 demo script:
```py
import boto3

# Creating a default session and printing its region
default_session = boto3.Session()
print(f"Default session created. Region: {default_session.region_name}")

# Creating a custom session with specified credentials and printing its region
# Note: In a real application, use secure methods to manage your credentials
custom_credentials_session = boto3.Session(
    aws_access_key_id='YOUR_ACCESS_KEY_ID',
    aws_secret_access_key='YOUR_SECRET_ACCESS_KEY',
    region_name='us-east-1' # Specifying a region is optional here but included for demonstration
)
print(f"Custom credentials session created. Region: {custom_credentials_session.region_name}")

# Creating a session with a specified region and printing its region
region_specific_session = boto3.Session(region_name='us-west-2')
print(f"Region-specific session created. Region: {region_specific_session.region_name}")
```

output:
```
Default session created. Region: us-east-1
Custom credentials session created. Region: us-east-1
Region-specific session created. Region: us-west-2
```
- default session: uses your environment's AWS setup, a 
- custom session with specific credentials for enhanced security, and a 
- region-specific session: tailored for operations in a particular geographic area

#### Client vs Resource
```py
import boto3

# You can directly create a client or resource without an explicit session
s3_client = boto3.client('s3')
s3_resource = boto3.resource('s3')

# Uploading a file using a client
with open('path/to/example.txt', 'rb') as file:
    s3_client.upload_fileobj(file, 'my-bucket', 'example.txt')

# Uploading a file using a resource
s3_resource.Bucket('my-bucket').upload_file('path/to/example.txt', 'example.txt')
```


- Create client & resources if non-default configs are needed:

```py
# Creating a session with custom configuration
custom_session = boto3.Session(region_name='us-west-2')

# Using the custom session to create a client
custom_s3_client = custom_session.client('s3')

# Using the custom session to create a resource
custom_s3_resource = custom_session.resource('s3')

# Now you can use custom_s3_client and custom_s3_resource with the settings defined in custom_session
```


### [Lesson 2: Introduction to Boto3 Client Configurations](https://codesignal.com/learn/courses/introduction-to-aws-sdk-for-python/lessons/introduction-to-boto3-client-configurations?courseSlug=introduction-to-aws-sdk-for-python)
- https://codesignal.com/learn/lesson/1985

#### p1 demo code
```py
import boto3
from botocore.config import Config

custom_config = Config(retries={'max_attempts': 3, 'mode': 'standard'})
s3_client = boto3.client('s3', endpoint_url='https://my-test-bucket.com', config=custom_config)
```

### [Lesson 3: Navigating Boto3 Exceptions: Mastering Error Handling in AWS Operations](https://codesignal.com/learn/courses/introduction-to-aws-sdk-for-python/lessons/navigating-boto3-exceptions-mastering-error-handling-in-aws-operations?courseSlug=introduction-to-aws-sdk-for-python)
- https://codesignal.com/learn/lesson/1986

- practice 1 demo script:
```py
import boto3
from botocore.exceptions import BotoCoreError, ClientError

# Create an S3 client
s3_client = boto3.client('s3')

# Try to list objects of non-existent bucket
try:
    response = s3_client.list_objects(Bucket='non-existent-bucket')

# Handle possible errors
except ClientError as e:
    error_code = e.response['Error']['Code']
    if error_code == 'NoSuchBucket':
        print("The bucket does not exist.")
    elif error_code == 'AccessDenied':
        print("You do not have permissions to access the bucket.")
    else:
        print("Unexpected error:", e.response['Error']['Message'])
        # print(f'unexpected error: {error_code}')

# Catch errors within Boto3 itself
except BotoCoreError as e:
    print("Boto3 error:", e)
```


### [Lesson 4: Managing Logs with AWS SDK for Python](https://codesignal.com/learn/courses/introduction-to-aws-sdk-for-python/lessons/managing-logs-with-aws-sdk-for-python?courseSlug=introduction-to-aws-sdk-for-python)
- https://codesignal.com/learn/lesson/1987

#### Python's logging library and Boto3
- set_stream_logger() fn
```py
import boto3
import logging

logging.basicConfig(level=logging.INFO)
boto3.set_stream_logger(name='boto3', level=logging.DEBUG) # log all Boto3 activities
boto3.set_stream_logger(name='botocore.client.S3', level=logging.DEBUG) # focus on one service, i.e. s3 operations
boto3.set_stream_logger(name='botocore', level=logging.DEBUG) # request and response interactions
```

- python logging levels: DEBUG, INFO, WARNING (default), ERROR, CRITICAL

#### p1 demo code

```py
import boto3
import logging

# Set up logging
logging.basicConfig(level=logging.DEBUG)

# Initialize the boto3 S3 resource
s3 = boto3.resource('s3')

# Apply the AWS debug logging filter
boto3.set_stream_logger('boto3', logging.DEBUG)

# Create a new bucket as the initial setup is empty
s3.create_bucket(Bucket='my-logging-test-bucket')

# List buckets to show logging output
for bucket in s3.buckets.all():
    print(bucket.name)
```


## [Course 2: Mastering Amazon S3 with AWS SDK for Python](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python)
### [Lesson 1: Mastering Amazon S3: Creating Sessions and Clients with Boto3](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/mastering-amazon-s3-creating-sessions-and-clients-with-boto3)
- https://codesignal.com/learn/lesson/1988

- Buckets: container for objects (files) in S3. **unique across all of S3**
- Objects: Files -- data, metadata, and a key (object name). **unique within a bucket by key and version ID**.
- Keys: filename. combo of bucket, key, and version ID uniquely identify each object in S3.
- Regions: When creating a bucket, need to specify AWS region where bucket resides.

- custom sessions, with specific credentials and settings, to operate with different AWS configurations or to manage resources across various regions:

```py
# Create a specific AWS session for a different region
session_us_east_1 = boto3.Session(
    aws_access_key_id='ANOTHER_ACCESS_KEY_ID',
    aws_secret_access_key='ANOTHER_SECRET_ACCESS_KEY',
    region_name='us-east-1'
)

# Create a S3 resource and client using the specific session
s3_resource_us_east_1 = session_us_east_1.resource('s3')
s3_client_us_east_1 = session_us_east_1.client('s3')
```

- practice 1 demo script:

```py
import boto3

# Create an AWS session with explicit credentials and region
session = boto3.Session(
    aws_access_key_id='test',
    aws_secret_access_key='test',
    region_name='us-west-2'
)

# Create an S3 resource based on the session
s3_resource = session.resource('s3')

# Print S3 resource details
print("S3 resource: ", s3_resource)

# Create an S3 client based on the session
s3_client = session.client('s3')

# Print S3 client details
print("S3 client: ", s3_client)

# Create a default S3 resource with the default session
# The default session uses credentials and settings from environment variables,
# AWS credentials and config file, or IAM role for Amazon EC2 instances
default_s3_resource = boto3.resource('s3')

# Print default S3 resource details
print("Default S3 resource: ", default_s3_resource)

# Create a default S3 client with the default session
default_s3_client = boto3.client('s3')

# Print default S3 client details
print("Default S3 client: ", default_s3_client)
```

### [Lesson 2: Mastering S3 Bucket Management with AWS SDK for Python](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/mastering-s3-bucket-management-with-aws-sdk-for-python?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)
- https://codesignal.com/learn/lesson/1989



#### p1 demo code

```py
import boto3

s3_resource = boto3.resource('s3')

s3_resource.create_bucket(Bucket='cosmo-galaxy-photos-2024') # Creating bucket in the default us-east-1 region
s3_resource.create_bucket(Bucket='cosmo-widget-data', CreateBucketConfiguration={'LocationConstraint': 'us-west-2'})  # Creating bucket in the us-west-2 region
s3_resource.create_bucket(Bucket='cosmo-doc-archive-2020', CreateBucketConfiguration={'LocationConstraint': 'eu-central-1'})  # Creating bucket in the eu-central-1 region

print("Buckets before deletion:")
for bucket in s3_resource.buckets.all():
    print(bucket.name)

s3_resource.Bucket('cosmo-doc-archive-2020').delete()

print("\nBuckets after deletion:")
for bucket in s3_resource.buckets.all():
    print(bucket.name)
    
"""
Expected output:

Buckets before deletion:
cosmo-galaxy-photos-2024
cosmo-widget-data
cosmo-doc-archive-2020

Buckets after deletion:
cosmo-galaxy-photos-2024
cosmo-widget-data
"""
```

### [Lesson 3: Managing AWS S3 Objects: Upload, Download, and Delete with Python and Boto3](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/managing-aws-s3-objects-upload-download-and-delete-with-python-and-boto3?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)
- https://codesignal.com/learn/lesson/1990

#### p1 demo code
```py
import boto3
import os

# Initialize the boto3 S3 resource
s3 = boto3.resource('s3')

# Create a new bucket as the initial setup is empty
s3.create_bucket(Bucket='photo-archive-2023')

# Upload the image to the 'photo-archive-2023' bucket using the image already in the filesystem
image_path = '/usercode/FILESYSTEM/assets/prompt-engineering-course-logo.jpg'
s3.Bucket('photo-archive-2023').upload_file(image_path, 'prompt-engineering-course-logo.jpg')

# List objects in the bucket before deletion
print("Objects in bucket before deletion:")
for obj in s3.Bucket('photo-archive-2023').objects.all():
    print(obj.key)

# Ensure the downloads folder exists
downloads_folder = '/usercode/FILESYSTEM/downloads'
if not os.path.exists(downloads_folder):
    os.makedirs(downloads_folder)

# Download the image from the bucket to the downloads folder
s3.Bucket('photo-archive-2023').download_file('prompt-engineering-course-logo.jpg', f'{downloads_folder}/prompt-engineering-course-logo.jpg')

# Delete the image from the bucket
s3.Object('photo-archive-2023', 'prompt-engineering-course-logo.jpg').delete()

# List objects in the bucket after deletion
print("\nObjects in bucket after deletion:")
for obj in s3.Bucket('photo-archive-2023').objects.all():
    print(obj.key)
```

#### Uploading Files to s3
```py
import boto3

s3_resource = boto3.resource('s3')
s3_resource.Bucket('cosmo-user-uploads').upload_file('path/to/local/file.jpg', 'cosmo-profile-2023.jpg')
```

#### Listing Objects in s3
```py
for obj in s3_resource.Bucket('cosmo-user-uploads').objects.all():
    print(obj.key)
```

#### Downloading files from s3
```py
s3_resource.Bucket('cosmo-user-uploads').download_file('cosmo-profile-2023.jpg', 'local/path/cosmo-profile.jpg')
```

### Retrieving metadata
```py
# Get the S3 object
cosmo_object = s3_resource.Object('cosmo-images-archive-2023', 'cosmo-profile-2023.jpg')

# Get object's metadata
metadata = cosmo_object.metadata
```

#### Deleting files from s3
```py
# Deleting single object
s3_resource.Object('cosmo-user-uploads', 'temporary-file.jpg').delete()

# Deleting all objects in the bucket
s3_resource.Bucket(bucket_name).objects.all().delete()
```

#### Handling S3 Exceptions Gracefully
```py
import boto3
from botocore.exceptions import ClientError

s3_resource = boto3.resource('s3')

try:
    s3_resource.Bucket('cosmo-user-uploads').delete()
except s3_resource.meta.client.exceptions.NoSuchBucket:
    print("Error: The specified bucket does not exist.")
except ClientError as e:
    # This captures other unexpected errors
    print(f"An unexpected error occurred: {e.response['Error']['Message']}")
```

### [Lesson 4: Mastering Multi-Part Uploads in Amazon S3 with Boto3 and Python](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/mastering-multi-part-uploads-in-amazon-s3-with-boto3-and-python?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)
- https://codesignal.com/learn/lesson/1991

#### p1 demo code

```py
import boto3
import os

# Create the S3 client
s3_client = boto3.client('s3')

# Create a new bucket
bucket_name = 'cosmo-archive-2023'
s3_client.create_bucket(Bucket=bucket_name)

# Path to your dataset
file_path = '/usercode/FILESYSTEM/assets/cosmo-hadoop-course-data-set.zip'
key = 'cosmos-hadoop-course-data-set.zip'

# Initiate multipart upload
multipart_upload = s3_client.create_multipart_upload(Bucket=bucket_name, Key=key)
upload_id = multipart_upload['UploadId']

uploaded_parts = []

# Open the file for reading data
with open(file_path, 'rb') as f:
    # Upload the first chunk
    data = f.read(1024 * 1024 * 5)  # 5MB
    response = s3_client.upload_part(Bucket=bucket_name, Key=key, PartNumber=1, UploadId=upload_id, Body=data)
    uploaded_parts.append({'PartNumber': 1, 'ETag': response['ETag']})

    # Upload the second chunk
    data = f.read(1024 * 1024 * 6)  # 6MB
    response = s3_client.upload_part(Bucket=bucket_name, Key=key, PartNumber=2, UploadId=upload_id, Body=data)
    uploaded_parts.append({'PartNumber': 2, 'ETag': response['ETag']})

    # Upload the final chunk (which is the rest of the file)
    data = f.read()
    response = s3_client.upload_part(Bucket=bucket_name, Key=key, PartNumber=3, UploadId=upload_id, Body=data)
    uploaded_parts.append({'PartNumber': 3, 'ETag': response['ETag']})

# Complete the multipart upload
s3_client.complete_multipart_upload(Bucket=bucket_name, Key=key, UploadId=upload_id, MultipartUpload={'Parts': uploaded_parts})
print("Dataset uploaded successfully in chunks of varying sizes. Multipart upload completed.")
```

#### Start a Multi-part Upload Session
```py
import boto3
import os

# Configure the S3 client
s3_client = boto3.client('s3')
bucket_name = 'my_bucket'
file_path = 'path/to/my_large_file.zip'
key = 'my_large_file.zip'

# Start a multi-part upload session
mpu = s3_client.create_multipart_upload(Bucket=bucket_name, Key=key)
parts = []
upload_id = mpu['UploadId']
```

#### Calculate the Number of Parts and Perform Upload

> **NOTE:** size of each part (except the last): >=5MB && <5GB

```py
# Set the part size to 5 MB
part_size = 1024 * 1024 * 5
# Retrieve the total file size
file_size = os.path.getsize(file_path)
# Calculate the total number of parts needed for the upload
part_count = (file_size + part_size - 1) // part_size

# Open the file in binary read mode
with open(file_path, 'rb') as f:
    # Iterate over each part
    for part_no in range(1, part_count + 1):
        # Read the specified part size from the file
        data = f.read(part_size)
        # Upload the part to S3 and receive a response containing the ETag
        response = s3_client.upload_part(Bucket=bucket_name, Key=key, PartNumber=part_no, UploadId=upload_id, Body=data)
        # Append the part number and ETag to the 'parts' list for later reference in completing the upload
        parts.append({'PartNumber': part_no, 'ETag': response['ETag']})
```

#### Complete the multi-part upload
```py
s3_client.complete_multipart_upload(Bucket=bucket_name, Key=key, UploadId=upload_id, MultipartUpload={'Parts': parts})
```


#### practice 2 multi-part upload code all together:
```py
import boto3
import os

# Initialize the S3 client
s3_client = boto3.client('s3')

# Create a new bucket for your uploads
bucket_name = 'cosmo-archive-2023'
s3_client.create_bucket(Bucket=bucket_name)

# Path to your dataset
file_path = '/usercode/FILESYSTEM/assets/cosmo-hadoop-course-data-set.zip'
key = 'cosmos-hadoop-course-data-set.zip'


# TODO: Initiate a multipart upload session
mpu = s3_client.create_multipart_upload(Bucket=bucket_name, Key=key)
uploaded_parts = []
upload_id = mpu['UploadId']
part_size = 1024*1024*5
file_size = os.path.getsize(file_path)
part_count = (file_size + part_size -1 ) // part_size
# TODO: Upload the dataset in 5 MB chunks using a loop
with open(file_path, 'rb') as f:
    for part_no in range(1, part_count + 1):
        data = f.read(part_size)
        response = s3_client.upload_part(Bucket=bucket_name, Key=key, PartNumber=part_no, UploadId=upload_id, Body=data)
        uploaded_parts.append({'PartNumber': part_no, 'ETag': response['ETag']})
        # data = f.read()
# TODO: Complete the multipart upload by combining all the uploaded parts
s3_client.complete_multipart_upload(Bucket=bucket_name, Key=key, UploadId=upload_id, MultipartUpload={'Parts': uploaded_parts})
```

### [Lesson 5: Mastering File Versioning and Management in Amazon S3 with Boto3](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/mastering-file-versioning-and-management-in-amazon-s3-with-boto3?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)
- https://codesignal.com/learn/lesson/1992

#### p1 demo code
```py
import boto3

# Initialize the Boto3 S3 resource and client
s3_resource = boto3.resource('s3')
s3_client = boto3.client('s3')

# Create the bucket 'cosmo-archive-data' with versioning enabled
bucket_name = 'cosmo-archive-data'
bucket = s3_resource.create_bucket(Bucket=bucket_name)

# Enable versioning for the 'cosmo-archive-data' bucket
s3_resource.BucketVersioning(bucket_name).enable()

# Upload 'version1.txt' and print its version ID
obj_key = 'versioned_document.txt'
obj_v1 = bucket.Object(obj_key)
response_v1 = obj_v1.put(Body='This is the content of version 1.')
print(f"Uploaded 'version1.txt' with version ID: {response_v1['VersionId']}")

# Upload 'version2.txt' and print its version ID
obj_v2 = bucket.Object(obj_key)
response_v2 = obj_v2.put(Body='This is the content of version 2.')
print(f"Uploaded 'version2.txt' with version ID: {response_v2['VersionId']}")

# Retrieve the latest version of the document without specifying the version ID
latest_version = bucket.Object(obj_key).version_id
print(f"Retrieved latest version of 'versioned_document.txt': {latest_version}")

# Retrieve and print 'version1.txt' using its version ID
specific_version = s3_client.get_object(
    Bucket=bucket_name,
    Key=obj_key,
    VersionId=response_v1['VersionId']
)
print(f"Retrieved 'versioned_document.txt' with a specific version ID: {response_v1['VersionId']}")

# Download and print 'version1.txt' using its version ID
s3_client.download_file(bucket_name, obj_key, 'version1.txt', ExtraArgs={'VersionId': response_v1['VersionId']})

# Now, let's open and print the content of the downloaded file.
with open('version1.txt', 'r') as file:
    print(file.read())

# Download the latest version
s3_resource.Bucket(bucket_name).download_file(Key=obj_key, Filename='latest_version.txt')

# Now, let's open and print the content of the downloaded latest version file.
with open('latest_version.txt', 'r') as file:
    print(file.read())
```


```py
import boto3

# Create a session with your AWS credentials
session = boto3.Session(
    aws_access_key_id='your_access_key',
    aws_secret_access_key='your_secret_key',
)

# Enable versioning on a bucket
s3_resource = session.resource('s3')
bucket_versioning = s3_resource.BucketVersioning('my_bucket')
bucket_versioning.enable()


# Suspending versioning on a bucket
bucket_versioning.suspend()
print('Bucket versioning has been suspended.')


# get status
versioning_status = bucket_versioning.status
print('Versioning Status:', versioning_status)
# Enabled/Suspended/None


# Uploading Objects to Version-Enabled Buckets
# uploading a file:
filename = 'example.txt'
bucket_name = 'my_bucket'
s3_resource.Bucket(bucket_name).upload_file(Filename=filename, Key=filename)
print(f'{filename} has been uploaded.')

# directly putting contents into an object:
content = "Hello, World!"
s3_resource.Object(bucket_name, 'example.txt').put(Body=content)
print('Content has been directly uploaded.')



# Retrieving and Downloading Objects from Version-Enabled Buckets
# just get latest version object:
obj = s3_resource.Object(bucket_name, filename).get()
print('Retrieved latest object version:', obj)


# dl with specifying key & filename:
downloaded_file = 'downloaded_example.txt'
s3_resource.Bucket(bucket_name).download_file(Key=filename, Filename=downloaded_file)
print(f'{filename} has been downloaded as {downloaded_file}.')


# retrieve the specific version of an object:
# Retrieving a specific version of an object using the client interface
s3_client = session.client('s3')
response_v1 = s3_client.get_object(Bucket='my_bucket', Key='example.txt', VersionId='your_version_id_here')
print('Retrieved specific object version:', response_v1)

# Reading the content of the retrieved object version
content = response_v1['Body'].read().decode('utf-8')
print('Content of the retrieved version:', content)


# Downloading a specific version of the object

#  download the specified version directly to a file with `download_file` method (specify ExtraArgs & VersionId):
s3_client.download_file('my_bucket', 'example.txt', 'example_specific_version.txt', ExtraArgs={'VersionId': response_v1['VersionId']})
print('Specific version of the object has been downloaded as example_specific_version.txt.')


# Listing Available Versions of an Object
s3_client = session.client('s3')
versions = s3_client.list_object_versions(Bucket='my_bucket', Prefix='example.txt')

for version in versions.get('Versions', []):
    print('Key:', version['Key'], 'VersionId:', version['VersionId'], 'LastModified:', version['LastModified'], 'IsLatest:', version['IsLatest'])

```

#### U5P4

```py
import boto3
import os
from pprint import pprint

# Create S3 resource
s3 = boto3.resource('s3')
s3_client = boto3.client('s3')

# Ensure that /usercode/FILESYSTEM/downloads folder exists
downloads_folder = "/usercode/FILESYSTEM/downloads"
os.makedirs(downloads_folder, exist_ok=True)

# Create S3 bucket called `cosmo-course-logos`
bucket_name = 'cosmo-course-logos'
s3.create_bucket(Bucket=bucket_name)

# Enable versioning for created bucket
s3.BucketVersioning(bucket_name).enable()

# Upload "/usercode/FILESYSTEM/assets/data-science-python-course-logo.jpg" to the bucket under object name "versioned-course-logo.jpg"
s3_client.upload_file(Filename='/usercode/FILESYSTEM/assets/data-science-python-course-logo.jpg', Bucket=bucket_name, Key='versioned-course-logo.jpg')

# Upload "/usercode/FILESYSTEM/assets/machine-learning-course-logo.jpg" to the bucket under object name "versioned-course-logo.jpg"
s3_client.upload_file(Filename='/usercode/FILESYSTEM/assets/machine-learning-course-logo.jpg', Bucket=bucket_name, Key='versioned-course-logo.jpg')

# TODO: Retrieve all version ids for the 'versioned-course-logo.jpg'. Remember, the first version uploaded will be the last in the list due to reverse order.
versions = s3_client.list_object_versions(Bucket=bucket_name, Prefix='versioned-course-logo.jpg')
for version in versions.get('Versions', []):
    print('Key:', version['Key'], 'VersionId:', version['VersionId'], 'LastModified:', version['LastModified'], 'IsLatest:', version['IsLatest'])
# print(versions[-1]['VersionId'])
pprint(versions)
    
# TODO: Download the earliest version of 'versioned-course-logo.jpg' to the '/usercode/FILESYSTEM/downloads/' folder
s3_client.download_file(bucket_name, 'versioned-course-logo.jpg', '/usercode/FILESYSTEM/downloads/versioned-course-logo.jpg', ExtraArgs={'VersionId': 'AZc82fqxrl_G7URJTS4d.WEn5pip5x1U'})
```

## [Course 3: Introduction to DynamoDB with AWS SDK for Python](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python)

### [Lesson 1: Setting Up Your DynamoDB Environment with Boto3 in Python](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python/lessons/setting-up-your-dynamodb-environment-with-boto3-in-python?courseSlug=introduction-to-dynamodb-with-aws-sdk-for-python)

- DynamoDB key concepts:
  - tables: each table item has unique PK requirement.
  - items: each table record, one or more attributes, no strict schema req besides PK.
  - attributes: key-value pair, data field within an item. Each can have different schemas.

#### Creating an AWS Session using Boto3

```py
import boto3

# Create an AWS session with explicit credentials and region
session = boto3.Session(
    aws_access_key_id='YOUR_ACCESS_KEY_ID',
    aws_secret_access_key='YOUR_SECRET_ACCESS_KEY',
    region_name='us-west-2'
)
```

#### Setting Up DynamoDB with Boto3

1. client interface: low-level access with methods closely mirroring the AWS API, ideal for detailed management tasks
2. resource interface: higher-level, object-oriented approach, simplifying interactions by representing AWS services as objects

```py
import boto3

# Create a default DynamoDB resource and client (with the default session)
default_dynamodb_resource = boto3.resource('dynamodb')
default_dynamodb_client = boto3.client('dynamodb')
```
- create multiple sessions when managing DynamoDB tables across different regions or using multiple AWS accounts -- allows configuring each session with specific credentials and settings

```py
# Create a specific AWS session for a different region
session_us_east_1 = boto3.Session(
    aws_access_key_id='ANOTHER_ACCESS_KEY_ID',
    aws_secret_access_key='ANOTHER_SECRET_ACCESS_KEY',
    region_name='us-east-1'
)

# Create a DynamoDB resource and client using the specific session
dynamodb_resource_us_east_1 = session_us_east_1.resource('dynamodb')
dynamodb_client_us_east_1 = session_us_east_1.client('dynamodb')
```

### [Lesson 2: Creating and Configuring DynamoDB Tables with AWS SDK for Python](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python/lessons/creating-and-configuring-dynamodb-tables-with-aws-sdk-for-python?courseSlug=introduction-to-dynamodb-with-aws-sdk-for-python)

- PK: 
  - partition key: Hash key
  - sort key (AKA range key)
- Data types:
  - scalar:
    - string (S)
    - number (N)
    - boolean (BOOL)
    - NULL
  - document:
    - map (M)
    - list (L)
  - Set:
    - string set (SS)
    - number set (NS)
    - binary set (BS)

- DynamoDB capacity modes:
  1. provisioned:
    - specify reads&writes/sec
    - for predictable traffic
    - eligible for AWS free tier
    - Read Capacity Unit (RCU): Provides enough capacity to perform one strongly consistent read per second, or two eventually consistent reads per second, for an item up to 4 KB in size.
      - eventual consistency: costs 1/2 the RCU as strong consistency
    - Write Capacity Unit (WCU): Provides enough capacity to perform one write per second for an item up to 1 KB in size.
  2. on-demand

#### Create DynamoDB table using Provisioned Throughput with a composite primary key

```py
import boto3

dynamodb = boto3.resource('dynamodb')  # Initialize the DynamoDB service

# Create a table with Provisioned Throughput and a composite primary key
table_provisioned = dynamodb.create_table(
    TableName='Users',
    KeySchema=[
        {'AttributeName': 'username', 'KeyType': 'HASH'},  # Partition key
        {'AttributeName': 'signup_date', 'KeyType': 'RANGE'}  # Sort key
    ],
    AttributeDefinitions=[
        {'AttributeName': 'username', 'AttributeType': 'S'},  # String type
        {'AttributeName': 'signup_date', 'AttributeType': 'S'}  # String type
    ],
    ProvisionedThroughput={'ReadCapacityUnits': 5, 'WriteCapacityUnits': 5}  # Specify capacity
)
```
- attributes used as part of PK (i.e. partition or sort key) **must be** included in AttributeDefinitions.
  - attr's not part of PK don't need to be defined in AttributeDefinitions unless involved in indexing or require specific type validation for operations -- allows DynamoDB to maintain flexible schema while eunsring that key attributes have defined data types for efficient indexing and querying.

- on demand capacity mode ex:
```py
import boto3

dynamodb = boto3.resource('dynamodb')

table_on_demand = dynamodb.create_table(
    TableName='Customers',
    KeySchema=[{'AttributeName': 'customer_id', 'KeyType': 'HASH'}],
    AttributeDefinitions=[{'AttributeName': 'customer_id', 'AttributeType': 'S'}],
    BillingMode='PAY_PER_REQUEST'
)
```

#### DyanmoDB Waiters
```py
import boto3

# Initialize the boto3 DynamoDB service
dynamodb = boto3.resource('dynamodb')

waiter = dynamodb.meta.client.get_waiter('table_exists')

# Configure the waiter to wait for up to 300 seconds (5 minutes), polling every 20 seconds
waiter.wait(TableName='ExampleTable', WaiterConfig={'Delay': 20, 'MaxAttempts': 15})

print("Table is now active and ready for use.")

# ==OR== Wait until the table exists, using default settings
table.wait_until_exists()
```

#### list all DynamoDB tables
```py
import boto3

# Initialize the boto3 DynamoDB service
dynamodb = boto3.resource('dynamodb')

print("Existing tables:", [table.name for table in dynamodb.tables.all()])


```


### [Lesson 3: Creating Data in DynamoDB: Inserting Items with PutItem and BatchWriteItem Operations](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python/lessons/creating-data-in-dynamodb-inserting-items-with-putitem-and-batchwriteitem-operations?courseSlug=introduction-to-dynamodb-with-aws-sdk-for-python)

### [Lesson 4: Mastering Data Retrieval in DynamoDB: GetItem and BatchGetItem](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python/lessons/mastering-data-retrieval-in-dynamodb-getitem-and-batchgetitem?courseSlug=introduction-to-dynamodb-with-aws-sdk-for-python)

### [Lesson 5: Manipulating Data in DynamoDB: Update and Delete Operations](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python/lessons/manipulating-data-in-dynamodb-update-and-delete-operations?courseSlug=introduction-to-dynamodb-with-aws-sdk-for-python)

```py
import boto3
# delete table getting table resource then calling delete() method on it:
dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table('Products')
table.delete()


# use delete_table() on/directly with low-level client:
client = boto3.client('dynamodb')
client.delete_table(TableName='ExampleTable')

```

### [Lesson 6: Retrieving Multiple Objects Efficiently in DynamoDB](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python/lessons/retrieving-multiple-objects-efficiently-in-dynamodb?courseSlug=introduction-to-dynamodb-with-aws-sdk-for-python)



## [Course 4: Mastering Messaging with AWS SDK for Python](https://codesignal.com/learn/courses/mastering-messaging-with-aws-sdk-for-python)

### [Lesson 1: Mastering AWS Messaging Fundamentals with Boto3](https://codesignal.com/learn/courses/mastering-messaging-with-aws-sdk-for-python/lessons/mastering-aws-messaging-fundamentals-with-boto3?courseSlug=mastering-messaging-with-aws-sdk-for-python)

### [Lesson 2: Creating and Configuring SQS Queues with Boto3](https://codesignal.com/learn/courses/mastering-messaging-with-aws-sdk-for-python/lessons/creating-and-configuring-sqs-queues-with-boto3?courseSlug=mastering-messaging-with-aws-sdk-for-python)

### [Lesson 3: Mastering SQS Operations: Sending, Receiving, and Deleting Messages](https://codesignal.com/learn/courses/mastering-messaging-with-aws-sdk-for-python/lessons/mastering-sqs-operations-sending-receiving-and-deleting-messages?courseSlug=mastering-messaging-with-aws-sdk-for-python)

### [Lesson 4: Creating and Configuring AWS SNS Topics with Python and Boto3](https://codesignal.com/learn/courses/mastering-messaging-with-aws-sdk-for-python/lessons/creating-and-configuring-aws-sns-topics-with-python-and-boto3?courseSlug=mastering-messaging-with-aws-sdk-for-python)

### [Lesson 5: Mastering AWS Messaging: Sending and Receiving Messages with SNS and SQS](https://codesignal.com/learn/courses/mastering-messaging-with-aws-sdk-for-python/lessons/mastering-aws-messaging-sending-and-receiving-messages-with-sns-and-sqs?courseSlug=mastering-messaging-with-aws-sdk-for-python)


## [Course 5: AWS Secrets Management with AWS SDK for Python](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 1: Securing AWS Resources: An Introduction to AWS Secrets Manager, SSM, and KMS](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/securing-aws-resources-an-introduction-to-aws-secrets-manager-ssm-and-kms?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 2: Mastering AWS Secrets Manager with Boto3: Creating, Retrieving, and Rotating Secrets](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/mastering-aws-secrets-manager-with-boto3-creating-retrieving-and-rotating-secrets?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 3: Advanced Secrets Management in AWS with Python SDK](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/advanced-secrets-management-in-aws-with-python-sdk?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 4: Managing Secrets and Configurations with AWS SSM Parameter Store](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/managing-secrets-and-configurations-with-aws-ssm-parameter-store?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 5: Managing Encryption Keys with AWS KMS and Boto3](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/managing-encryption-keys-with-aws-kms-and-boto3?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

