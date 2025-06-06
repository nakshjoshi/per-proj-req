Firecracker is an open source virtualization technology that is purpose-built for creating and managing secure, multi-tenant[ ***(means running workloads from different users (tenants) on the same physical hardware, while keeping them isolated and secure from each other)***]  container and function-based services

## Benfits
- It uses a system (KVM) that keeps apps from different people separate and safe, even if they run on the same computer.
- It starts apps in just 125 milliseconds  & 
It can create up to 150 small virtual machines (microVMs) every second.
- Each Firecracker microVM uses very little memory {***<5 MB***}.
This means you can run lots of them at the same time on one machine. It also manages resources smartly, so everything runs smoothly, even if you're using thousands of microVMs.


## Working of FireCracker VM

1. The Foundation: Bare Metal Server
At the bottom is your actual hardware – the "bare metal server."

It runs Linux and uses a special module called KVM (Kernel-based Virtual Machine) for virtualization.

 2. Firecracker Creates MicroVMs in User Space
Firecracker runs in user space, above the Linux kernel.

It creates and manages thousands of tiny virtual machines, called microVMs.

These microVMs are customizable: you decide how much CPU or memory they use.
3. Each microVM contains:
A Guest OS (just enough to run the app).

The containerized app or function (the workload).

4.  Security Layers
Virtualization barrier (orange outline): Isolates the microVM from the host.

Jailer barrier (gray outline): Adds an extra lock using Linux security features (like namespaces, chroot).

5. - Firecracker exposes a REST API to allow clients (like AWS Lambda) to start/stop/configure VMs.
- I also has control plane and data plane, kinda similar to kubernetes
