![Image](https://github.com/user-attachments/assets/e48a7648-f680-4780-9af7-d1703a1cd1bc)

### Routing Policies with Route53

#### Route53 Explanation:
Hosting a website on AWS EC2 instances requires ensuring constant availability for users, even if some instances fail. Route 53 employs health checks to monitor instance health and automatically directs traffic away from unhealthy instances, ensuring seamless user experience.

#### Route53 Routing Policies:
- **Latency:** Route traffic to the AWS region with the lowest latency, enhancing application performance by minimizing response time for users.
- **Weighted:** Ideal for load balancing traffic between different versions of a website, gradually rolling out new features to a percentage of users.
- **Failover:** Automatically redirects traffic to a secondary server if the primary server fails.
- **Geo-Location:** Allows routing traffic based on the geographic location of users, optimizing performance and compliance.

#### Steps:
1. Deploy EC2 instances and create necessary certificates, then create an AMI image.
2. Deploy instances with the AMI in multiple regions.
3. Configure failover records with health checks for each server.
4. Set up primary failover records, directing traffic to the primary instance and failing over to secondary instances if necessary.
5. Verify failover functionality by editing files on instances and observing traffic redirection.
6. Monitor traffic using cloud shell and demonstrate health checks.
7. Test latency by creating records and changing values to observe regional routing.
8. Implement weighted routing by distributing traffic between regions.
9. Showcase Route53 resolver capabilities.

#### Interview Question:
Q: Could you please identify global AWS services?  
A: Route53 and IAM are global services. Although some may consider S3 as global, it operates within specific regions. For instance, when configuring VPC endpoints, specific regions like NV might be requested due to service availability constraints.

