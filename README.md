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



