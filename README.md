
# AWS assume role script compatible with MFA token

## This script enable you to assume a AWS Role with MFA token authentication enabled

## Instructions:
copy the file aws_role to any bin path (ec. /usr/local/bin)
run command: source aws_role

## Requirements (dependencies):
- aws-cli
- jq
- a AWS credentials profile ($HOME/.aws/credentials)

## HOW it Works

The first time the tool ask for aws account parameters and save it in $HOME/.aws_role/config as a Json File

{"profile": "defalt", "account": "12345678901234", "token": "arn:aws:iam::775678901234:mfa/myuser"}

if you need a custom config file in a local directory, copy this file as ./.aws_role.cfg

the utility sets three environment vars:

- export AWS_ACCESS_KEY_ID
- export AWS_SECRET_ACCESS_KEY
- export AWS_SESSION_TOKEN

## Arguments

you can pass de Role name as argument, if not, 'Developer' is used as default.


## Examples:

aws credentials file:

[default]
aws_access_key_id = AKIAS30000000000001
aws_secret_access_key = u/Ti00000000000000000A+Yszm

[other]
aws_access_key_id = AKIAS30000000000003
aws_secret_access_key = u/Ti9990000000000000A+Yszm

======

run source aws_role

output:

AWS_ROLE (AWS Assume Role utility) v0.1

Lets start setup AWS_ROLE

AWS available profiles:
1 -> default
2 -> other

Select a AWS profile [1-2]: 2

AWS Account: 1234567891234

2FA token ARN: arn:aws:iam::1900000021:mfa/user

parameters saved to: /home/user/.aws_role/config

AWS Assume Role 'Developer' for account 1234567891234
AWS Profile: other
MFA Token ARN: arn:aws:iam::1900000021:mfa/user
MFA Token OTP: {Your OTP}


Next time:
run source aws_role FRODO

AWS_ROLE (AWS Assume Role utility) v0.1

using config file: /home/user/.aws_role/config

AWS Assume Role 'FRODO' for account 1234567891234
AWS Profile: other
MFA Token ARN: arn:aws:iam::1900000021:mfa/user
MFA Token OTP: {Your OTP}

