# ansible-cloudwatch-logs-agent

An Ansible role to install AWS Cloudwatch Logs agent on CentOS 7 & CentOS 6

## Prerequisites

This role assumes you run an AMI provide by CentOS on AWS.

## Usage

Include the folder in your roles directory. You can add log files to the configuration in, for example, your group_vars, like this:

```
logs:
  - file: /var/log/syslog
    format: "%b %d %H:%M:%S"
    group_name: syslog
```

## Tricks 

Get the latest CentOS AMI by running :

```
aws --region eu-west-1 ec2 describe-images \
    --owners aws-marketplace \
    --filters Name=product-code,Values=aw0evgkw8e5c1q413zgy5pjce \
    --query 'sort_by(Images, &CreationDate)[-1].[ImageId]' \
    --output 'text'
```

## License

MIT
