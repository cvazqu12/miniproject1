# Mini Project #1 
## by Christopher Vazquez

### <div style="text-align:center">Objective</div> 

The objective of this exercise is to conjoin two separate local area networks, with each LAN containing a plethora of end devices, such as a DNS, DHCP, Web Server, and some personal devices like a laptop and PC. Each PC and Laptop should be able to access the services from the separate LAN. 

***

### <div style="text-align:center">Use Cases</div>

Scenario #1: These are the building blocks used for creating a private Intranet, where information does not leave the network. If you're able to create a direct connection (that you own) between two different Data Centers, this method would work. 

Scenario #2: IoT devices are traditionally not secure, so you can isolate these devices in its own separate network. 

***

### <div style="text-align:center">Detailed Steps</div>

**<div style="color:skyblue">Step 1: Procure the nessecary equipment for this lab. In the case of the Diagram attached to this repository, we will need:</div>** 

   - Four computers (two for each LAN)
   - A Router (Cisco 2900 series)
   - Two Switches
   - Six RJ45 Ethernet cables
   - One serial cable (USB to DB9 to RJ45)

**<div style="color:skyblue">Step 2: Connect all of your devices together.</div>**

Please refer to the system architecture diagram in ***Figure 1***, as all of the end devices for each LAN need to connect into their switch. The only devices that the router will connect to are the switches.

---

**<div style="color:skyblue">Step 3: Prepping the Router</div>**

Please take the serial to RJ45 adapter and plug the RJ45 end into the CONSOLE port of the router. Connect the other end directly into your computer. 

**<div style="color:skyblue">Step 3.1: Console in</div>**

Please ensure that you one of the following programs installed, dependent on your operating system:

 - macOS: homebrew
 - Linux: apt-get
 - Windows: PuTTY

 Regardless of your operating system, you will need to find the port that your serial cable is connected to. 

For Windows devices, find the port in your Device Manager. Look for the submenu "Ports (COM & LPT). Make note of the port you see (such as COM1, COM2, COM#). 

Go to PuTTY, set the connection to serial, and paste the port found from the Device Manager. The default Baud rate is 9600, so change this setting if it is *not* 9600, as the connection will fail.

Click on Connect. If successful, you will see a black window pop up. Hit return until you see a prompt, such as "Router>"

For Unix devices (macOS, Linux): open your terminal and type ls /dev/*usb* to find the port need to console in. An example would be "usbtty0".

If you do not have "screen" installed already, please do the following.

Linux: <code>sudo apt-get install screen</code>


Once downloaded, ensure that the cable is connected to your computer and the router. **Ensure the router is on.**

Both Linux and macOS devices simply need to write the following command. Replace the brackets with the port found earlier without the quotes. Use sudo if it fails. If successful, the terminal will go blank. Hit return until you see a prompt, such as "Router>"

<code>screen /dev/{port} 9600</code>

Example: <code style="color:skyblue">screen /dev/usbtty0 9600</code>

**<div style="color:skyblue">Step 3.2: Configuring the router</div>**

For this lab, we will be using a Cisco 2900 series router, so these instructions are meant specifically for Cisco's IOS. Please consult your router's documentation if the router does match.

Please take a look at Figure 2 for the commands to set up a port configuration on a Cisco 2900 Series Router. This is for LAN 0. Repeat the same steps for LAN1. 

**<div style="color:skyblue">Step 4: Configuring End Devices</div>**

Once your router is configured, each of the end devices need to have their IP addresses configured. Each system will not have the same configuration, but they all need to have mappings for:

    - Default Gateway
    - DNS Server
    - Personal IP address 
    - Subnet Mask

For example, let's take a look at Web Server0's configuration:

Since the IP block is 192.168.0.0/26, we can use the information to plug in the following.

    - Default Gateway (or Router IP): 192.168.0.1
    - DNS Server: 192.168.0.3 

    - Personal IP address: 192.168.0.4
    - Subnet Mask: 255.255.255.192

For DNS, NAMO was used for DNS and Apache2 was used for the Web server.













    

