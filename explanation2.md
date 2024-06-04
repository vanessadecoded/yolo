You are required to have installed vagrant, ansible, virtual box and docker if not already installed.
 

After installation in the root of the project create a vagrantfile which will afterwards be configured;

This Vagrantfile sets up a virtual machine using the Ubuntu 20.04 box provided by "geerlingguy." It forwards two ports from the guest machine to the host machine: port 3000 on the guest to port 4000 on the host, and port 5000 on the guest to port 6000 on the host.

It provisions the VM using Ansible, a configuration management tool. It specifies a playbook named "yolo_playbook.yaml" to run during provisioning, which contains tasks to set up and configure software on the VM. 

 I configured the ansible playbook as follows:
  This Ansible playbook is designed to automate the setup of a development environment for a project called "yolo." It performs various tasks sequentially on the local machine (specified by connection: local) as the user "tracy" with sudo privileges (become: true).

Here's a breakdown of what each part does:

hosts: all: Specifies that these tasks should be applied to all hosts defined in the inventory file (though in this case, it's just the local machine).
gather_facts: false: Disables gathering of facts about the target system (not necessary for local setup).
connection: local: Specifies that tasks should be executed on the local machine.
become: true: Allows the tasks to run with escalated privileges.
become_method: sudo: Specifies that the sudo command should be used for privilege escalation.
become_user: tracy: Specifies the user to become when executing privileged tasks.
become_flags: '-H -S': Flags passed to sudo when escalating privileges (sets environment variables and prompts for password if required).
roles: This section defines the roles to be applied to set up the development environment. Each role represents a set of tasks grouped together for a specific purpose. Here are the roles and what they likely do:
clone-repo: Clones the project repository.
check-docker-installation: Checks if Docker is installed on the system.
docker-install: Installs Docker if it's not already installed.
directory-destination: Sets up directory destinations for the project.
copy-files: Copies necessary files to the project directory.
ownership-permission: Sets ownership and permissions for project files.
docker-compose-up: Starts the Docker containers using docker-compose.
The commented-out sections below the roles (# denotes a comment) indicate additional tasks that can be performed, such as starting Docker services, building Docker images, and running Docker containers. These tasks are not included in the playbook but can be uncommented and added if needed. They would typically be part of the respective roles (docker-install, docker-compose-up, etc.) or placed in separate roles for better organization and reusability.

The uncommentend section can still be used to run the playbook although in my case i created roles that would be used instead
 After the configuration above you can run Vagrant up and then vagrant provision