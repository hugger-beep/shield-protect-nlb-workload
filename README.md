# shield-protect-nlb-workload


# AWS Shield Advanced Protection for Network Load Balancer

This repository contains CloudFormation templates for implementing AWS Shield Advanced protection with comprehensive monitoring for Network Load Balancers (NLB) using Elastic IP addresses.

## Architecture

    Internet((Internet)) --> EIP1[EIP 1]
    EIP1 --> NLB[Network Load Balancer]
    NLB --> EC2[EC2 Instance]
    CW --> SNS
    CW --> Dashboard
    
    ShieldAdv[Shield Advanced] --> |Protects| EIP1
    ShieldAdv --> |Protects| EIP2 [[1]](https://repost.aws/questions/QUiUAkXLlrTh2nnWAI9ZKCrA/shield-advanced-l3-4-only-for-external-nlb)
    
## Monitoring
    [Zonal Health Check]
    [Connection Health Check]
    [Target Health Check]
    [Composite Health Check]
    CW[CloudWatch Alarms]
    SNS[SNS Topic]
    Dashboard[CloudWatch Dashboard]


## Features
### Shield Advanced Protection

1. Layer 3/4 DDoS protection for EIPs

2. Health check-based detection

3. Protection group with SUM aggregation for scaling instances

### Health Monitoring

#### Composite health check combining:

1. NLB zonal health

2. Connection count monitoring

3. Target group health

### DDoS Attack Detection

#### Multi-level attack volume thresholds

1. Warning (1GB/5min)

2. Critical (5GB/5min)

3. Emergency (10GB/5min)

#### DDoS event detection alerts

