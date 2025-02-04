# Virtualization

Virtualization is the process of creating a virtual version of a resource, such as a server, storage device, network, or operating system. This virtual version can be used to run multiple instances of the resource on a single physical machine, enabling efficient use of hardware resources and improved flexibility and scalability.

Virtualization can be used in various scenarios, such as server virtualization, desktop virtualization, network virtualization, and storage virtualization. It allows organizations to consolidate their IT infrastructure, reduce costs, improve resource utilization, and enhance disaster recovery and business continuity capabilities.

## Hypervisor

Hypervisor is a software that runs virtual machines. It is responsible for managing the virtual machines and providing them with the necessary resources. There are different types of hypervisors, such as **Type 1** and **Type 2** hypervisors.

### Type 1 Hypervisor

Type 1 hypervisor, also known as bare-metal hypervisor, runs directly on the physical hardware of the host machine. It does not require a host operating system and provides direct access to the hardware resources. _Examples_ of Type 1 hypervisors include VMware ESXi, Microsoft Hyper-V, and Citrix XenServer. It run directly on the host's hardware mostly use in production and it run as Base OS, while _Type 2_ hypervisors run on top of the host's operating system.It can also be clustered meaning multiple hypervisors can be managed as a single entity.

### Type 2 Hypervisor

Type 2 hypervisor, also known as hosted hypervisor, runs on a host operating system like Software. It requires a host operating system to provide the necessary services and resources for running virtual machines. _Examples_ of Type 2 hypervisors include VMware Workstation, Oracle VirtualBox, and Parallels Desktop. It run on top of the host's operating system and mostly use for development and testing purposes.

## Host OS and Guest OS

Host OS is the operating system that runs on the physical hardware of the host machine. It provides the necessary services and resources for running applications and managing hardware. In the context of virtualization, the host OS is the operating system that runs on the physical server hosting the virtual machines

Guest OS is the operating system that runs on a virtual machine. It is independent of the host OS and can be different from the host OS. The guest OS interacts with the virtual hardware provided by the hypervisor and runs applications within the virtual machine environment

## Bridging

Bridge is a network device that connects two or more network segments. In the context of virtualization, bridging refers to connecting a virtual network interface of a virtual machine to a physical network interface of the host machine. This allows the virtual machine to communicate with other devices on the physical network as if it were a physical machine.

## General Steps in Virtual Machine

1. Install a hypervisor software on the host machine.
2. Create a new virtual machine using the hypervisor software.
3. Configure the virtual machine settings, such as memory, CPU, storage, and network.
4. Install an operating system on the virtual machine.
5. Install and configure applications on the virtual machine.
6. Test the virtual machine to ensure that it is working correctly.
7. Remove iso file from the virtual machine. so that it will not boot from the iso file again.
8. Monitor the virtual machine performance and make adjustments as needed.
9. Backup the virtual machine to protect against data loss.
10. Scale the virtual machine as needed to meet changing requirements.
11. Repeat the process to create additional virtual machines as needed.

## Vagrant

Vagrant is an open-source tool for building and managing virtual machine environments. It provides a simple and consistent way to create, configure, and share development environments across different platforms. Vagrant uses virtualization technologies such as VirtualBox, VMware, and Docker to create and manage virtual machines.

Box is a package format for Vagrant environments. It is a compressed file that contains a base image of a virtual machine, along with metadata and configuration files. Boxes are used to create new Vagrant environments by importing them into Vagrant and configuring them with the necessary settings.

Environment is a collection of virtual machines managed by Vagrant. It consists of one or more virtual machines, along with the configuration settings and provisioning scripts needed to set up the environment. Vagrant environments can be shared and reused across different platforms, making it easy to collaborate on development projects.

[Documentation for Command-Line Interface](https://developer.hashicorp.com/vagrant/docs/cli)

### Basic Vagrant Commands

1. `vagrant init` - Initialize a new Vagrant environment with a Vagrantfile.  
   This command creates a default Vagrantfile in your working directory, which you can customize to define the box, network settings, synced folders, and provisioning scripts for your environment.

2. `vagrant up` - Start the Vagrant environment.  
   This command boots your Vagrant machine. If the VM does not exist yet, Vagrant will download the specified box (if not already available), create the VM, and then provision it according to the settings in the Vagrantfile.

3. `vagrant ssh` - SSH into the Vagrant environment.  
   This command opens an SSH connection to your running Vagrant guest instance, allowing you to interact with the guest OS directly from your terminal.

4. `vagrant halt` - Stop the Vagrant environment.  
   This gracefully shuts down the virtual machine, similar to powering it off. It saves the current state so you can later restart the environment.

5. `vagrant destroy` - Destroy the Vagrant environment.  
   This permanently removes the virtual machine and its associated resources, freeing up system resources. You will need to run `vagrant up` again to recreate the VM if needed.

6. `vagrant status` - Check the status of the Vagrant environment.  
   This shows you whether your virtual machines are running, halted, suspended, or in another state, helping you manage and troubleshoot your environments.

7. `vagrant reload` - Reload the Vagrant environment.  
   This command restarts the virtual machine and applies any changes made to the Vagrantfile, effectively reprovisioning the VM without having to completely halt and up it again.

8. `vagrant suspend` - Suspend the Vagrant environment.  
   This pauses your virtual machine by saving its current state to disk, allowing you to resume later without fully shutting down. It is like putting the VM into a sleep mode.

9. `vagrant resume` - Resume the suspended Vagrant environment.  
   This command wakes up a previously suspended VM and restores it to its running state, so you can continue your work where you left off.

10. `vagrant provision` - Run the provisioners defined in the Vagrantfile.  
    If you have specified provisioning scripts (using shell scripts, Puppet, Chef, etc.) in your Vagrantfile, this command will execute them, updating the configuration or installing software on the guest machine.

11. `vagrant box list` - List the available Vagrant boxes.  
    This shows all boxes you have downloaded or added to your local Vagrant box repository, which you can use in your Vagrant environments.

12. `vagrant box add` - Add a new Vagrant box to the local box repository.  
    Use this command with a box name or a URL to download and install a box that you can later reference in your Vagrantfile when initializing an environment.

13. `vagrant box remove` - Remove a Vagrant box from the local box repository.  
    This command deletes unwanted or outdated box images from your local repository, which can help free up disk space.

14. `vagrant plugin install` - Install a Vagrant plugin.  
    Vagrant plugins extend the functionality of Vagrant. Use this command to install third-party tools or extensions that can add features like enhanced networking, custom workflows, or integration with other services.

15. `vagrant plugin uninstall` - Uninstall a Vagrant plugin.  
    This allows you to remove plugins that you no longer need, helping to keep your Vagrant installation lean and less prone to conflicts.

16. `vagrant plugin list` - List the installed Vagrant plugins.  
    Use this command to see all the plugins currently active in your Vagrant environment, which is helpful for troubleshooting and ensuring proper plugin versions.

17. `vagrant global-status` - Show the status of all Vagrant environments on the host machine.  
    This command lists every Vagrant-managed virtual machine on your host, along with their directories and current states. It is useful for managing multiple projects or cleaning up orphaned machines.

18. `exit` - Exit the SSH session in the Vagrant environment.  
    Simply typing `exit` will close your SSH session and return you to your host machine's terminal.

Only Vagrant User can switch to root user by using `sudo -i` command.
