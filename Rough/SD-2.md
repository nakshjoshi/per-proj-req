client = user to the server
server = machine, capable to run 24/7 with Public IP add, can be anywhere
Virtual Machine
DNS Server = Domain Name System
User Overload = Server Crash, physical resources cant handle load
Fault Tolerant, but kabhi toh limit reach kregi 
Resources should be used efficiently, over optimized nhin krna h otherwise wastage
Vertical Scaling(LB not needed) = Adding more resources like CPU, RAM, GPU etc, but vertical scaling is not possible in running machine , hamien machien restart krni hi padegi to add more CPU and RAM, jb they kerenge toh beech mein ke downtime ayega to restart server with more resources 
Horizonral Scaling = Adding parallel machines to avoid downtime, but jitne bhi parallel machine h sbki IP alag alag hogi, and DNS toh hamein ek hi IP address dega, toh uss case mein user jaye kahan, iske liye ham ek load balancer machine jo as in intermediate use krte hain and DNS takes us to load balancer

load balancing algoes: round robin, 
when detect new user we add horizontally one more server and inform load balancer, when the server boot, LB then checks, is it up and running (healthy) 
Amazon say its Elastic Load Balancing, load balancer has good number of resoures


Microservice Architecture, in this you have different sservices for everything, like auth, api  order, payments, inn saare microservices ke apne apne servers chl rhe hain in different amount
we need to do route routing to those servers, every microservice has its own horizontal scaling and load balcners , this whole microservice architecture routing idea is called API Gateway
API gateway is centralized entry point, attach an auth service with API gateway 
EC-2 elastic compute, VM
amazon -> API gateay -> microservices 

amazon SQS(pull mech) - Batch Processing: to handle multiple requrest which may take time, we make the process async so that on one end we may have a queue to handle further processing the request, but in other end services to receive requests dont stop (this can also be horizntally scaled in creasing parallel tasks )

CSV queue
	
Rate limitting = to precenet ddos attacks, after certain number of requests per seccond or per any time we try blocking that incoming IP request (leaky bucket, token bucket are the rate limiting strategies )

PUB-SUB MODEL (SNS simple notification service): single gateway to notify thorugh many channels. this isevent driven architecture and generally it has no acknolegement generally , so agar koi notifcation channel miss ho jata h due to external servie down, then there is no callback, you either requeue it, or make a separate dead leter quque for it 

Fanout → One message is sent → multiple services act (email, inventory, shipping). Helps services work independently.

what is the difference betwen fanout and sns pub sub 

how to scale up database : make multiple replica(read replica: you always insert into primary node, ) when to use primary node and read replica 
![[Pasted image 20250602140517.png]]
 Caching → Stores frequent data in memory (e.g., Redis). Faster responses and less load on database. Checks cache first → if miss, fetch from DB and store in cache. used for repitive and complex computations 
 CDN → or cloud front , used before load balancer, user request to nearest cloud front it quicklly leads to the load balancer IP, use Anycast → Same IP used by many global servers(CDN or cloud front ). Request is routed to the closest or fastest one.


if i want to query smhing  is it existing in my reguiona clodu front cache then it will happen fat, if not cdn will fetch it from the server/load balancer 