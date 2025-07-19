# Project 6 – Creating an Amazon RDS Database
![Amazon RDS Architecture](https://github.com/fadykaram88/Creating-an-Amazon-RDS-Database/blob/main/rds-guided-lab-arch.png?raw=true)

## Task 1: Launch a MySQL-Compatible Amazon RDS Instance

1. In the AWS Console, search for **RDS** and click **Create database**.
2. Choose **Standard Create**.
3. For **Engine options**, select **MySQL**.
4. **Version**: Choose the latest MySQL version (e.g., 8.0.35).
5. **Templates**: Choose `Free tier`.
6. **DB instance identifier**: `my-rds-database`
7. Set Master username: `admin`
8. Set Master password and confirm it (e.g., `Fady123456`)

---

## Task 2: Configure Connectivity

9. Under **Connectivity**, set the following:
   - **Virtual Private Cloud (VPC)**: Choose the one you created before
   - **Subnet group**: Default (or the one for your VPC)
   - **Public access**: Choose `Yes`
   - **VPC security group**: Choose existing and select one that allows MySQL/Aurora (port 3306)

10. Click **Create database**

---

## Task 3: Launch EC2 Instance to Access the RDS

11. In the AWS Console, search **EC2** > click **Launch Instance**:
   - **Name**: `RDS Client`
   - **OS Image**: Amazon Linux 2023
   - **Instance type**: `t2.micro` (Free tier)
   - **Key Pair**: Choose existing (`Vockey`)
   - **VPC**: Same as RDS
   - **Subnet**: Public subnet
   - **Auto-assign Public IP**: Enabled
   - **Security Group**: Choose one that allows port 3306 (MySQL)

12. Launch the instance.

---

## Task 4: Connect to the EC2 Instance and Install MySQL Client

13. Use **Session Manager** or SSH to connect to the EC2 instance.

14. In the terminal, run:

```bash
sudo su - ec2-user
sudo yum install mysql -y
```

---

## Task 5: Connect to the RDS Database

15. Go to **RDS** > **Databases** > Select your DB > copy **Endpoint**

16. In the EC2 terminal, run:

```bash
mysql -h <your-endpoint> -u admin -p
```

17. Enter your password when prompted.

18. You are now connected to the RDS database!

---

## ✅ Project Summary:

- RDS (MySQL) instance launched and publicly accessible
- EC2 instance created and connected to same VPC
- MySQL client installed on EC2 and connected to RDS

---

## 👋 See you in the next project!
