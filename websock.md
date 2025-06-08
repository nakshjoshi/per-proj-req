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


