# Database Migration Project: Traditional DB to AWS RDS

## Project Overview

This project demonstrates the migration of data from a traditional database environment to AWS RDS using an EC2 instance as the migration server.

The migration process ensures secure data transfer, validation, and minimal downtime while moving workloads to the cloud.

---

## Architecture

![alt text](Architecture.png)
```text
Traditional Database → EC2 Migration Server → AWS RDS → Application
```
## Architecture Explanation

This architecture represents the migration of a traditional on-premises database to AWS RDS using an EC2 instance as the migration server.

### 1. Traditional Database (Source)

The migration process starts with the existing traditional database, which may be hosted on-premises or on a local server. This database contains the application data that needs to be moved to the cloud.

* Source database can be **Mariadb**
* Database backup is created using tools like:

  * `mysqldump`
 

This backup ensures data safety before migration.

---

### 2. Amazon EC2 (Migration Server)

An EC2 instance is used as an intermediate migration server.

Its responsibilities include:

* Receiving the exported database backup
* Performing data validation
* Applying transformations if required
* Securely transferring data to AWS RDS

This acts as the bridge between the traditional environment and the cloud.

---

### 3. Amazon RDS (Target Database)

Amazon RDS is the final destination where the database is migrated.

RDS provides:

* Automated backups
* Multi-AZ high availability
* Encryption at rest
* Automatic patching
* Scalability

The backup file from EC2 is imported into the RDS instance.

---

### 4. Application Layer

After successful migration, the application is connected to the new AWS RDS database.

This ensures:

* Better performance
* High availability
* Reduced infrastructure management
* Improved security

---

### 5. Supporting AWS Services

#### Amazon S3

Used as an optional storage layer for:

* Backup staging
* Temporary storage
* Disaster recovery

#### AWS Secrets Manager

Stores database credentials securely and avoids hardcoding passwords.

#### Amazon CloudWatch

Monitors:

* EC2 instance performance
* Database health
* Storage usage
* CPU utilization

#### Security Groups

Control inbound and outbound traffic between EC2 and RDS for secure communication.

---

### Migration Flow

1. Export data from the traditional database.
2. Transfer the backup file to the EC2 migration server.
3. Validate and transform data if required.
4. Import the backup into AWS RDS.
5. Verify data integrity and application connectivity.
6. Switch application traffic to the RDS database.

---

### Benefits of this Architecture

* Smooth migration from legacy systems to cloud
* Secure and reliable data transfer
* Reduced operational overhead
* Improved scalability and performance
* High availability with RDS Multi-AZ
* Better backup and disaster recovery

---

## Tech Stack

- AWS EC2
- AWS RDS
- Mariadb
- Linux
- AWS CLI
- SSH
- Database Dump Tools (`mysqldump`)

---

## Project Workflow

### Step 1: Source Database Preparation
- Identified the traditional database.
- Verified database schema and data integrity.
- Took backup using dump utilities.
![](./Screenshot%20(551).png)
![](./Screenshot%20(552).png)
![](./Screenshot%20(553).png)
![](./Screenshot%20(554).png)
![](./Screenshot%20(555).png)

### Step 2: EC2 Migration Server Setup
- Launched EC2 instance.
- Installed database client tools.
- Configured security groups.

### Step 3: Data Export
Exported database from source:

For Mariadb:
```bash
mysqldump -u root -p source_db > backup.sql
```


```
![](./Screenshot%20(557).png)

---

### Step 4: Transfer Backup to EC2
Transferred backup file securely:

```bash
scp backup.sql ec2-user@<EC2-IP>:/home/ec2-user/
```
![](./Screenshot%20(591).png)

---

### Step 5: Import into AWS RDS

For MySQL:
```bash
mysql -h <RDS-ENDPOINT> -u admin -p target_db < backup.sql
```

For PostgreSQL:
```bash
psql -h <RDS-ENDPOINT> -U postgres -d target_db -f backup.sql
```

---

### Step 6: Validation
- Verified schema consistency.
- Checked record counts.
- Tested application connectivity.

---

## Output :
![](./Screenshot%20(592).png)


## Key Features

- Secure migration process
- Reduced infrastructure management using RDS
- Improved scalability
- Automated backup support
- High availability support
- Performance optimization

---

## Challenges Faced

- Database connectivity issues
- Security group configuration
- Data consistency validation
- Migration downtime planning

---

## Outcome

Successfully migrated the database from a traditional environment to AWS RDS, improving reliability, scalability, and reducing operational overhead.

---

## Future Improvements

- Automate migration using AWS DMS
- Add CloudWatch monitoring
- Implement Multi-AZ deployment
- Enable automated failover

---
## Conclusion

This project demonstrates the successful migration of a traditional database to AWS RDS using Amazon EC2 as a migration server. The migration improves scalability, security, and availability while reducing infrastructure management. It highlights practical experience in database migration, AWS services, and cloud infrastructure management.

## Author

**Sanket Gadade**  
Cloud & DevOps Engineer