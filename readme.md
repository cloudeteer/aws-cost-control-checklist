# AWS Cost Controls
We've all been there: that dreaded email notification from AWS with our new cloud bill. We resolve to reduce our costs next month, but another month rolls around and not much has changed.

Here are some of the tools and tricks at your disposal for controlling your AWS cloud spend and reducing your costs. There's an overwhelming number of resources out there to reduce costs. Knowing which ones to prioritize will largely depend on your unique situation and architecture.

# “Free” Money

[ ] AWS Activate Credits, VC backed startups are eligible to receive up to $100,000 in usage credits (one time only)

[ ] Credits for Testing & POC Implementation

# Tricks to Reduce Network Transit Costs

[ ] Move Data Transfer Costs to the Edge (e.g. CDN)
- Use Cloudflare to radically reduce transfer costs (Cloudfront has zero bandwidth fees)
- Use CloudFront

[ ] Configure an S3 Endpoint in your VPC
- Reduces Egress traffic over your NAT gateways (or instances) – one of the biggest costs
- Use VPC Endpoints with AWS Services (E.g. S3) where possible

[ ] Optimize NAT Traffic
- Use NAT instances rather than NAT gateway appliances for dev/test environments

[ ] Use internal private IPs rather than public IPs or Elastic IPs
- Use CNAMEs to AWS hostnames for resources that need to be accessed internally and externally to take advantage of the split-horizon DNS
- Use A records to Private IPs for hostnames that should be accessed strictly internally

[ ] Use a Docker Pull-Thru Registry Cache
- The pull-thru cache will reduce the ingress traffic, but only really effective if hitting one per AZ

[ ] Reduce Availability Zones where suitable to reduce cross-zone traffic
- For dev/test environments, use a single AZ to reduce cross-az transit costs.
- Traffic within an AZ is free.

[ ] Reduce Inter-zone/region traffic

# Shave Compute Costs

[ ] Invest in an AWS Savings Plan

[ ]  Buy (convertible) Reserved EC2 Instances
- Reserved Instances are complicated, but “convertible” RIs are a no-brainer.
- Pro tip: Use spot.io to manage this process for you

[ ] Move to a cheaper AWS region

[ ] Upgrade to newer generations of EC2 instance families

[ ] Use EC2 AMD Instances
- https://cloudonaut.io/6-new-ways-to-reduce-your-AWS-bill-with-little-effort/

[ ] Setup Spot Instances
- Use SpotInstance.com to get almost immediate gratification
- Use spot “fleets”

[ ] Leverage (or Tune) Auto-scaling Capabilities
- Use the SpotInst Ocean controller for Kubernetes to “right-size” your EC2 instances

[ ] Right Size Resources

[ ] Optimize Kubernetes Workloads
- Ensure proper memory & CPU requests and limits are set
- Ensure pods can be rescheduled by setting proper annotations

[ ] Shutdown unused instances
- Don’t just stop instances, but terminate instances to prevent racking up EBS costs
- Reduce Database Costs

[ ] Use Aurora Serverless where appropriate

[ ] Use containerized databases for dev/test environments

[ ] “Right Size” Compute and Storage

# Reduce Storage Costs

[ ] Backup your data in S3 rather than EBS or EFS to save big

[ ] Add Lifecycle Rules for Retention Policies on S3 buckets
- Automatically rotate logs to Glacier or delete after N days

[ ] Use reduced redundancy for less mission-critical artifacts such as logs

[ ] Optimize EBS Volumes
- Reduce oversized volumes

[ ] Optimize EBS Colume Snapshots

# Use the various tools at your disposal

[ ] Komiser (Free/Open Source)

[ ] KubeCost (Free/Open Source) – Tool to gain visibility into operating costs inside of your Kubernetes clusters

[ ] Goldilocks (Free/Open Source) – Tool to help “Right Size” your Kubernetes Pods

[ ] SpotInst.com (SaaS)

[ ] CloudChecker (SaaS)


Source: https://cloudposse.com/checklist/
