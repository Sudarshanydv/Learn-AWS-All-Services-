# 1. Q: What is computer networking?
A: Networking means connecting two or more computers to share data, files, or resources.

# 2. Q: What are the types of networks?
A: LAN (Local Area Network), MAN (Metropolitan Area Network), and WAN (Wide Area Network).


# 2. Why would you use the AWS CLI?
The AWS CLI provides a convenient way to automate tasks, manage AWS resources, and interact with services directly from the command line, making it useful for scripting and administration.

3. How do you install the AWS CLI?
You can install the AWS CLI on various operating systems using package managers or by downloading the installer from the AWS website.

4. What is the purpose of AWS CLI profiles?
AWS CLI profiles allow you to manage multiple sets of AWS security credentials, making it easier to switch between different accounts and roles.

5. How can you configure the AWS CLI with your credentials?
You can configure the AWS CLI by running the aws configure command, where you provide your access key, secret key, default region, and output format.

6. What is the difference between IAM user-based credentials and IAM role-based credentials in the AWS CLI?
IAM user-based credentials are long-term access keys associated with an IAM user, while IAM role-based credentials are temporary credentials obtained by assuming a role using the sts assume-role command.

7. How can you interact with AWS services using the AWS CLI?
You can interact with AWS services by using AWS CLI commands specific to each service. For example, you can use aws ec2 describe-instances to list EC2 instances.

8. What is the syntax for AWS CLI commands?
The basic syntax for AWS CLI commands is aws <service-name> <operation> [options], where you replace <service-name> with the service you want to interact with and <operation> with the desired action.

9. How can you list available AWS CLI services and commands?
You can run aws help to see a list of AWS services and the corresponding commands available in the AWS CLI.

10. What is the purpose of output formatting options in AWS CLI commands?
Output formatting options allow you to specify how the results of AWS CLI commands are presented. Common options include JSON, text, table, and YAML formats.

11. How can you filter and format AWS CLI command output?
You can use filters like --query to extract specific data from AWS CLI command output, and you can use --output to choose the format of the output.

12. How can you create and manage AWS resources using the AWS CLI?
You can create and manage AWS resources using commands such as aws ec2 create-instance for EC2 instances or aws s3 cp to copy files to Amazon S3 buckets.

13. How does AWS CLI handle pagination of results?
Some AWS CLI commands return paginated results. You can use the --max-items and --page-size options to control the number of items displayed per page.
