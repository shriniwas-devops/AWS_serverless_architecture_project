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
docker build -t sqs_message_reader .
````
3. Create an ECR repo
