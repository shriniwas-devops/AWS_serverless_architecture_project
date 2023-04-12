PROJECT ARCHITECTURE:


<img width="1075" alt="fghfghfghfghj" src="https://user-images.githubusercontent.com/122585172/230899409-38fcfe52-b8b5-414f-be01-654b4ffc54f0.png">


PREREQUISITES:

- Microservices
- Serverless Architecture
- AWS Lambda Function
- Amazon Simle Queue Service (SQS)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Container Service (Amazon ECS)
- Amazon DynamoDB Database
- Amazon API Gateway









# Create an S3 bucket


keep the bucket name for future reference

# Create an Dynamodb table
Use id as a PRIMARY KEY and type would be Number

keep the table name for future reference

# Create SQS
Keep the SQS Name for future referencesss

# API Gateway

Dummy payload:

````
{
    "Customer": "Aseef Ahmed",
    "OrderId": 1,
    "OrderDate": "2021-09-25T23:28:15",
    "OrderAmount": "200USD",
    "OrderStatus": "PAID"
}
````

# Build Microservice
1. go to the directory 'microservices/sqs_message_reader'
2. Build the docker image with
````
sudo docker build -t IMAGE_NAME.
````
3. Create an ECR repository (i.e. sqs_message_reader)
````
aws ecr create-repository --repository-name ECR_REPO
````
4. Login to the ECR with
````
aws ecr get-login-password | sudo docker login --username AWS --password-stdin ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com
````

Replace ACCOUNT_ID / AWS_REGION with your account details
5. Retag the image t with the repository URI that you just created
````
sudo docker tag IMAGE_NAME ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com/ECR_REPO
````
6. Push the image into your ECR repo with
````
sudo docker push ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com/sqs_message_reader

````

# Create ECS Task Defination
use the image that you uploaded into ECR

# Create ECS Service
- use platform version 1.3.0 

# Load Test
Run the following script to load test. Make sure replace the variable API_URI in the script

````
./scripts/load-test.sh
````
