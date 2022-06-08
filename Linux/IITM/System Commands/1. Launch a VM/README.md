# Launching a Virtual Machine

Date: December 22, 2021
Lecture #: 1
Lecture URL: https://youtu.be/PHrN7yp1AJw
Notion URL: https://21f1003586.notion.site/Launching-a-Virtual-Machine-e493cecce6a743a9b37516d196c07c1d
Type: 📒 Lecture
Week #: 1

### Why do we need a Virtual Machine (VM)?

- Laptops usually come pre-installed with Windows
    - Unless, of course, you are an 🍎 person
- We wish to try Linux almost natively, without removing the existing OS
    - Also considering the fact that we do not wish to dual boot

### Requirements

- An .iso image of the operating system we want
    - Ubuntu 20.04 is recommended, or just use arch btw
        
        ![xkcd.png](Launching%20a%20Virtual%20Machine%20fbbd766e3aa145798901ceecaa9d50ec/xkcd.png)
        
        - Can be downloaded [here](https://ubuntu.com/download/desktop)
- A Hypervisor
    - A **hypervisor**, also known as a virtual machine monitor or VMM, is
    software that creates and runs virtual machines (VMs). A hypervisor
    allows one host computer to support multiple guest VMs by virtually
    sharing its resources, such as memory and processing.
        
        *Source: [https://www.vmware.com/topics/glossary/content/hypervisor.html](https://www.vmware.com/topics/glossary/content/hypervisor.html)*
        
    - [Oracle VirtualBox](https://www.virtualbox.org/)
    - [VMWare Workstation Player](https://www.vmware.com/in/products/workstation-player/workstation-player-evaluation.html)
    - or just use [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/about)
    - Atleast 20GB free space for the VM
    - Some RAM ¯\_(ツ)_/¯
        - 8GB+ recommended

### Steps

- Download the Ubuntu .iso file from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
- Download either VirtualBox or the VMWare Workstation Player
    - Install them
- Open VirtualBox / VMWare Workstation Player
    
    (I will be using VirtualBox)
    
    - Click on the “New Button to create a new VM”
        
        ![Untitled](Launching%20a%20Virtual%20Machine%20fbbd766e3aa145798901ceecaa9d50ec/Untitled.png)
        
    - Add a name and choose the OS type and version
        
        ![Untitled](Launching%20a%20Virtual%20Machine%20fbbd766e3aa145798901ceecaa9d50ec/Untitled%201.png)
        
    - Adjust the RAM and Storage as per your liking, make sure to keep the minimum specs
    - Select the VM on the left menu and go to settings
        
        ![Untitled](Launching%20a%20Virtual%20Machine%20fbbd766e3aa145798901ceecaa9d50ec/Untitled%202.png)
        
    - Go to Storage → Storage Devices → Controller → Empty → Click on the CD icon and choose “**Choose/Create a Virtual Optical Disk...**” and choose your .iso file
        
        ![Untitled](Launching%20a%20Virtual%20Machine%20fbbd766e3aa145798901ceecaa9d50ec/Untitled%203.png)
        
    - Proceed with the installation
        - Uhh it’s just Next, Next, Next .... Next ... Restart

When you install it correctly and get it up and running, you might see something like this ...

![VirtualBox_Ubuntu_22_12_2021_01_30_33.png](Launching%20a%20Virtual%20Machine%20fbbd766e3aa145798901ceecaa9d50ec/VirtualBox_Ubuntu_22_12_2021_01_30_33.png)

*(this screenshot here is Ubuntu 21.10 and gosh that’s a creepy monke)*