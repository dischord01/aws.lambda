# aws.lambda

This role allows you to create AWS IAM Assume Role and Policy for deploying AWS Lambda functions. 

## Requirements

```
pip install aws-cli
```

## Usage 

To use this role you first need to export your AWS API keys 

```
export AWS_ACCESS_KEY_ID="AAAAAAAAAAAAAAAAAAAA"
export AWS_SECRET_ACCESS_KEY="SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS"
```

Then add your Lambda function to the `templates` folder. 

Edit the `vars/main.yml` file to add the name of your AWS Lambda function.

```
lambda_function_name: "MyCoolLambdaFunction"
``` 

Example Playbook to run `aws.lambda` role:

```
- name: Deploy Lambda Function
  hosts: localhost
  become: no
  roles:
    - { role: aws.lambda }
```

Then run the playbook. 

```
ansible-playbook -i inventory aws_lambda.yml
```

### Lambda Cron

After you deployed the lambda function, you navigate to Event sources and choose for the Scheduled Event. After naming your event, you can provide the following schedule expression.

cron(15 17 ? * MON-FRI *)
This expression wil stop the servers every weekday, from monday to friday, at 17:15 PM.
 