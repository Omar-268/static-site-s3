# static-site-s3
This project demonstrates how to use Terraform with LocalStack to host a simple static website on an S3 bucket all running locally without AWS costs.

## Project Architecture
```
static-site-s3/
 ├── main.tf
 ├── provider.tf
 ├── variables.tf
 └── website/
      ├── index.html
      └── error.html
```
## How to run it in your localhost

### Run localstack
```
docker run --rm -it -p 4566:4566 localstack/localstack
```
you can download it from here 
[LocalStack](https://www.localstack.cloud/)

### Initialize Terraform
```
terraform init
terraform plan
terraform apply
```
## Verification
After completing all the steps, you will see that the bucket has been created successfully. 
```
$ aws --endpoint-url=http://localhost:4566 s3 ls s3://my-static-site
2025-09-04 11:49:03        128 error.html
2025-09-04 11:49:03        132 index.html
```

```
$ aws --endpoint-url=http://localhost:4566 s3 cp s3://my-static-site/index.html -
<!DOCTYPE html>
<html>
<head>
  <title>My Static Site</title>
</head>
<body>
  <h1>Welcome to my website 🚀</h1>
</body>
</html>
```
