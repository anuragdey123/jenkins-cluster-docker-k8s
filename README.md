9. Provision Multi-Tier Infrastructure using Ansible on Kubernetes (LAMP Stack Example) 
Note: Build base images manually, no pre-built images allowed 
● Use Ansible to provision a complete LAMP stack (Linux, Apache, MySQL, PHP) 
inside a Kubernetes environment with persistent storage and services. 
-----------------------------------------------------------------------------------------------


📌 Project Name:
Provisioning a Multi-Tier LAMP Stack on Kubernetes using Ansible

📌 Objective:
To manually build and deploy a full LAMP (Linux, Apache, MySQL, PHP) stack inside a Kubernetes cluster using:
- Custom Docker images (No prebuilt images)
- Ansible for automated provisioning/configuration
- Kubernetes for orchestration, storage, and service exposure

🧱 Stack Components:

1. **Linux**:
   - Custom base image built using Dockerfile (e.g., Ubuntu)
   - Used in both Apache/PHP and MySQL containers

2. **Apache + PHP**:
   - Dockerfile created to install Apache and PHP
   - A sample `index.php` placed in the image to test PHP functionality
   - Exposed using Kubernetes `NodePort` Service

3. **MySQL**:
   - Custom image built with Dockerfile
   - `init.sql` used to create database and tables
   - Data stored using Kubernetes `PersistentVolume` and `PersistentVolumeClaim`

4. **Ansible**:
   - Installed inside a container running in a pod
   - Inventory file points to Kubernetes service IPs or hostnames
   - Playbook used to configure LAMP stack (e.g., deploy PHP code, check DB)

5. **Kubernetes**:
   - Pods: Apache-PHP, MySQL, Ansible
   - Services: For internal and external communication
   - Volumes: For MySQL persistent storage

🛠️ Key Steps Performed:

- Built all images manually using `docker build`
- Deployed each service using Kubernetes YAMLs (Pods, Services, PVCs)
- Used Ansible inside a pod to automate tasks like copying files, restarting services, checking configs
- Exposed the application using NodePort (e.g., http://<node-ip>:30080)

🗂 Folder Structure:

lamp-k8s-ansible/
├── docker/
│   ├── apache/ → Dockerfile, index.php
│   └── mysql/  → Dockerfile, init.sql
├── k8s/        → YAMLs for pods, services, PVCs
└── ansible/    → playbook.yml, inventory

📊 Output:
- Fully functional LAMP stack running inside Kubernetes
- Accessible web page running PHP
- MySQL database connected with persistent data
- Ansible automating setup inside the cluster

