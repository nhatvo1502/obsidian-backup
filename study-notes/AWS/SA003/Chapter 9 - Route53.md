**Route 53 Overview**

	-> Amazon DNS service

    -> Top-Level Domain
        -> .gov, .gov.uk
        -> controllled by Internet Assigned Numbers Authority (IANA)
    
    -> Domain Registrars
        -> site that sells domain name

    -> Command DNS Records
        -> SOA
            -> name of the server that supplies the data for the Zone
            -> administrator of the Zone
            -> current version of the data file
            -> default number of seconds for the TTL file on resource records
            
        -> NS Records - name server
            -> used by TLD servers to direct traffic to the content DNS server that contains the authoritative DNS records
            
        -> A Record - address
            -> computer translate domain name to IP address
        -> CNAME - canonical name
            -> resolve one domain name to another
        -> Alias Records
            -> map resource record to ELB, CloudFront distributions or S3 bucket (static website)
            -> only from AWS

**Routing Policies**
    -> Simple Routing
        -> route traffic to 1 primary resource

    -> Weighted Routing
        -> route traffic based on their weight value

    -> Latency-Based Routing
        -> route traffic based on user's performant

    -> Failover Routing
        -> when active is unresponsive, failover to passive

    -> Geolocation Routing
        -> route traffic based on user's location

    -> Geoproximity Routing
        -> similar to geolocation

    -> Multivalue Answer Routing
        -> return multiple value based on health check
            