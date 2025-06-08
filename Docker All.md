# mgmt API
In Docker container management, instead of manually using terminal commands, we can automate everything using code. Like in AWS ECS, containers are spun up and destroyed automatically as users come and go—this whole orchestration can be replicated manually too. Say we have 3–4 users, we create 3–4 containers on demand, and once a user logs out, the container is killed and user data is wiped, so no storage is done. The idea is simple: for each user, there’s a dedicated Docker container. We use the Docker Engine API to talk to Docker, and to handle this through code, we use Node.js with libraries like Dockerode and Express. We set up routes like GET /containers to list them or POST /containers to spin up new ones (maybe using Alpine), and assign ports using a port mapping logic (like from 8000–9000 range). A backend script handles free port discovery and tracks which port maps to which container to avoid clashes.
So the final setup becomes: user logs in  backend finds a free port  starts a container mapped to that port  user connects through browser at localhost:port (like localhost:8081 or localhost:8082)  when the user logs out, the container gets destroyed. This setup helps make a scalable, isolated, and dynamic container environment, and also sort of achieves a mini load balancer behavior without using heavyweight tools.



# 2nd
solves "It works on my machiner" problem (due to different settings, software, etc.).         
Docker: Makes sure your app runs the exact same way everywhere – on your computer, a 
friend's, or a big server. It's like a consistent "shipping container" for your software.          
Images & Containers:                                                                                                          
Image: A recipe for your software. It contains everything your app needs to run (code, tools, 
settings).                                                                                                                          
Container: The actual running app created from that recipe. It's like a mini-computer running 
just your app, totally separate from other apps on your machine.                                        
Docker CLI: Your command-line tool to talk to Docker. (e.g., typing docker run).            
Docker Daemon: The brain of Docker that does all the work in the background (creating, 
running, managing containers).                                                                                                 
Port Mapping: Your app in a container needs to be seen from your regular computer so we 
need the expose the port. (e.g., a website).                                                                               
…Connects a port on your computer to a port inside the container.Example: docker run -p 
8080:80 my-web-app (Your computer's port 8080 opens to the app's port 80).        
Environment Variables: To give secret settings to your app inside the container (like a 
database password).Example: docker run -e DB_NAME=mydata my-app.         
Dockerfile: A text file with instructions on how to build your Docker Image (recipe).Purpose: 
Automates creating your image, so it's always built the same way.                                      
Example: "Start with Ubuntu," "Install Node.js," "Copy my code." then use docker build to 
turn your Dockerfile into an Image.                                                                                         
Docker Hub:  A cloud library for Docker Images. Example: as YouTube for app recipes. 
Purpose: To share your app's recipe (Image) with others or download ready-made 
ones.Sharing: docker push (upload your Image).Getting: docker pull (download an 
Image).                                                                                                                                 
Docker Compose:                                                                                                              
Problem: Running many interconnected apps (e.g., a website + a database + a chat app).          
A tool that lets you manage multiple containers together using one simple file 
(docker-compose.yml).                                                                                                              
It makes complex app setups easy to start and stop all at once.                                                   
Starting All: docker compose up.Stopping All: docker compose down



# 3rd
A docker hub is a service where we or any user can push the docker image created by them so that the others working in their team or organization can pull and use them, maintaining the same dependency and version levels, solving the problem of it only runs on my machine. So next are the steps to create our own docker hub and host it in AWS. For example, we go to AWS, launch a EC2 instance with Ubuntu, then we use docker, docker-compose, router, nginx, and SSL certificate, AWS EC2 we use t2.large, open the AWS SSH client on our terminal, install the packages, dependencies, and docker, make the docker registry folder, the data folder to store all the images pushed by the public, then we make a YAML file which is a docker-compose file, listening to specific port, wake up the docker-compose file, make some authentications, set up an nginx server which is a HTTPS SSL certified, add the required ports on the EC2, push images to our own docker hub.

# 4th
AWS ECS is a Docker Orchestration System. Basically, it sees how many containers, how many are up and running, how to balance the load in it. And it all happens automatically. We don't interfere much in it. Manually, what we can do is, we can also manually spin up and kill the containers using the command line interface commands. Using the command docker run.it, mention the operating system name and the entry points. So, what we do is, we have a cloud ID, which is a Docker container, which is made up of the fashion is, if we have 3 to 4 users, we have 3 to 4 containers up and running, or maybe spinning, whatever is right. Containers spin on demand and kills after the user is gone. Hence, the user data is not stored. For each user, we have each container. So, what we do is, there is a Docker app. We open terminal on the app, connect the app basically with it. We have the Docker Engine API, which is Docker SoC, entry point for the communication with the Docker app. We implement it in Node.js using the Docker node, which is basically the Docker Engine API library. So, what we do is, we basically write a code in Node.js to create, spin, delete and manage containers based on functions. We do this by creating an express server or maybe just a normal index.js files. Through GET, PUT, POST requests in the express server, routing through the API calls and assigning codes to it, we manage the containers on the Docker app through the code. And hence, we are kind of making a load balancing system in it.