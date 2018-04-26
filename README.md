# Ansible Role for AWS CloudWatch Logs agent

[![Build Status](https://travis-ci.org/bitintheskud/ansible-role-cloudwatch-logs-agent.svg?branch=master)](https://travis-ci.org/bitintheskud/ansible-role-cloudwatch-logs-agent)

## Introduction

An Ansible role to install AWS Cloudwatch Logs agent on CentOS.

In case you can't afford to run Amazon Linux, this role will install the cloudwatch agent on centos.

Current status :

  -  CentOS 7 --> Tested.
  -  CentOS 6 --> Not tested (Contributor welcome !)

Please see: https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/QuickStartEC2Instance.html

## Prerequisites

This role assumes you run an AMI provide by CentOS on AWS market place (free of charge).

To find the latest AMI from Centos for your AWS region you can run the command below.

```
aws --region eu-west-1 ec2 describe-images \
    --owners aws-marketplace \
    --filters Name=product-code,Values=aw0evgkw8e5c1q413zgy5pjce \
    --query 'sort_by(Images, &CreationDate)[-1].[ImageId]' \
    --output 'text'
```

## Usage

Include the folder in your roles directory. 

If you want to run this playbook locally you can do the following.

Clone the repository

```shell
git clone https://github.com/bitintheskud/ansible-role-cloudwatch-logs-agent.git
```
Create a local ansible playbook with the role included. 

```Shell
cat > playbook.yml
---
- name: Test cloudwatch role
  hosts: 127.0.0.1
  become: yes
  roles:
    - { role: '<YOUR PATH>/ansible-role-cloudwatch-logs-agent' }
```

Run ansible-playbook

```shell
ansible-playbook  -i "localhost," -c local playbook.yml
```

You need to attach a role to your instance to send message to AWS Cloudwatch. 

see: https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/QuickStartEC2Instance.html


## What's next 

- Test redhat 7 distribution with this role. 


## License

MIT
