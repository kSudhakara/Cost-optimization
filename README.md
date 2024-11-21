# Cost-optimization
### Why Migrate from On-Premises to the Cloud?

Companies migrate from on-premises infrastructure to the cloud primarily to:

- **Reduce Maintenance**: No need to manage physical servers, updates, and repairs.
- **Lower Costs**: Avoid hefty investments in hardware, power, and cooling.
- **Increase Efficiency**: Easily scale resources up or down based on demand.

However, if after migrating, the company still faces high costs or inefficiencies, it's usually not the cloud provider’s fault. Instead, it’s a **shared responsibility** between the cloud provider and the customer.

### Example Problem: Unused Snapshots

Suppose you create an EC2 instance with an attached EBS volume to store application data. You take snapshots of the EBS volume for backups, which is useful for recovery in case of failures. But once the instance and application are no longer needed, those snapshots become redundant, adding unnecessary costs. 

For a few instances, this might be manageable manually. But at scale, where companies have hundreds of instances across regions, manual management becomes inefficient and error-prone.

Solution: Automate with AWS Lambda

This is where **AWS Lambda** shines. Lambda is a **serverless** service, meaning you don’t have to manage the underlying infrastructure. You simply write the code to handle specific tasks, and Lambda runs it automatically.

In this case, a Lambda function can be triggered when an EC2 instance is deleted. The function will then check for any stale snapshots related to the instance and delete them automatically. This ensures you only pay for the storage you actually need.

Using **Boto3**, the AWS SDK for Python, you can easily automate this task, saving time and reducing unnecessary cloud costs. Automating resource management with Lambda helps ensure your cloud environment remains cost-efficient without manual intervention.
