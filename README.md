## Sample App for AWS lightsail

Sample Python Flask application to showcase the steps of building and running a web server with Docker.

Docker: https://www.docker.com/  
Flask documentation: https://flask.palletsprojects.com/en/1.1.x/  
AWS Lightsail documentation: https://aws.amazon.com/blogs/aws/lightsail-containers-an-easy-way-to-run-your-containers-in-the-cloud/


### Prerequisite:
1. aws cli installed and configured
2. brew install aws/tap/lightsailctl


### Step 1: Create a container service

```
aws lightsail create-container-service --service-name simple-time-service  --power small --scale 1
```

### Step 2: Create application container and push container image


``` 
aws lightsail push-container-image --service-name simple-time-service --label flask-container --image simple_time
==> get image tag of this newly pushed image
```

### Step 3: Deploy the container

```
aws lightsail create-container-service-deployment --service-name simple-time-service --containers file://containers.json --public-endpoint file://public-endpoint.json
```

### Monitor the deployment
aws lightsail get-container-services --service-name simple-time-service
