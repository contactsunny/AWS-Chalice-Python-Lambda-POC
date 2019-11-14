# AWS Lambda with Chalice and Python
A simple POC to demonstrate how to write, test locally, and deploy Python Lambda functions to AWS using Chalice.

# Installing Chalice
Make sure you are using Python 2.7, Python 3.6, or Python 3.7 on your local machine. Also, make sure you have ```pip``` installed. With that, use one of the following commands (depending on the version of Python installed) to install Chalice on your local machine:

```shell
pip install chalice
```
or 
```shell
pip3 install chalice
```

# How to run locally
```cd``` into the project directory and run the following command to start the local server for your Lambda function:

```shell
chalice local
```

If that command doesn't work or if Chalice fails to resolve localhost, try the following command:

```shell
chalice local --host 0.0.0.0
```
This command should work.

# Configuring AWS Credentials on your local machine
You need create a ```.aws``` folder in your home directory and save your credentials in a file named ```config``` inside this directory. You use the following commands to do that:

```shell
mkdir ~/.aws
cd ~/.aws && vim config
```
Add the following content to the file, replace the placeholders with  your actual credentials, and save the file:

```shell
[default]
aws_access_key_id=<your_access_key_here>
aws_secret_access_key=<your_secret_key_here>
region=<your_region_here>
```

# Deploying the Lambda function to AWS
Once you have developed and written the function, make sure you have the following configuration in the ```.chalice/config.json``` file:

```json
{
	"version": "2.0",
	"app_name": "chalice-poc",
	"stages": {
		"dev": {
			"api_gateway_stage": "api",
			"manage_iam_role":false,
			"iam_role_arn":"arn:aws:iam::xxxyyyzzz:role/abc",
			"environment_variables": {
				
			}
		}
	},
	"app_name": "chalice-poc-dev"
}
```
Replace the placeholders with your actual values, of course. Once this is done, run the following command from the project root directory to deploy the Lambda function to AWS:

```shell
chalice deploy
```

# Detailed instructions
For more information about how to work with Chalice, refer to the [blog post here](https://blog.contactsunny.com/tech/getting-started-with-chalice-to-create-aws-lambdas-in-python-step-by-step-tutorial).