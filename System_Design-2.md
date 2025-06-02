# System Design-2

### Scalability and Cost Optimization

To scale smartly and keep costs in check, we first need to understand the traffic pattern of our service.

---

## Netflix:

- You should have clear policies in place for scaling.
- Be ready for handling traffic spikes.
- Try to predict the number of users beforehand, then pre-scale your servers.
- Warm up extra servers in advance.
- For the first 10-15 to 30 minutes, cache content at the nearest global CDN server to serve users quickly.

---

## YouTube:

- Traffic is mostly unpredictable (a little predictable sometimes during events).
- Still, they manage to handle sudden spikes well.

---

## Hotstar:

- Handles both movies (predictable) and live streaming (can be highly unpredictable).
- They have some idea about max users for live events, so they pre-warm servers accordingly.
- They usually turn off auto-scaling during such events because auto-scaling takes time – new servers need time to boot, install dependencies, and configure everything.

---

## Serverless Computing (AWS Lambda):

SaaS owners often struggle between managing the app and the servers. To solve this, we can use serverless options like **AWS Lambda**.

- Users don’t need to know about or handle the infrastructure.
- Lambda runs code **only when triggered** (like on an API call).
- It scales automatically and is cost-efficient.
- Starts instantly, so no need to keep servers warm or worry about load management.

**But there are some downsides:**

- **Cold start**: If there are no users, the function takes time to start. This hurts the first user’s experience.
- **Duration limits**: You have to respond quickly. Long processing is not ideal.
- **DDOS risk**: Since Lambda scales without limits, a DDOS can lead to a massive bill.
- **Vendor lock-in**: You get tied to a cloud provider (like how Apple locks you in its ecosystem).

---

## More on Auto Horizontal Scaling:

- When we horizontally scale (add more machines), each machine needs to be able to run the same code.
- That code might have dependencies, and every new server must install those.
- So, we need scripts to auto-install dependencies. But even that **takes time** during scaling.

---

## Cross-platform or Version Compatibility Issues:

- Often, the code works on your machine but fails on the cloud (classic “works on my machine” issue).
- To solve this, we use **Virtualization**:
  - Create a VM locally with a specific OS version and install all needed dependencies.
  - Pack that into an image (bootable image), then move it to a cloud server.
- This way, we solve version mismatch and dependency issues, but VMs are **resource heavy**.

---

### Containerization (Lightweight VMs):

- Traditional VM = OS + packages + code → Very heavy.
- With containers, we **remove the OS** from each VM.
- So, containers are much lighter.
- This allows running **many containers on a single machine**.

> **Q: Does 1 VM or container handle 1 user?**  
> **A:** No, one container/VM can handle many users. It depends on the workload. But containers are spun up or killed based on need and usage.

---

### Container Management = Container Orchestration

We need something to manage the containers: creating, destroying, error handling, etc.

- **Google Borg**: Used by Google internally for large-scale container orchestration (not open-source).
- It manages **clusters** (groups of servers) and runs containers on them.

---

### Kubernetes:

- Kubernetes is kind of an **open-source alternative to Google Borg**, made by Google and donated to CNCF.
- It’s now the go-to solution for container orchestration across the industry.

