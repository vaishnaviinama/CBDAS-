# CBDAS-
Create a vitual LAN with two subnets ( Public and Private ) 



# Steps Performed

### 1. Create VPC
- Log in to AWS Management Console  
- Open VPC service  
- Click **Create VPC**  
- Enter details:
  - Name: vpc
  - IPv4 CIDR block: 10.0.0.0/16
- Click **Create VPC**

---

### 2. Create Public Subnet
- Go to **Subnets → Create Subnet**
- Select vpc
- Enter details:
  - Subnet name: Public-Subnet
  - CIDR block: 10.0.1.0/24

### 3. Create Private Subnet
- Create another subnet in the same VPC
- Enter details:
  - Subnet name: `Private-Subnet`
  - CIDR block: `10.0.2.0/24`
- Disable Auto-assign Public IP

### 4. Create Internet Gateway
- Go to **Internet Gateways**
- Click **Create Internet Gateway**
- Attach it to vpc

### 5. Create Route Table for Public Subnet
- Go to **Route Tables**
- Create a new route table: Public-RT
- Add route:
  - Destination: 0.0.0.0/0
  - Target: Internet Gateway
- Associate with Public-Subnet

### 6. Configure Private Subnet Route Table
- Create another route table: Private-RT
- Associate it with Private-Subnet
- (Optional) Add NAT Gateway for outbound internet access

### 7. Launch EC2 Instances (Optional)
- Launch EC2 instance in 
- Enable SSH access using public IP
- Launch EC2 instance in 
- Access private instance via public instance (Bastion Host)

### 8. Security Configuration
- Configure Security Groups:
  - Public instance:
    - Allow SSH (Port 22) from your IP
  - Private instance:
    - Allow SSH only from Public instance

### 9. Testing Connectivity
- Connect to Public EC2 instance
- From Public instance, SSH into Private instance using private IP
- Verify connectivity

Successfully created a VPC with Public and Private subnets.  
- Public subnet allows internet access  
- Private subnet remains secure and isolated  

 Youtube video link --https://youtu.be/yxt9kGjYJWY?si=KYZLHQmEE-m3blhB
- Use NAT Gateway if private subnet needs internet access  
- Always follow least privilege principle in IAM  
