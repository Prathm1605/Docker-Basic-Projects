Project 1: Setting up SSH connection between two Ubuntu containers in Docker

This project involves setting up and establishing a secure shell (SSH) connection between two Ubuntu containers in Docker. The steps are:

Run Container 1: Start an Ubuntu container from Docker Hub.
SSH Configuration (Container 1): Install the open-ssh-server package to allow it to act as an SSH server.

Run Container 2: Start a second Ubuntu container.

SSH Configuration (Container 2): Install the ssh-client package to allow it to act as an SSH client.

Set Root Password (Container 1): Set a new password for the root user inside Container 1.

Connect: Establish an SSH connection from Container 2 to Container 1.

This project provides valuable insights into:

Improved Security: Establishes a secure and encrypted connection, protecting data confidentiality, integrity, and authenticity.

Ease of Management: Docker simplifies managing and deploying containers, reducing infrastructure complexity.

Better Collaboration: Enables multiple team members to work simultaneously with isolated, communicating containers.

Scalability: Containers are lightweight and can be easily scaled up or down to meet changing application demands.

Portability: Docker containers are highly portable, allowing easy migration between environments and cloud providers.

How to Run 

Pull Ubuntu Image: docker pull ubuntu

Create Project Directory: mkdir project1 && cd project1

Create Container 1: docker run -it --name container1 ubuntu

Install OpenSSH Server in Container 1:

apt-get update 
apt-get install openssh-server 

Configure SSH in Container 1:
Install Nano: apt-get install nano 

Edit sshd_config: nano /etc/ssh/sshd_config 

Uncomment PermitRootLogin and set it to yes. 

Save and exit (Ctrl+S, Ctrl+X).
Start SSH Service in Container 1:
service ssh start 

Exit Container 1: exit 

Create Container 2: docker run -it --name container2 ubuntu 

Install OpenSSH Client in Container 2:
apt-get update 
apt-get install openssh-client 

Exit Container 2: exit 

Set Root Password in Container 1:

Start Container 1: docker start container1 

Access Container 1: docker exec -it container1 bash 

Set password: passwd root  (Enter "123" as password for demonstration)

Get IP Address of Container 1:
Exit Container 1: exit 

Get IP: docker inspect container1 | grep "IPAddress" 

Connect from Container 2 to Container 1 via SSH:

Start Container 2: docker start container2 

Access Container 2: docker exec -it container2 bash 

Connect via SSH: ssh root@ (Use the IP address obtained in the previous step, e.g., 172.17.0.2)

Accept connection and enter password ("123").


