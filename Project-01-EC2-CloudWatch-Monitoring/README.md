# Project 01 — EC2 CloudWatch Monitoring & CPU Alerting

## Overview

A hands-on AWS monitoring project that demonstrates how to monitor an Amazon EC2 instance using Amazon CloudWatch and configure an automated CPU utilization alarm.

The project also uses `stress-ng` to generate controlled CPU load and validate that the CloudWatch alarm responds to high CPU utilization.

## Architecture

```text
                    AWS Cloud
                       │
                       ▼
                ┌─────────────┐
                │    EC2      │
                │  Amazon     │
                │ Linux 2023  │
                └──────┬──────┘
                       │
                 CPU Metrics
                       │
                       ▼
                ┌─────────────┐
                │ CloudWatch  │
                │   Metrics   │
                └──────┬──────┘
                       │
                CPU threshold
                       │
                       ▼
                ┌─────────────┐
                │ CloudWatch  │
                │    Alarm    │
                └─────────────┘
```

## AWS Services Used

- Amazon EC2
- Amazon CloudWatch
- Amazon Linux 2023
- CloudWatch Alarms

## Tools Used

- Linux / SSH
- `stress-ng`
- AWS Management Console

## Implementation

### 1. EC2 Instance

Created an Amazon EC2 instance using Amazon Linux 2023.

The instance was used as the monitoring target for the project.

### 2. CloudWatch Monitoring

Used Amazon CloudWatch to monitor EC2 CPU utilization.

The CPU utilization metric was used to observe the workload generated on the instance.

### 3. CPU Alarm

Configured a CloudWatch alarm based on EC2 CPU utilization.

The alarm was designed to detect high CPU usage and change state when the configured threshold was exceeded.

### 4. CPU Load Testing

Installed `stress-ng` on the EC2 instance:

```bash
sudo dnf install -y stress-ng
```

Generated CPU load using:

```bash
stress-ng --cpu 2 --timeout 10m
```

This provided a controlled workload for testing the CloudWatch monitoring and alarm configuration.

### 5. Alarm Validation

While the CPU workload was running, CloudWatch monitored the increased CPU utilization.

The alarm state was observed to validate the monitoring configuration.

## Testing

The project was tested by:

1. Launching the EC2 instance.
2. Installing `stress-ng`.
3. Generating controlled CPU utilization.
4. Monitoring CPU metrics through CloudWatch.
5. Verifying the configured CloudWatch alarm response.
6. Cleaning up the AWS resources after testing.

## Key Learnings

- Understanding EC2 monitoring with CloudWatch
- Creating CloudWatch alarms
- Monitoring CPU utilization
- Generating controlled workloads on Linux
- Using `stress-ng` for testing
- Validating monitoring and alerting configurations
- Cleaning up AWS resources after project completion

## Cleanup

After completing the testing, the EC2 instance and associated monitoring resources were removed to avoid unnecessary AWS charges.

## Project Status

**Completed**
