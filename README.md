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

#### Multi-level attack volume thresholds - change the threshold to suit your environment

1. Warning (1GB/5min)

2. Critical (5GB/5min)

3. Emergency (10GB/5min)

#### DDoS event detection alerts

#### Visualization & Alerting

1. CloudWatch dashboard

2. Email notifications via SNS

#### Metric monitoring for:

1. Active connections

2. Health status

3. Attack volume

4. DDoS events

## Prerequisites
1. AWS Shield Advanced subscription

2. Network Load Balancer with two Elastic IP addresses

3. AWS CloudFormation access

4. Valid email address for notifications


## Parameter	                   ##  Description	                       ## Default
NLBName	                           Name of the Network Load Balancer	   nlb-ext-shield
EmailAddress	                   Email for alarm notifications	       
EIP1AllocationId	               First EIP Allocation ID	
EIP2AllocationId	               Second EIP Allocation ID	
HealthyHostThreshold	           Minimum healthy hosts	               1
ConnectionThreshold	               Max concurrent connections	           10000
AttackVolumeWarningThreshold	   Warning level (bytes)	               1000000000
AttackVolumeCriticalThreshold	   Critical level (bytes)	               5000000000
AttackVolumeEmergencyThreshold	   Emergency level (bytes)	               10000000000



