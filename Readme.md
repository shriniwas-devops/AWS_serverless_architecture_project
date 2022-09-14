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
docker build -t IMAGE_NAME.
````
3. Create an ECR repository (i.e. sqs_message_reader)
````
aws ecr create-repository --repository-name ECR_REPO
````
4. Login to the ECR with
````
aws ecr get-login-password | docker login --username AWS --password-stdin ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com
````

Replace ACCOUNT_ID / AWS_REGION with your account details
5. Retag the image t with the repository URI that you just created
````
docker tag IMAGE_NAME ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com/ECR_REPO
````
6. Push the image into your ECR repo with
````
docker push ACCOUNT_ID.dkr.ecr.AWS_REGION.amazonaws.com/sqs_message_reader
````