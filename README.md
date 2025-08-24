 **Install AWS CLI** (you already have it since you ran commands).
**Configure AWS CLI** with your credentials and region:

   ```powershell
   aws configure
   ```

   * Enter your **Access Key ID**, **Secret Key**, **Default Region** (e.g., `ap-south-1`), and preferred output format (`json`).

--

### 1. Choose an AMI (Amazon Machine Image)

aws ec2 describe-images --owners amazon --filters "Name=name,Values=amzn2-ami-hvm-*-x86_64-gp2" --region ap-south-1


### 2. Choose an Instance Type

t3.micro   # Free-tier eligible

### 3. Create a Key Pair (for SSH/RDP login)

aws ec2 create-key-pair --key-name MyKeyPair --query "KeyMaterial" --output text > MyKeyPair.pem

### 4. Create a Security Group

aws ec2 create-security-group --group-name MySecurityGroup --description "My security group"

### 5. Launch the Instance
C:\Program Files\Amazon\AWSCLIV2\awscli>aws ec2 run-instances --image-id=ami-0a716d3f3b16d290c --instance-type=t3.micro --region=eu-north-1

## Get the instances using filters
C:\Program Files\Amazon\AWSCLIV2\awscli>aws ec2 describe-instances --filters "Name=instance-type,Values=t3.micro" --query "Reservations[].Instances[].InstanceId"

## Get instance ids of all instances
C:\Program Files\Amazon\AWSCLIV2\awscli>aws ec2 describe-instances --filters "Name=instance-type,Values=t3.micro" --query "Reservations[].Instances[].InstanceId"
## Terminate an instance uisng instance id

C:\Program Files\Amazon\AWSCLIV2\awscli>aws ec2 terminate-instances --instance-ids i-09****8*abab58b5



