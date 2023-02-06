# AWS_CloudFormation-Jenkins

This contains CloudFormation template for demo use with Jenkins

simplests3cft.json

```JSON
{
    "AWSTemplateFormatVersion": "2010-09-09",
    "Resources": {
        "S3Bucket": {
            "Type": "AWS::S3::Bucket"
        }
    },
    "Outputs": {
        "BucketName": {
            "Value": {
                "Ref": "S3Bucket"
            },
            "Description": "Name of the sample Amazon S3 bucket."
        }
    }
}
```

JSON creates a bucket and automatically assigns a bucket name and outputs the bucket name

# Create Personal Access Token

**Note** GitHub deprecated password-based authentication August 31st 2021

1. Click **Profile** - **Settings** - **Developer Settings**
2. **Personal Access Tokens** - **Tokens (classic)**
3. **Generate new token**
4. **Note** name token and set **Expiration**

![image](https://user-images.githubusercontent.com/91480603/217093506-b573e8d9-4a3c-44b9-9ec0-9aa801f9f46e.png)

5. **Select Scopes**

![image](https://user-images.githubusercontent.com/91480603/217093812-d9af8580-da38-40cf-8b43-f1ec1837c67b.png)

6. **Create token**

![image](https://user-images.githubusercontent.com/91480603/217094152-c6de5eaf-ffab-490b-b960-8b9d300d1321.png)

# Configure Jenkins to use GitHib

1. Jenkins > Dashboard > Manage Jenkins > Configure System
2. **GitHub** **+Add** *Jenkins* **Kind** is **Secret text** 

**Secret** = token

**ID** = auto created

**Description** = friendly name 

![image](https://user-images.githubusercontent.com/91480603/217095533-49f34318-6053-4d7b-a76f-b5ec34b6656e.png)

# Create a job

![image](https://user-images.githubusercontent.com/91480603/217096661-49b97516-4ece-4ba0-ae38-643b8cb01e1f.png)

1. Enter a item name - Freestyle project

![image](https://user-images.githubusercontent.com/91480603/217096804-c357329e-62de-4d9e-96e6-7fa1a612ec8c.png)

2. Configure **Source Code Management**

![image](https://user-images.githubusercontent.com/91480603/217097167-90aa8284-7d11-4eff-8567-be60433d37c2.png)

For credentials use **Kind** - **Username with password** - password = Personal Access Token

3. Configure **Build Environment**

![image](https://user-images.githubusercontent.com/91480603/217098363-fd0725db-544c-46c3-9ed7-235ff4a378bb.png)

**Note for AWS Access Key and AWS Secret Key use credentials for IAM user with only access to CloudFormation and S3**

![image](https://user-images.githubusercontent.com/91480603/217098496-0973a610-d14f-47b1-be90-3fbdbf7d24bb.png)

![image](https://user-images.githubusercontent.com/91480603/217098834-0e18d189-6d05-4ce5-819b-b4377f0e5f50.png)





