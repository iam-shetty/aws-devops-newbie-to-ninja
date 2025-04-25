![Security VS NACL](https://github.com/saikiranpi/mastering-aws/assets/109568252/2fe56c98-cc17-4589-821d-9b54e16ac47c)


# Security Groups vs Network Access Control Lists (NACLs)

Let's delve into the differences between security groups (SG) and network access control lists (NACLs) in AWS, using the analogy of firewalls and practical examples to illustrate their functionalities.

## Security Groups

Security groups act as stateful firewalls, controlling traffic at the instance level based on rules. They regulate inbound and outbound traffic and are associated with individual instances.

Security Groups act as virtual firewalls for Amazon EC2 instances (virtual servers) at the instance level. They control inbound and outbound traffic by allowing or denying specific protocols, ports, and IP addresses.
Each EC2 instance can be associated with one or more security groups, and each security group consists of inbound and outbound rules.
Inbound rules determine the traffic that is allowed to reach the EC2 instance, whereas outbound rules control the traffic leaving the instance.
Security Groups can be configured using IP addresses, CIDR blocks, security group IDs, or DNS names to specify the source or destination of the traffic.
They operate at the instance level and evaluate the rules before allowing traffic to reach the instance.
Security Groups are stateful, meaning that if an inbound rule allows traffic, the corresponding outbound traffic is automatically allowed, and vice versa.
Changes made to security group rules take effect immediately

### Practical Example

Suppose you have an instance with default security group settings:
- All inbound traffic is denied by default.
- Outbound traffic is allowed by default.

1. **Allow All Inbound Traffic:** Delete the outbound rules and test internet connectivity. You'll notice that the instance can connect to the internet.
2. **Restrict Outbound Access to Websites:** Add outbound rules for HTTP and HTTPS. Test again to ensure only website access is permitted.
3. **Allow ICMP Protocol for Ping:** As ping uses ICMP protocol, add an outbound rule to allow ICMP traffic for ping to work.

Remember, security groups start with a default deny stance and require explicit rules to allow traffic..

## Network Access Control Lists (NACLs)

NACLs, on the other hand, function as stateless firewalls, controlling traffic at the subnet level based on rules. They evaluate inbound and outbound traffic separately and are associated with subnets

NACLs are an additional layer of security that operates at the subnet level. They act as stateless traffic filters for inbound and outbound traffic at the subnet boundary.
Unlike Security Groups, NACLs are associated with subnets, and each subnet can have only one NACL. However, multiple subnets can share the same NACL.
NACLs consist of a numbered list of rules (numbered in ascending order) that are evaluated in order from lowest to highest.
Each rule in the NACL includes a rule number, protocol, rule action (allow or deny), source or destination IP address range, port range, and ICMP (Internet Control Message Protocol) type.
NACL rules can be configured to allow or deny specific types of traffic based on the defined criteria.
They are stateless, which means that if an inbound rule allows traffic, the corresponding outbound traffic must be explicitly allowed using a separate outbound rule.
Changes made to NACL rules may take some time to propagate to all the resources using the associated subnet.

### Real-Time Scenario

Let's consider a scenario where you have a web server that needs to be accessible from the internet. Here's the setup:
- Outbound Rules: Allow all traffic.
- Inbound Rules: Allow TCP port 80 from 0.0.0.0/0 (anywhere) for web traffic and TCP port 22 from your IP address for SSH access.

By configuring NACLs in this manner, you ensure that web traffic (HTTP) is allowed from anywhere while SSH access is restricted to your IP address only.

## Comparison: SG vs NACL

- **Security Groups:** Work at the instance level. They are stateful and require explicit rules for inbound and outbound traffic.
- **NACLs:** Operate at the subnet level. They are stateless and evaluate inbound and outbound traffic separately, with the option to allow or deny traffic based on defined rules.

Remember, in an interview scenario, you may be asked to differentiate between security groups and NACLs. Security groups regulate traffic at the instance level, while NACLs control traffic at the subnet level, offering both allow and deny options based on defined rules.

![SG vs NACL](sg_vs_nacl.png)

This diagram visually represents the differences between security groups and NACLs in AWS, highlighting their respective scopes and functionalities.


![Sg vs NACL](https://github.com/saikiranpi/mastering-aws/assets/109568252/8a623a87-f5f0-4d5d-a84c-268f28bd690a)

![Screenshot 2023-06-29 at 12 14 32 AM](https://github.com/iam-veeramalla/aws-devops-zero-to-hero/assets/43399466/30bbc9e8-6502-438b-8adf-ece8b81edce9)
![Image](https://github.com/user-attachments/assets/fbda947e-ddd6-45b7-b6a4-920be140bcaf)

![Image](https://github.com/user-attachments/assets/4510b0d2-7dc9-4e39-b487-88bcff63679d)

![Image](https://github.com/user-attachments/assets/35cf4e07-d35c-4823-8a18-2c90017c0753)
.
