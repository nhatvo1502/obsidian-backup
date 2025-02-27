**CloundWatch**

    -> monitor system allow us to look into aws's resources

**System Metrics **

    -> metrics out of the box

**Application Metrics**

	-> agent installed on EC2 instance to collect info

Alarms

    -> alert when metric reach a certains threshold

**AWS CloudWatch Logs**

    -> to monitor, store, and access log files
    -> Amazon CloudWatch Agent for custom logs

    -> Log Event:
        -> record with timestamp and data
    -> Log Stream
        -> collection of log events
        -> continuously
    -> Log Group
        -> collection of log streams
        -> for easy manage
    
    -> Features:
        -> Filter Patterns
        -> Insights
            -> allow to query logs using SQL-like interactive solutio
        -> Alarms
    
**Amazon Managed Grafana**

    -> Fully managed AWS service 
    -> secure data visualizations for query, correlating and visualizing metrics, logs, and traces from differece sources
    -> Usecases
        -> Container Metric Visualizations = Prometheus for EKS, ECS or Kubernetes cluster metrics
        -> IoT and edge device data
        -> Troubleshooting

Amazon Managed Service for Prometheus

    -> serverless AWS-managed open-source Prometheus
    -> auto scalling and HA
    -> work with Amazon EKS or self-managed Kubernetes clusters
    -> PromQL = query language
    -> Data retention 150 days