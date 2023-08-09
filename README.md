# Microserver Uptime

Microserver Uptime is a concise bash script specifically designed to operate on Linux/Unix servers. It counts the number of days a Web Server has been operational. This script is tailor-made for Single Board Computers (SBCs) including Raspberry Pi, Rock Pi, and Orange Pi.The purpose of Uptime is to record number of days a microserver hardware can run a webserver during its lifetime. 

These SBCs are recognized for their cost-effectiveness and their ability as powerful microserver hardware systems that perform excellently as Web Servers. They can host various websites and operate for a prolonged duration with minimal upkeep. A recent study by [Dhuny et al.,(2022)](https://www.sciencedirect.com/science/article/pii/S2590005622000479) highlighted their ability to support up to 40 concurrent users.

These units offer ideal solutions for edge computing, can be installed on-premises or utilized as home-hosting solutions. They require negligible cooling and consume minimal power.

The script installs as a service on Ubuntu, automatically counting and calculating the number of days a web server has been active on a microserver. This data is beneficial for measuring and comparing the reliability of different microserver hardware solutions.

The source codes are open source, making them modifiable to run on any hardware with a Linux OS. Currently, the service is operational on [RPI64Box (Dhuny and Mohamudally,2022)](https://www.sciencedirect.com/science/article/pii/S2665963822000872). Each SBC's unique serial number is used to identify the hardware in use upon installation.

The setup process employs ansible and can be installed as described below.

## Prerequisites

Before you begin, ensure you have met the following requirements:
* Your system is a Linux-based OS with `systemd`
* You have `sudo` privileges

## Installing Microserver Uptime

To install Microserver Uptime, follow these steps:

1. Install Ansible on your system. In a Debian-based system, you would run:

    ```bash
    sudo apt-get update
    sudo apt-get install ansible
    ```

2. Clone the Git repository:

    ```bash
    git clone https://github.com/dhuny/uptime.git
    ```

3. Navigate into the cloned directory:

    ```bash
    cd uptime
    ```

4. Run the ansible playbook to setup:

    ```bash
    ansible-playbook -i inventory.ini microserver_setup.yml
    ```
	
## Getting the number of days

To display the number of days a web server is running on a hardware

```bash
sudo service microserver status
```

## Version of Uptime

To display the version number of uptime

```bash
sudo /etc/microserver/microserverUptime.sh -v
```

## Uninstalling Microserver Uptime

If you want to remove the setup, run the following command:

```bash
ansible-playbook -i inventory.ini remove_microserver_setup.yml
```
	
## Reference

Dhuny, R. and Mohamudally, N.A. (2022), “RPI64Box: A portable 3-tiered LAMP stack in a 64-bit Operating System environment”, [Software Impacts, Vol. 14, p. 100390](https://www.sciencedirect.com/science/article/pii/S2665963822000872).

Dhuny, R., Peer, A.A.I., Mohamudally, N.A. and Nissanke, N. (2022), “Performance evaluation of a portable single-board computer as a 3-tiered LAMP stack under 32-bit and 64-bit Operating Systems”, [Array, Vol. 15, p. 100196](https://www.sciencedirect.com/science/article/pii/S2590005622000479).


