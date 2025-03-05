# route53-health-checks

# Health-based Detection Configuration for AWS Shield Advanced

## Overview
This CloudFormation template sets up a comprehensive health monitoring system for AWS Shield Advanced using Route 53 health checks and CloudWatch alarms. 
It creates a multi-layered monitoring solution that tracks endpoint health, latency, and error rates.

## Architecture

- Primary Health Check (HTTPS)
- Latency Monitoring
- Error Rate Detection
- Combined Health Status
- CloudWatch Dashboard
- SNS Notifications

## Components

### Health Checks
1. **Primary Health Check**
   - HTTPS endpoint monitoring
   - 30-second intervals
   - 3 failure threshold
   - Multi-region checking (us-east-1, eu-west-1, ap-southeast-1)
   - SNI enabled

2. **Latency Health Check**
   - CloudWatch metric-based
   - Monitors response times
   - Integrates with CloudWatch alarms

3. **Error Rate Health Check**
   - CloudWatch metric-based
   - Tracks failure rates
   - Automatic status updates

4. **Combined Health Check**
   - Aggregates all health checks
   - 2/3 threshold for overall health
   - Provides unified health status

### Monitoring & Alerting
- **CloudWatch Alarms**
  - Latency threshold monitoring
  - Error rate tracking
  - Automatic notification triggers

- **SNS Topic**
  - Email notifications
  - Health check status updates
  - Alarm state changes

- **CloudWatch Dashboard**
  - Health check status visualization
  - Latency metrics
  - Error rate tracking

## Parameters
- `HealthCheckName`: Name for Route 53 health checks (Default: shield-advanced-health-check)
- `EndpointToMonitor`: Target endpoint URL (Default: capp.securitydev.site)
- `NotificationEmail`: Email for alerts (Requires valid email format)

## Outputs
1. Primary Health Check ID
2. Combined Health Check ID
3. SNS Topic ARN

## Usage

### Prerequisites
- AWS Shield Advanced enabled
- Route 53 DNS configuration
- Valid SSL certificate for the endpoint
- IAM permissions for CloudWatch and Route 53

### Deployment
1. Upload template to CloudFormation
2. Provide required parameters
3. Create stack
4. Verify health check creation
5. Confirm SNS subscription

### Monitoring
- View health status in Route 53 console
- Monitor metrics in CloudWatch dashboard
- Check email notifications for alerts

## Security Features
- HTTPS health checks
- SNI enabled
- Email validation
- Multi-region monitoring
- Aggregated health status

## Best Practices
1. Set appropriate thresholds
2. Monitor across multiple regions
3. Configure meaningful alerts
4. Regular testing of notifications
5. Review and adjust parameters as needed

## Maintenance
- Review health check thresholds
- Update endpoint configurations
- Verify notification settings
- Monitor CloudWatch costs
- Adjust parameters based on requirements

## Troubleshooting
1. Check endpoint accessibility
2. Verify SSL certificates
3. Confirm SNS subscriptions
4. Review CloudWatch metrics
5. Check IAM permissions

## Cost Considerations
- Route 53 health check pricing
- CloudWatch metrics and alarms
- SNS notifications
- Multi-region monitoring
