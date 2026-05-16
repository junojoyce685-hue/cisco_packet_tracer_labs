**BASIC PASSWORD CONFIGURATION IN PACKET TRACER**

**1. Configure Password on Switch Through a Console Line Using a PC**

<img width="184" height="134" alt="image" src="https://github.com/user-attachments/assets/9a62e27e-d7fa-44aa-b605-7ced5b7e4c3c" />

As shown in the image, drag and drop a PC from the End Devices section and a Switch from the Network Devices Section
in the bottom of packet tracer. Select the console line[blue] from the connections section in the bottom, plug in by clicking on it and then on PC ad switch.
On PC, select RS 232 and on switch, select Console ports respectively.
Click on PC, navigate to Desktop -> Command Line, click Ok on default configurations. 

**Terminal Commands:**

Press RETURN to get started!

Switch>en

Switch#conf t

Enter configuration commands, one per line.  End with CNTL/Z.

Switch(config)#enable secret password1

Switch(config)#line console 0

Switch(config-line)#password password0

Switch(config-line)#login

Switch(config-line)#exit

Switch(config)#end

Switch#

%SYS-5-CONFIG_I: Configured from console by console

Switch#exit

**NOTE : THIS PASSWORD IS NOT SAFE AS IT IS STORED AS PLAIN TEXT IN THE RUNNING CONFIGURATION FILE !**

**You can simply write   #sh r    instead of the whole #show running-config to check this**

Check running configuration file :

Switch#sh r

Building configuration...

Current configuration : 1156 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname Switch
!
enable secret 5 $1$mERr$bufOnTwckI.adrhVdRrUB0
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
....
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
!
!
!
line con 0
<mark> password password0 </mark>
 login
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end


***USE THE #service password-encrypt     COMMAND TO ENCRYPT THIS***


Switch(config)#service password-encrypt

Switch(config)#exit

Switch#
%SYS-5-CONFIG_I: Configured from console by console

Switch#sh r
Building configuration...

Current configuration : 1166 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname Switch
!
enable secret 5 $1$mERr$bufOnTwckI.adrhVdRrUB0
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!....
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 no ip address
 shutdown
!
!
!
!
line con 0
<mark> password 7 08314D5D1A0E0A05165B </mark>
 login
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end


**NOTE : This Password Is Still Very Weak And Can Be Easy Decrypted**

**2. FOR CONSOLE CONFIG ON A ROUTER USING A USB PORT ON LAPTOP**

<img width="173" height="142" alt="image" src="https://github.com/user-attachments/assets/c98eb556-851d-45bc-bd45-d614502b39bb" />


Drag the Laptop and Router 4321 from End Device and Network Device sections respetively, and select the USB cable[purple] from the conncetions
section
Click on USB console on the Router and USB port on the Laptop [USB0 used here]. Click on Laptop

Follow the same steps as above in 1. to navigate to Desktop -> Command Line. Rest of the steps are identical as well.
