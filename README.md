# DockerInAWS

## Basic AWS linux box.

#### 1. Steps to get the instance assigned name in your AWS EC2 shell.

1. Create a user for AWS from [IAMUSER](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)
2. Save your ```AWS Access Key ID``` and ```AWS Secret Access Key``` for you IAMUSER.
3. ssh into AWS EC2 and add the below to your __~/.bash_profile__ of __ec2_user__.
 - __As per AWS docs You must specify an AWS Region when using the AWS CLI, either explicitly or by setting a default Region. For a list of the available Regions, see [Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html).__
```
  export REGION=ap-south-1
  export AWS_INSTANCE_ID=`curl -s http://169.254.169.254/latest/meta-data/instance-id`
  export EC2_NAME=$(aws ec2 describe-tags --region $REGION --filters "Name=resource-id,Values=$AWS_INSTANCE_ID" "Name=key,Values=Name" --output text | cut -f5)
```
4. Reload the bash profile with ```source ~/.bash_profile```
