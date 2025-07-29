# Run Ansible Inside Kubernetes Pod and Automate Ping Test

In this project, I created a setup to run Ansible inside a Kubernetes pod to perform automation tasks like running a simple ping test on a remote target. This setup simulates a real-world DevOps environment where Ansible automation tasks are containerized and deployed inside Kubernetes clusters.

---

## What Was Done

- Created a custom Ansible Pod YAML definition.
- Installed and configured Ansible inside the Kubernetes pod.
- Created and mounted an inventory file (`hosts`) for Ansible target definitions.
- Added SSH keys and set up passwordless SSH between Ansible Pod and remote Ubuntu container.
- Verified the Ansible setup by executing:
  - `ansible all -m ping` for local connection
  - `ansible all -m ping -i hosts` for remote target over SSH

---

##  Project Structure

- ansible-inside-k8s-pod/
  - ansible-pod.yaml
  - ansible-pod/
  - hosts
  - ubuntu-target.yaml
  - roles/
  - screenshots/
   
---

##  How It Works

1. **Create the Kubernetes Pod** using `ansible-pod.yaml`:
   ```
   kubectl apply -f ansible-pod.yaml
   Exec into the Pod:
   kubectl exec -it ansible-pod -- bash

Install Ansible and create SSH keys:
apt update && apt install ansible -y
ssh-keygen -t rsa
ssh-copy-id user@remote

Run the ping module to test connectivity:
For local:
ansible all -m ping -c local
For remote:
ansible all -m ping -i hosts

- Screenshots

 ###  Ansible Pod Created Successfully  
> This screenshot shows the successful creation of the Ansible Pod inside the Kubernetes cluster using `kubectl apply -f`.

![Ansible Pod Created](https://github.com/shreya-singh27/ansible-inside-k8s-pod/assets/XXXXXX/ansible-pod-created.png)

---

###  Local Ping Test (Inside Pod)  
> This confirms that Ansible can successfully ping the localhost using `ansible all -m ping -c local`.

![Local Ping Test](https://github.com/shreya-singh27/ansible-inside-k8s-pod/assets/XXXXXX/ansible-local-ping-success.png)

---

###  Remote Ping Test (Target Container)  
> This screenshot shows Ansible pinging a remote container target defined in the `hosts` file using SSH.

![Remote Ping Test](https://github.com/shreya-singh27/ansible-inside-k8s-pod/assets/XXXXXX/ansible-remote-ping-success.png)


- Conclusion
 This setup helps demonstrate how infrastructure automation can be deployed as code inside Kubernetes environments using Ansible. It's a great example of integrating configuration management tools inside containerized clusters for real-world DevOps practices.

- Learnings
 Running Ansible in a containerized environment

 SSH and inventory setup for automation

 Basics of Kubernetes pod creation and communication

