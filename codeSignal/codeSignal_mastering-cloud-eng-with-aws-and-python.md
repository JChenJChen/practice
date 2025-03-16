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




### [Lesson 3: Navigating Boto3 Exceptions: Mastering Error Handling in AWS Operations](https://codesignal.com/learn/courses/introduction-to-aws-sdk-for-python/lessons/navigating-boto3-exceptions-mastering-error-handling-in-aws-operations?courseSlug=introduction-to-aws-sdk-for-python)

### [Lesson 4: Managing Logs with AWS SDK for Python](https://codesignal.com/learn/courses/introduction-to-aws-sdk-for-python/lessons/managing-logs-with-aws-sdk-for-python?courseSlug=introduction-to-aws-sdk-for-python)

## [Course 2: Mastering Amazon S3 with AWS SDK for Python](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python)
### [Lesson 1: Mastering Amazon S3: Creating Sessions and Clients with Boto3](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/mastering-amazon-s3-creating-sessions-and-clients-with-boto3?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)

### [Lesson 2: Mastering S3 Bucket Management with AWS SDK for Python](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/mastering-s3-bucket-management-with-aws-sdk-for-python?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)


### [Lesson 3: Managing AWS S3 Objects: Upload, Download, and Delete with Python and Boto3](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/managing-aws-s3-objects-upload-download-and-delete-with-python-and-boto3?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)


### [Lesson 4: Mastering Multi-Part Uploads in Amazon S3 with Boto3 and Python](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/mastering-multi-part-uploads-in-amazon-s3-with-boto3-and-python?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)


### [Lesson 5: Mastering File Versioning and Management in Amazon S3 with Boto3](https://codesignal.com/learn/courses/mastering-amazon-s3-with-aws-sdk-for-python/lessons/mastering-file-versioning-and-management-in-amazon-s3-with-boto3?courseSlug=mastering-amazon-s3-with-aws-sdk-for-python)



## [Course 3: Introduction to DynamoDB with AWS SDK for Python](https://codesignal.com/learn/courses/introduction-to-dynamodb-with-aws-sdk-for-python)


## [Course 4: Mastering Messaging with AWS SDK for Python](https://codesignal.com/learn/courses/mastering-messaging-with-aws-sdk-for-python)


## [Course 5: AWS Secrets Management with AWS SDK for Python](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 1: Securing AWS Resources: An Introduction to AWS Secrets Manager, SSM, and KMS](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/securing-aws-resources-an-introduction-to-aws-secrets-manager-ssm-and-kms?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 2: Mastering AWS Secrets Manager with Boto3: Creating, Retrieving, and Rotating Secrets](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/mastering-aws-secrets-manager-with-boto3-creating-retrieving-and-rotating-secrets?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 3: Advanced Secrets Management in AWS with Python SDK](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/advanced-secrets-management-in-aws-with-python-sdk?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 4: Managing Secrets and Configurations with AWS SSM Parameter Store](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/managing-secrets-and-configurations-with-aws-ssm-parameter-store?courseSlug=aws-secrets-management-with-aws-sdk-for-python)

### [Lesson 5: Managing Encryption Keys with AWS KMS and Boto3](https://codesignal.com/learn/courses/aws-secrets-management-with-aws-sdk-for-python/lessons/managing-encryption-keys-with-aws-kms-and-boto3?courseSlug=aws-secrets-management-with-aws-sdk-for-python)