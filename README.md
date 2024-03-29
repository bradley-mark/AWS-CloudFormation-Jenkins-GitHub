# AWS_CloudFormation-Jenkins

![image](https://user-images.githubusercontent.com/91480603/217654398-11eaa7a9-6e6c-4260-9eb0-35629ea698ef.png)

**Configure Jenkins to use GitHub repository**

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

# Create Personal Access Token in GitHub

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

# Configure Jenkins to use GitHub

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

**Example user created**

![image](https://user-images.githubusercontent.com/91480603/217098834-0e18d189-6d05-4ce5-819b-b4377f0e5f50.png)

**Uncheck** 

![image](https://user-images.githubusercontent.com/91480603/217099113-848b3f6e-44e0-46de-ab90-ae00dcd2c75d.png)

4. **Save**
5. **Build Now**

![image](https://user-images.githubusercontent.com/91480603/217099288-420bae4e-7fa3-4066-aa73-2506721bd58d.png)

6. Review **Status**

![image](https://user-images.githubusercontent.com/91480603/217099734-a6961553-ca88-4d97-8f2a-f50b750da66d.png)

7. Review **Console Output**

![image](https://user-images.githubusercontent.com/91480603/217099508-59533aa2-ec1d-4c91-b4dc-e2a57fd6c821.png)

![image](https://user-images.githubusercontent.com/91480603/217099971-46e9882c-e253-4bab-9689-5fc76dcf472d.png)

![image](https://user-images.githubusercontent.com/91480603/217100439-574cdfc8-d226-4e5c-8394-78cf7fe95d37.png)

![image](https://user-images.githubusercontent.com/91480603/217100532-9d2d8525-8a2d-46e0-b5d2-b75290690d22.png)

# Automatic Submit of Jenkins from Git

**Jenkins**

1. Login to **Jenkins**
2. **Job > Configure > Build Triggers**
3. Check **GitHub hook trigger for GITScm polling**

![image](https://user-images.githubusercontent.com/91480603/217271620-0e5cbfc4-65c9-4e6c-b362-44dcb609d621.png)

4. Save

**GitHub**

1. Login to **GitHub**
2. **Repository folder > Settings > Webhooks > Add webhook**
3. **Payload URL** enter Jenkins server dashboard address with **/github-webhook/**
4. **Content type** application/json
5. **Add webhook**

![image](https://user-images.githubusercontent.com/91480603/217273773-70e05f83-56f3-4d09-a4b8-12573bd4926b.png)

Any JSON code change within GitHub will auto trigger a build request in Jenkins
