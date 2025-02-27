**High Availability and Scaling**

    Vertical Scaling
        -> increase the performance of an instance
        -> cons: cannot be increase forever

    Horizontal Scaling
        -> increase the number of instances
        -> pros: can be increase forever
        -> High Availability

    3Ws
        What do we scale
        Where do we scale
        When do we scale

**Launch Template**

    -> a template specifies all settings needed to build out an EC2 instance
    -> capable to use for all EC2 auto-scaling
    -> support versioning
    -> more granularity
    -> recommended

**Launch Configurations**

    -> only for certain EC2 auto-scaling
    -> immutable
    -> limited options
    -> not recommended

**Auto-Scaling Groups**

    -> only for ec2 instances
    -> collection of ec2 instances
    -> treated as a group for purposes of scaling and management
    -> How:
        -> Define template
        -> specify networking
        -> specify purchasing
        -> ELB configuration
        -> set scaling policies
        -> notification (alert via sns)

**Lifecycle events**

    -> an event where the instance is in pending mode
    -> event where first initial spinning up and before InService
    -> event where instance is terminating and before it actually terminated
Lifecycle Hooks
    -> 

**Auto-Scaling Restrictions**

    -> Minimum
        -> lowest number of EC2 
    -> Maximum 
        -> highest number of EC2
    -> Desired
        -> number of EC2 you want rn

**Auto Scaling Policies**

    -> Step Scaling
        -> Check-in by time interval
        -> Scaling Out Step
        -> Scaling In Step

    -> Simple Scaling
        -> relies on metrics for scaling
        -> ex: add 1 instance if CPU Ultilization metric > 80%
    
    -> Target Tracking
        -> use scaling metric to set a a value for ASG to maintain at all timestamp
        -> ex: Maintain ASGAverageCPUUltilization = 50%

**Instance Warm-up**

    -> issue: instance when just spinning up will fail the HC and get terminate
    -> solution: warm-up to stop instances from being terminated prematurely

**Instance Cooldown**

    -> issue: unusual high demands make Auto-scaling over-do result in high cost = runaway scaling events
    -> solution: pauses Auto Scaling for a set amount of time

**Avoid Thrashing**

    -> create instances quickly
    -> spin down slowly

**Scaling Types (When to scale)**

    -> Reactive
        -> playing catchup
        -> scale when load reach certain threshold

    -> Scheduled
        -> predictive workload
        -> scale at a certain time on schedule events

    -> Predictive
        -> scale with forcast
        -> using machine learning to reevaluated every 24 hours to create a forecast for the next 48 hours

**Scaling Relational Databases**

    4 Types of Scaling
        -> Vertical Scaling
            -> Resizing database to a bigger one
        -> Scaling Storage
            -> Increase storage
            -> Cannot be scale down
        -> Read Replicas
            -> Create read-only copies to increase read performance
            -> Does not improve write performance
        -> Aurora Serverless
            -> AWS managed
            -> Use case: unpredictable workload

    Scaling vs Refactoring
        -> Refactoring is changing a database engine usually from Relation to Dynamo
        -> don't be afraid to change if it solves the issue
        -> not recommended in real world but it a feasible solution
    
**Scaling Non-relational Databases**

    Types
        -> Provisioned
            -> for predictable workload
            -> need to review past usage to set upper/lower scaling bounds
            -> cost effective
        -> On-Demand
            -> sporadic workload
            -> select on-demands
            -> less cost effective
    
    Read Capacity Unit RCU
        -> reads per second for an item up to 4kb
        -> anything larger 4kb requires another RCU
        -> 1 strongly consistent per second per RCU
        -> 2 eventually consistent per second per RCU
    
    Write Capacity Unit WCU
        -> write per seconf for an item up to 1kb

**Disaster Recover**
    
    Recovery Point Objective RPO
        -> How much time are you afford to lose?
        -> The lower the greater the cost

    Recovery Time Object RTO
        -> In the event of failure, how fast do you want to fail over? How much time can the biz afford?
        -> The lower the time, the more expensive the cost

    DR Strategy
        -> Backup and Restore
            -> make a snapshot of production environment, restore in the event of failure
            -> slowest, cheapest

        -> Pilot Light
            -> usecase: make a copy of read-replica of the db to another az, spin up web ec2 in the event of failure + promote RR DB to primary
            -> faster than backup and restore, but still bare some downtime

        -> Warm Standby
            -> usecase: make a RR copy from the DB to another az + 1 web ec2 in another az, in the event of failure, promote to primary, divert traffic over and scale the web instance up to handle traffic
            -> less down time than Pilot Light
            -> slightly more expensive

        Active/Active Failover
            -> make an exact copy of the production environment in another az
            -> no downtime, lowest RTO and RPO
            -> most expensive