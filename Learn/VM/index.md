# Virtualization

## Table of Contents

- [Virtualization](#virtualization)
- [Hypervisor](#hypervisor)
  - [Type 1 Hypervisor (Bare-Metal)](#type-1-hypervisor-bare-metal)
  - [Type 2 Hypervisor (Hosted)](#type-2-hypervisor-hosted)
- [Host OS and Guest OS](#host-os-and-guest-os)
- [Bridging](#bridging)
- [General Steps in Virtual Machine Creation](#general-steps-in-virtual-machine-creation)
- [Vagrant](#vagrant)
  - [Basic Vagrant Commands](#basic-vagrant-commands)
  - [Sample Vagrantfile](#sample-vagrantfile)
- [Provisioning](#provisioning)
  - [Vagrant Provisioning](#vagrant-provisioning)
  - [Provisioning Examples](#provisioning-examples)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)

Virtualization is the process of creating a virtual version of a resource, such as a server, storage device, network, or operating system. This virtual version can be used to run multiple instances of the resource on a single physical machine, enabling efficient use of hardware resources and improved flexibility and scalability.

Virtualization can be used in various scenarios, such as server virtualization, desktop virtualization, network virtualization, and storage virtualization. It allows organizations to consolidate their IT infrastructure, reduce costs, improve resource utilization, and enhance disaster recovery and business continuity capabilities.

**Key Benefits of Virtualization:**

- **Resource Efficiency**: Run multiple VMs on a single physical server
- **Isolation**: Keep applications separate to prevent conflicts
- **Snapshots and Backups**: Easily create backups and restore points
- **Rapid Deployment**: Quickly spin up new environments from templates
- **Testing and Development**: Safely test configurations without affecting production
- **Disaster Recovery**: Simplify backup and recovery processes

## Hypervisor

A hypervisor is a software that runs virtual machines (VMs). It is responsible for managing the VMs and providing them with the necessary resources. There are two main types of hypervisors: **Type 1** and **Type 2**.

### Type 1 Hypervisor (Bare-Metal)

Type 1 hypervisors, also known as bare-metal hypervisors, run directly on the physical hardware of the host machine. They do not require a host operating system and provide direct access to the hardware resources. Type 1 hypervisors are typically used in production environments due to their high performance and efficiency. They can also be clustered, meaning multiple hypervisors can be managed as a single entity.

_Examples_ of Type 1 hypervisors include:

- **VMware ESXi**
  - Enterprise-grade solution
  - Supports advanced features like vMotion (live migration)
  - Used in large data centers
- **Microsoft Hyper-V Server**
  - Integrated with Windows Server environments
  - Good for Windows-centric organizations
- **Citrix XenServer**
  - Open-source roots
  - Good for mixed environments
- **KVM (Kernel-based Virtual Machine)**
  - Linux-based open-source solution
  - Popular in open-source environments
- **Proxmox VE**
  - Combines KVM with container-based virtualization

**Use Cases for Type 1 Hypervisors:**

- Enterprise server consolidation
- Cloud hosting environments
- Mission-critical production workloads
- Environments requiring maximum performance

### Type 2 Hypervisor (Hosted)

Type 2 hypervisors, also known as hosted hypervisors, run on top of a host operating system. They require a host operating system to provide the necessary services and resources for running virtual machines. Type 2 hypervisors are often used for development and testing purposes.

_Examples_ of Type 2 hypervisors include:

- **VMware Workstation/Player**
  - Feature-rich desktop virtualization
  - Available in both free and paid versions
  - Strong snapshot capabilities
- **Oracle VirtualBox**
  - Open-source and free
  - Cross-platform compatibility
  - Good for beginners
- **Parallels Desktop**
  - Mac-specific solution
  - Optimized for running Windows on macOS
  - Seamless integration features
- **QEMU**
  - Open-source emulator and virtualizer
  - Supports many architectures

**Use Cases for Type 2 Hypervisors:**

- Development and testing environments
- Learning and education
- Running multiple operating systems on a desktop/laptop
- Software compatibility testing

## Host OS and Guest OS

- **Host OS**: The operating system that runs on the physical hardware of the host machine. It provides the necessary services and resources for running applications and managing hardware. In the context of virtualization, the host OS is the operating system that runs on the physical server hosting the virtual machines.
- **Guest OS**: The operating system that runs on a virtual machine. It is independent of the host OS and can be different from the host OS. The guest OS interacts with the virtual hardware provided by the hypervisor and runs applications within the virtual machine environment.

**Tips for Host OS Selection:**

- Choose a lightweight host OS to maximize resources available for VMs
- Ensure the host OS is compatible with your chosen hypervisor
- Select an OS with good driver support for your hardware
- Consider security implications and keep the host OS updated
- For production environments, minimize unnecessary services on the host

**Tips for Guest OS Configuration:**

- Install VM tools/guest additions for better performance
- Allocate appropriate resources based on the workload
- Use minimal installations to reduce overhead
- Keep guest OS updated and secured independently from host
- Consider using templates for consistent deployments

## Bridging

Bridging is a networking concept that connects two or more network segments. In the context of virtualization, bridging refers to connecting a virtual network interface of a virtual machine to a physical network interface of the host machine. This allows the virtual machine to communicate with other devices on the physical network as if it were a physical machine.

**Common Network Modes in Virtualization:**

1. **Bridge Networking**

   - Gives VMs direct access to physical network
   - VMs receive their own IP addresses from the network's DHCP server
   - Example configuration in VirtualBox:
     ```
     vboxmanage modifyvm "VM Name" --nic1 bridged --bridgeadapter1 eth0
     ```

2. **NAT (Network Address Translation)**

   - VMs share the host's IP address
   - Host performs translation between VM and external network
   - Good for internet access but limited inbound connectivity
   - Example configuration in VirtualBox:
     ```
     vboxmanage modifyvm "VM Name" --nic1 nat
     ```

3. **Host-Only Networking**

   - Creates a private network between host and VMs
   - VMs cannot access external network directly
   - Good for isolated test environments
   - Example configuration in VirtualBox:
     ```
     vboxmanage modifyvm "VM Name" --nic1 hostonly --hostonlyadapter1 vboxnet0
     ```

4. **Internal Networking**
   - Creates isolated networks between VMs only
   - Host cannot access this network
   - Example configuration in VirtualBox:
     ```
     vboxmanage modifyvm "VM Name" --nic1 intnet --intnet1 "mynetwork"
     ```

## General Steps in Virtual Machine Creation

Here are the general steps to create and manage a virtual machine:

1.  Install a hypervisor software on the host machine.
2.  Create a new virtual machine using the hypervisor software.
3.  Configure the virtual machine settings, such as memory, CPU, storage, and network.
    - **Tip**: Follow the "minimum + 50%" rule for resource allocation based on the OS requirements
    - **Example**: If Windows 10 requires 2GB RAM minimum, allocate at least 3GB
4.  Install an operating system on the virtual machine.
    - **Tip**: Use ISO files mounted as virtual optical drives
    - **Example**: `VBoxManage storageattach "VM Name" --storagectl "IDE Controller" --port 0 --device 0 --type dvddrive --medium /path/to/os.iso`
5.  Install and configure applications on the virtual machine.
6.  Test the virtual machine to ensure that it is working correctly.
7.  Remove the ISO file from the virtual machine settings so that it will not boot from the ISO file again.
8.  Monitor the virtual machine performance and make adjustments as needed.
    - **Tip**: Use built-in monitoring tools to identify resource bottlenecks
    - **Example**: In VirtualBox, use `VBoxManage metrics setup` to monitor resource usage
9.  Backup the virtual machine to protect against data loss.
    - **Tip**: Create snapshots before major changes
    - **Example**: `VBoxManage snapshot "VM Name" take "Before Update" --description "Snapshot before system update"`
10. Scale the virtual machine as needed to meet changing requirements.
11. Repeat the process to create additional virtual machines as needed.

**Best Practice**: Create a VM template once configured properly to quickly deploy new instances

## Vagrant

Vagrant is an open-source tool for building and managing virtual machine environments. It provides a simple and consistent way to create, configure, and share development environments across different platforms. Vagrant uses virtualization technologies such as VirtualBox, VMware, and Docker to create and manage virtual machines.

- **Box**: A package format for Vagrant environments. It is a compressed file that contains a base image of a virtual machine, along with metadata and configuration files. Boxes are used to create new Vagrant environments by importing them into Vagrant and configuring them with the necessary settings.
- **Environment**: A collection of virtual machines managed by Vagrant. It consists of one or more virtual machines, along with the configuration settings and provisioning scripts needed to set up the environment. Vagrant environments can be shared and reused across different platforms, making it easy to collaborate on development projects.

**Popular Vagrant Boxes:**

- `ubuntu/focal64` - Ubuntu 20.04 LTS
- `centos/7` - CentOS 7
- `debian/bullseye64` - Debian 11
- `generic/alpine312` - Alpine Linux 3.12
- `hashicorp/bionic64` - Ubuntu 18.04 LTS

**Finding Boxes:**

- Official Vagrant box catalog: [https://app.vagrantup.com/boxes/search](https://app.vagrantup.com/boxes/search)
- Command line: `vagrant box search term`

[Documentation for Command-Line Interface](https://developer.hashicorp.com/vagrant/docs/cli)

### Basic Vagrant Commands

Here are some basic Vagrant commands:

1.  `vagrant init`: Initialize a new Vagrant environment with a Vagrantfile.

    This command creates a default `Vagrantfile` in your working directory, which you can customize to define the box, network settings, synced folders, and provisioning scripts for your environment.

    ```bash
    vagrant init
    # Initialize with specific box
    vagrant init ubuntu/focal64
    ```

2.  `vagrant up`: Start the Vagrant environment.

    This command boots your Vagrant machine. If the VM does not exist yet, Vagrant will download the specified box (if not already available), create the VM, and then provision it according to the settings in the `Vagrantfile`.

    ```bash
    vagrant up
    # Start a specific machine in multi-VM environment
    vagrant up web-server
    ```

3.  `vagrant ssh`: SSH into the Vagrant environment.

    This command opens an SSH connection to your running Vagrant guest instance, allowing you to interact with the guest OS directly from your terminal.

    ```bash
    vagrant ssh
    # Connect to a specific machine
    vagrant ssh database
    # Run a command directly
    vagrant ssh -c "ls -la /var/www"
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

### Sample Vagrantfile

Below is a sample Vagrantfile that demonstrates various configuration options:

```ruby
Vagrant.configure("2") do |config|
  # Define the base box
  config.vm.box = "ubuntu/focal64"

  # Set up a forwarded port
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Set up a private network
  config.vm.network "private_network", type: "dhcp"

  # Set up a synced folder
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

  # Provision the VM using a shell script
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
  SHELL
end
```

## Provisioning

Provisioning is the process of setting up and configuring software, services, and resources on a virtual machine or server. It involves installing and configuring the necessary components, such as operating systems, applications, databases, and networking settings, to prepare the system for use. Provisioning can be done manually or automated using tools like shell scripts, configuration management tools (e.g., Puppet, Chef, Ansible), and cloud orchestration platforms (e.g., Terraform).

### Vagrant Provisioning

Vagrant allows you to automate the provisioning of virtual machines using shell scripts, configuration management tools, and other provisioning methods. You can define provisioning scripts in the `Vagrantfile` to set up the environment according to your requirements. Vagrant supports various provisioners, such as shell, Puppet, Chef, Ansible, and Salt, to automate the installation and configuration of software and services on the guest machine.

Example of shell provisioning in `Vagrantfile`:

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y nginx
  SHELL
end
```

### Provisioning Examples

**Using Puppet:**

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provision "puppet" do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file  = "site.pp"
  end
end
```

**Using Chef:**

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provision "chef_solo" do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe "apache2"
  end
end
```

**Using Ansible:**

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
```

## Best Practices

- **Use Version Control**: Keep your `Vagrantfile` and provisioning scripts in version control (e.g., Git) to track changes and collaborate with others.
- **Use Base Boxes**: Start with a minimal base box and customize it using provisioning scripts to ensure consistency and reduce the size of your Vagrant environment.
- **Automate Everything**: Automate the setup and configuration of your Vagrant environment to ensure repeatability and reduce manual errors.
- **Use Plugins**: Leverage Vagrant plugins to extend functionality and integrate with other tools and services.
- **Clean Up**: Regularly clean up unused boxes and environments to free up disk space and resources.
- **Document**: Document your Vagrant environment and provisioning scripts to make it easier for others to understand and use.

## Troubleshooting

- **Check Logs**: Review Vagrant logs (`vagrant up --debug`) to identify issues during the VM creation and provisioning process.
- **Network Issues**: Ensure that your network settings (e.g., forwarded ports, private networks) are correctly configured and not conflicting with other services.
- **Resource Allocation**: Verify that your host machine has sufficient resources (CPU, memory, disk space) to run the Vagrant environment.
- **Box Compatibility**: Ensure that the Vagrant box you are using is compatible with your Vagrant version and hypervisor.
- **Update Vagrant**: Keep Vagrant and its plugins up to date to benefit from the latest features and bug fixes.
- **Community Support**: Leverage the Vagrant community (forums, GitHub issues, Stack Overflow) for help with common issues and best practices.
