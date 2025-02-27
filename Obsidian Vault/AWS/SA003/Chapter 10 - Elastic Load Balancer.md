Elastic Load Balancer

    -> automatically distributes incoming application traffic across multiple targets

Types

    -> Application
        -> Layer 7: HTTP and HTTPS traffic
        -> application aware
        -> Intelligent Load Balancer
    -> Network
        -> Layer 4: OSI model
        -> handling million of request per second, ultra-low latencies
        -> Performance Load Balancer
    -> Gateway
        -> Layer 3
        -> use when deploying inline virtual appliances when network traffic is not destined for Gateway LB itself
    -> Classic
        -> Legacy Layer 7
        -> X-Forwarded, sticky sessions
        -> class/test/dev

Health Checks

    -> all AWS LB can be configured with HC
    -> unhealthy instances = OutOfService
    -> LB perform HC on all registered instance (even unhealthy one)
    -> LB stop sending request to unhealthy instance
    -> LB resume sending traffic when instance becomes health

Application Load Balancer

    -> Layer 7
    -> Open Systems Interconnection OSI model

    Load Balancer -> Listener -> Target Group -> Health Check

    -> Listener
        -> checks for connection request from clients, using the protocol and port you configure
        -> HTTPS
        -> must deploy at least one SSL/TLS server certificate on LB
            -> decryption happens at ELB before sending to targets
    
    -> Rules
        -> determine how the load balancer routes requests to its registered targets
        -> each rule consist priority
        -> priority consist one or more actions and one or more conditions
    
    -> Target Group
        -> use to register AWS resource
        -> can be assigned to ELB

    -> Path-Based Routing
        -> 
    
Network Load Balancer

    -> Layer 4
    -> best suited for for load balancing of TCP traffic where extreme performance is required
    -> can decrypt traffic, but requires certificate on the ELB

Classic Load Balancer

    -> Legacy HTTP/HTTPS layer7 x-forwarded-for
    -> 504 error = gateway timed out

Sticky Sesssion

    -> bind a user's session to a specific EC2 instance to ensure all requests from the user during the session are sent to the same instance
    -> disable sticky session when there is timed-out

Deregistration Delay (connection draining)

    -> keep connection open if the EC2 instances are de-registered or being unhealthy



