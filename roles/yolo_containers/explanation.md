## Provision a geerlingguy/ubuntu2004 using vagrant and deploy Yolo app using ansible

## Implementation plan

  ## prerequisites 
  1. Install Vagrant
  2. Install VirtualBox

## Step 1
 Provision a geerlingguy/ubuntu2004 instance using Vagrant manually on your local machine.
  Follow these steps:

 `
 Create a new directory and navigate to it.
 Execute the following command to initialize a Vagrant configuration file:

`
 vagrant init geerlingguy/ubuntu2004

 `

`
  A Vagrantfile will be generated in the current directory.
  Open the Vagrantfile in a text editor and locate the following lines:

`
  config.vm.box = "geerlingguy/ubuntu2004"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  vb.memory = "1024"
  end
  config.vm.provider "virtualbox" do |vb|
`
  Uncomment the lines and add the following line to allow insecure box downloads:
  

`
  config.vm.box_download_insecure = true
`

Save the Vagrantfile.

Run the following command to download the Ubuntu virtual machine:
`
vagrant up

`
Then run below to access the virtual machine

`
vagrant ssh
`

## Step 2 

Clone and deploy the Yolo application using Ansible and Docker:

Create a vars.yml file for add the variables
Create a roles directory then a task directory the a main.yml file for the container roles

In the main.yml file under the container role, define tasks to clone the repository.

Define tasks for building the client and backend Docker images.

Create a new folder and copy the docker-compose.yaml file from the cloned project into this directory.

Define tasks to run the containers based on the docker-compose.yaml file.

Confirm the services are running and accessible by executing the following command:

`
ansible-playbook playbook.yml --tags containers

`

