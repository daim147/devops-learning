# Virtualization

Virtualization is the process of creating a virtual version of a resource, such as a server, storage device, network, or operating system. This virtual version can be used to run multiple instances of the resource on a single physical machine, enabling efficient use of hardware resources and improved flexibility and scalability.

Virtualization can be used in various scenarios, such as server virtualization, desktop virtualization, network virtualization, and storage virtualization. It allows organizations to consolidate their IT infrastructure, reduce costs, improve resource utilization, and enhance disaster recovery and business continuity capabilities.

## Hypervisor

A hypervisor is a software that runs virtual machines (VMs). It is responsible for managing the VMs and providing them with the necessary resources. There are two main types of hypervisors: **Type 1** and **Type 2**.

### Type 1 Hypervisor (Bare-Metal)

Type 1 hypervisors, also known as bare-metal hypervisors, run directly on the physical hardware of the host machine. They do not require a host operating system and provide direct access to the hardware resources. Type 1 hypervisors are typically used in production environments due to their high performance and efficiency. They can also be clustered, meaning multiple hypervisors can be managed as a single entity.

_Examples_ of Type 1 hypervisors include:

- VMware ESXi
- Microsoft Hyper-V
- Citrix XenServer

### Type 2 Hypervisor (Hosted)

Type 2 hypervisors, also known as hosted hypervisors, run on top of a host operating system. They require a host operating system to provide the necessary services and resources for running virtual machines. Type 2 hypervisors are often used for development and testing purposes.

_Examples_ of Type 2 hypervisors include:

- VMware Workstation
- Oracle VirtualBox
- Parallels Desktop

## Host OS and Guest OS

- **Host OS**: The operating system that runs on the physical hardware of the host machine. It provides the necessary services and resources for running applications and managing hardware. In the context of virtualization, the host OS is the operating system that runs on the physical server hosting the virtual machines.
- **Guest OS**: The operating system that runs on a virtual machine. It is independent of the host OS and can be different from the host OS. The guest OS interacts with the virtual hardware provided by the hypervisor and runs applications within the virtual machine environment.

## Bridging

Bridging is a networking concept that connects two or more network segments. In the context of virtualization, bridging refers to connecting a virtual network interface of a virtual machine to a physical network interface of the host machine. This allows the virtual machine to communicate with other devices on the physical network as if it were a physical machine.

## General Steps in Virtual Machine Creation

Here are the general steps to create and manage a virtual machine:

1.  Install a hypervisor software on the host machine.
2.  Create a new virtual machine using the hypervisor software.
3.  Configure the virtual machine settings, such as memory, CPU, storage, and network.
4.  Install an operating system on the virtual machine.
5.  Install and configure applications on the virtual machine.
6.  Test the virtual machine to ensure that it is working correctly.
7.  Remove the ISO file from the virtual machine settings so that it will not boot from the ISO file again.
8.  Monitor the virtual machine performance and make adjustments as needed.
9.  Backup the virtual machine to protect against data loss.
10. Scale the virtual machine as needed to meet changing requirements.
11. Repeat the process to create additional virtual machines as needed.

## Vagrant

Vagrant is an open-source tool for building and managing virtual machine environments. It provides a simple and consistent way to create, configure, and share development environments across different platforms. Vagrant uses virtualization technologies such as VirtualBox, VMware, and Docker to create and manage virtual machines.

- **Box**: A package format for Vagrant environments. It is a compressed file that contains a base image of a virtual machine, along with metadata and configuration files. Boxes are used to create new Vagrant environments by importing them into Vagrant and configuring them with the necessary settings.
- **Environment**: A collection of virtual machines managed by Vagrant. It consists of one or more virtual machines, along with the configuration settings and provisioning scripts needed to set up the environment. Vagrant environments can be shared and reused across different platforms, making it easy to collaborate on development projects.

[Documentation for Command-Line Interface](https://developer.hashicorp.com/vagrant/docs/cli)

### Basic Vagrant Commands

Here are some basic Vagrant commands:

1.  `vagrant init`: Initialize a new Vagrant environment with a Vagrantfile.

    This command creates a default `Vagrantfile` in your working directory, which you can customize to define the box, network settings, synced folders, and provisioning scripts for your environment.

    ```bash
    vagrant init
    ```

2.  `vagrant up`: Start the Vagrant environment.

    This command boots your Vagrant machine. If the VM does not exist yet, Vagrant will download the specified box (if not already available), create the VM, and then provision it according to the settings in the `Vagrantfile`.

    ```bash
    vagrant up
    ```

3.  `vagrant ssh`: SSH into the Vagrant environment.

    This command opens an SSH connection to your running Vagrant guest instance, allowing you to interact with the guest OS directly from your terminal.

    ```bash
    vagrant ssh
    ```

4.  `vagrant halt`: Stop the Vagrant environment.

    This gracefully shuts down the virtual machine, similar to powering it off. It saves the current state so you can later restart the environment.

    ```bash
    vagrant halt
    ```

5.  `vagrant destroy`: Destroy the Vagrant environment.

    This permanently removes the virtual machine and its associated resources, freeing up system resources. You will need to run `vagrant up` again to recreate the VM if needed. `vagrant destroy -f` will destroy the VM without confirmation.

    ```bash
    vagrant destroy
    ```

6.  `vagrant status`: Check the status of the Vagrant environment.

    This shows you whether your virtual machines are running, halted, suspended, or in another state, helping you manage and troubleshoot your environments.

    ```bash
    vagrant status
    ```

7.  `vagrant reload`: Reload the Vagrant environment.

    This command restarts the virtual machine and applies any changes made to the `Vagrantfile`, effectively reprovisioning the VM without having to completely halt and up it again.

    ```bash
    vagrant reload
    ```

8.  `vagrant suspend`: Suspend the Vagrant environment.

    This pauses your virtual machine by saving its current state to disk, allowing you to resume later without fully shutting down. It is like putting the VM into a sleep mode.

    ```bash
    vagrant suspend
    ```

9.  `vagrant resume`: Resume the suspended Vagrant environment.

    This command wakes up a previously suspended VM and restores it to its running state, so you can continue your work where you left off.

    ```bash
    vagrant resume
    ```

10. `vagrant provision`: Run the provisioners defined in the Vagrantfile.

    If you have specified provisioning scripts (using shell scripts, Puppet, Chef, etc.) in your `Vagrantfile`, this command will execute them, updating the configuration or installing software on the guest machine.

    ```bash
    vagrant provision
    ```

11. `vagrant box list`: List the available Vagrant boxes.

    This shows all boxes you have downloaded or added to your local Vagrant box repository, which you can use in your Vagrant environments.

    ```bash
    vagrant box list
    ```

12. `vagrant box add`: Add a new Vagrant box to the local box repository.

    Use this command with a box name or a URL to download and install a box that you can later reference in your `Vagrantfile` when initializing an environment.

    ```bash
    vagrant box add hashicorp/ubuntu-22.04
    ```

13. `vagrant box remove`: Remove a Vagrant box from the local box repository.

    This command deletes unwanted or outdated box images from your local repository, which can help free up disk space.

    ```bash
    vagrant box remove hashicorp/ubuntu-22.04
    ```

14. `vagrant plugin install`: Install a Vagrant plugin.

    Vagrant plugins extend the functionality of Vagrant. Use this command to install third-party tools or extensions that can add features like enhanced networking, custom workflows, or integration with other services.

    ```bash
    vagrant plugin install vagrant-vbguest
    ```

15. `vagrant plugin uninstall`: Uninstall a Vagrant plugin.

    This allows you to remove plugins that you no longer need, helping to keep your Vagrant installation lean and less prone to conflicts.

    ```bash
    vagrant plugin uninstall vagrant-vbguest
    ```

16. `vagrant plugin list`: List the installed Vagrant plugins.

    Use this command to see all the plugins currently active in your Vagrant environment, which is helpful for troubleshooting and ensuring proper plugin versions.

    ```bash
    vagrant plugin list
    ```

17. `vagrant global-status`: Show the status of all Vagrant environments on the host machine.

    This command lists every Vagrant-managed virtual machine on your host, along with their directories and current states. It is useful for managing multiple projects or cleaning up orphaned machines.

    ```bash
    vagrant global-status
    ```

18. `exit`: Exit the SSH session in the Vagrant environment.

    Simply typing `exit` will close your SSH session and return you to your host machine's terminal.

    ```bash
    exit
    ```

Only the Vagrant user can switch to the root user by default by using the `sudo -i` command.

`~/.vagrant.d` is the default directory where Vagrant stores its configuration files, boxes, and plugins.

A shared folder is a directory on the host machine that is accessible from the guest machine. It allows you to share files between the host and guest machines, making it easy to transfer data and collaborate on projects. Shared folders can be configured in the `Vagrantfile` using the `config.vm.synced_folder` directive. The default shared folder is `/vagrant` in the guest machine, which corresponds to the directory containing the `Vagrantfile` on the host machine.

## Provisioning

Provisioning is the process of setting up and configuring software, services, and resources on a virtual machine or server. It involves installing and configuring the necessary components, such as operating systems, applications, databases, and networking settings, to prepare the system for use. Provisioning can be done manually or automated using tools like shell scripts, configuration management tools (e.g., Puppet, Chef, Ansible), and cloud orchestration platforms (e.g., Terraform).

### Vagrant Provisioning

Vagrant allows you to automate the provisioning of virtual machines using shell scripts, configuration management tools, and other provisioning methods. You can define provisioning scripts in the `Vagrantfile` to set up the environment according to your requirements. Vagrant supports various provisioners, such as shell, Puppet, Chef, Ansible, and Salt, to automate the installation and configuration of software and services on the guest machine.

Example of shell provisioning in `Vagrantfile`:
