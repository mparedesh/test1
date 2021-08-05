# Flugel Challenge AWS S3

## This repo was created with the next instructions:
1. Create Terraform code to create an AWS S3 bucket with two files: test1.txt and test2.txt. The content of these files must be the timestamp when the code was executed.
2. Using Terratest, create the test automation for the Terraform code, validating that both files and the bucket are created successfully. 
3. Setup Github Actions to run a pipeline to validate this code.
4. Publish your code in a public GitHub repository, and share a Pull Request with your code. Do not merge into master until the PR is approved.
5. Include documentation describing the steps to run and test the automation.
<br />

## Configuration
<br />

**Before execute the code, it's necessary configure the next environment variables:**

<br /><br />

| Windows version:|
| ------------ |
| set TF_VAR_AWS_DEFAULT_REGION=XXXXX|
| set TF_VAR_AWS_ACCESS_KEY_ID=XXXXX |
|set TF_VAR_AWS_SECRET_ACCESS_KEY=XXXXX |

<br />

| Linux version:|
| ------------ |
| export TF_VAR_AWS_DEFAULT_REGION=XXXXX|
| export TF_VAR_AWS_ACCESS_KEY_ID=XXXXX |
|export TF_VAR_AWS_SECRET_ACCESS_KEY=XXXXX |

<br />

- TF_VAR_AWS_DEFAULT_REGION - must content the AWS Region where the S3 bucket will be created
- TF_VAR_AWS_ACCESS_KEY_ID must content the IAM User AWS Access Key ID
- TF_VAR_AWS_SECRET_ACCESS_KEY must content the IAM User Secret Access Key


**To run the code you must  execute the next commands:**
<br /><br />

| Terraform commands:|
| ------------ |
| cd code|
| terraform init|
| terraform plan|
| terraform apply |
| terraform destroy (if you want to reverse the created AWS resources) |

<br />

## Test

For test the code you can use the terratest go script ("flugel_s3_test.go") to create the bucket, the bucket objects, check the correct filenames and finally destroy the created resources. Execute the next comands:
<br /><br />

| Go commands:|
| ------------ |
| cd test|
| go mod init "github.com/mparedesh/test1"|
| go get -v -t -d|
| go mod tidy|
| go test -v|


<br />

# Github Action Pipeline

It's necessary to create three repo secrets as show follow:
<br /><br />

| Repo Secrets:|
| ------------ |
| AWS_DEFAULT_REGION|
| AWS_ACCESS_KEY_ID|
| AWS_SECRET_ACCESS_KEY|

<br />

- TF_VAR_AWS_DEFAULT_REGION - must content the AWS Region where the S3 bucket will be created
- TF_VAR_AWS_ACCESS_KEY_ID must content the IAM User AWS Access Key ID
- TF_VAR_AWS_SECRET_ACCESS_KEY must content the IAM User Secret Access Key


# License

GNU General Public Licensed. See LICENSE for full details.