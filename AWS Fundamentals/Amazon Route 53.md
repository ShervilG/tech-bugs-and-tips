## What is S3 ?
DNS service provided by Amazon.
## What is DNS ?
Domain registrar. 
- Domain records can be of types -> A, AAAA, CNAME etc.
- Zone File -> Holds Domain Records
- TLD -> .com .biz etc.
- SLD (second level domain) -> google.com
## What does a record contain ?
Each record contains ->
- Domain/Subdomain Name: example.com, api.example.com
- Record Type: A(Maps hostname to IPv4), AAAA(Maps hostname to IPv6), NS (Named server IPs for hosted zones that can be DNS queried), CNAME(Maps hostname to hostname, only non root domains e.g -> aka.something.mydomain.com)
- Value: 12.12.12.12
- Routing Policy
- TTL (Saved at clients side, so that client don't query dns server again and again)
> `Alias` can map any domain root/non-root to AWS resources
## Routing Policy
Which value is dns query routed to. Records can map same host to different IPs so routing policies handles dns query traffic to route them to appropriate record value. E.g -> abc.diy.com maps to 1.1.1.1 and 2.2.2.2 in 2 records.
Types ->
- Simple
- Weighted
- Latency
## Third Party Domain Registrar and Route53
If We purchase domain name from say Godaddy. All we need to do is ->
- Create a HostedZone in route53,
- Update NS records on 3rd party site to use our route53 name-servers