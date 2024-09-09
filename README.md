# AudioToText
This code converts an audio file to text transcript using a serveless architectutre which use the flow , An audio file uploadee to Amazon S3 which invokes an event to trigger a AWS Lambda which uses Amazon Transcribe to conver the audio file to text transcript.You can use this to capture the meeting details in transcipt and later use for analysis. The Architecture diagram shown below:
![image](https://github.com/user-attachments/assets/eb7057dc-656c-4df0-b8e5-3c6d01c45c47)

The code contains the cloudformation templates which will create the S3Bucket and event notication on file upload of mp3 , you can extend to other files with the suffix option a, Lambda Role and  AWS Lambda Function which will process the file from S3 and put the transcript out to the S3Bucket 

The AWS Lambda code is written in Python and the source code is available in the Python folder , this is pacakaged as a zip packagae with the dependency. The code uses boto3 . Python folder contain the Lambdacode in the file named lambda_function.py . If you cahnge the source code you can create the zip package , the directory is named python . Navigate to the Project directory cd Python

Create a new directory named package install the noto3 dependency mkdir package pip install --target ./package boto3

Create a .zip file with the installed libraries at the root project cd package zip -r ../my_deployment_package.zip .

Add the lambda_function.py file to the root of the .zip file cd .. zip my_deployment_package.zip lambda_function.py

Upload the .zip package to the S3 Bucket and pass the reference to the cloudformation template , cloudformation template will create the lambda function from the zip pacakge.

Upload Template Files from the cfn folder to S3 Bucket:

aws s3 cp . s3://my-bucket/cfntemplate.yaml/ --recursive

CloudFormation Stack Creation:

aws cloudformation create-stack
--stack-name datavalidator
--template-url https://my-bucket.s3.region.amazonaws.com/datavalidator/cfntemplate.yaml
--capabilities CAPABILITY_NAMED_IAM
