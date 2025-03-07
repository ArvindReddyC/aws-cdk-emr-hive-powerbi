
#How to run this Project

To manually create a virtualenv on MacOS and Linux:

```
$ python3 -m venv .venv
```

After the init process completes and the virtualenv is created, you can use the following
step to activate your virtualenv.

```
$ source .venv/bin/activate
```

If you are a Windows platform, you would activate the virtualenv like this:

```
% .venv\Scripts\activate.bat
```

Once the virtualenv is activated, you can install the required dependencies.

```
$ pip install -r requirements.txt
```

At this point you can now synthesize the CloudFormation template for this code.

```
$ cdk synth
```

# EMR Pipeline & Data Visualization with PowerBI Overview

## Tools and Technologies

### AWS
- Cloud Development Kit (CDK)
- Virtual Private Cloud (VPC)
- Simple Storage Service (S3)
- Elastic MapReduce (EMR)
- Apache Hive

### Azure
- Virtual Machine
- Microsoft PowerBI (requires Windows to run)

## AWS Cloud Development Kit (CDK)
- Open-source framework from AWS that allows developers to define cloud infrastructure as code using TypeScript, JavaScript, Python, C#, and Java.
- Infrastructure is defined as reusable components called constructs, which generate AWS CloudFormation templates.
- Provides higher-level abstraction while still allowing flexibility and control.


## Create Bucket Deployment Stack
1. Get sales data and place it in the data directory
2. Create a new folder for the stack
3. Create a new Python file for the stack
4. Inside the new file:
   - Create a `BucketDeploymentStack` class
   - Create primary bucket
   - Create log bucket
   - Create data deployment stack

## Create Security Stack
1. Create a new folder for the security stack
2. Create a new Python file for the security stack
3. Create a security stack class
4. Create a VPC within the class

## Data Overview

### AWS Elastic MapReduce (EMR)
- Managed big data platform on AWS
- Allows users to process and analyze vast amounts of data using Apache Hadoop, Spark, and Hive.
- Supports data ingestion, processing, transformation, and analysis, including machine learning and Spark streaming.
- Highly scalable (easily add or remove nodes from the cluster)
- Offers security features such as encryption for data in transit and at rest, and fine-grained access control
- Integrates with AWS services like Amazon Redshift and Amazon Athena
- Provides monitoring tools such as Amazon CloudWatch, AWS CloudTrail, and AWS Management Console

## Hive vs Spark

### Hive
- Data warehousing system for querying and analyzing large datasets stored in Hadoop Distributed File System (HDFS)
- Designed for batch processing, optimized for long-running queries
- Very stable
- Easier to learn (Hive Query Language, HQL, is similar to SQL)

### Spark
- Fast and flexible big data processing engine
- Supports batch and real-time processing workloads
- Steeper learning curve, especially for SQL users
- Supports multiple languages, including Python, Scala, and Java

## Create Hive Scripts
1. **Create tables script**
   - Create an external table for raw data
   - Create an external table for transformed data
2. **Create a transformation script**
   - ETL script fixes dates in the sales data
   - Inserts transformed data into the new table

## Create EMR Cluster Stack
1. Create a new folder
2. Create a new Python file
3. Create an EMR cluster stack class
4. Inside the class:
   - Create a new policy to read from the scripts directory
   - Create EMR Cluster
   - Retrieve correct subnet ID from AWS Console (under EC2-VPC)
   - Create Hive step for creating tables
   - Create Hive step for transforming data

## Deploying the Stacks
1. Deploy stacks individually
2. First, run:
   ```sh
   cdk synth [stack id]
   ```
3. Then deploy with:
   ```sh
   cdk deploy [stack id]
   ```
4. Deploy Data Deployment Stack
5. Deploy Security Stack
6. Deploy EMR Cluster Stack

