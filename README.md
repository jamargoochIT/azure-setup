<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in Azure</h1>
This tutorial goes through the the creation and configuration of Virtual Machines in Azure.<br /><br><br><br><br>


We’re going to create a Domain Controller and a Client and then ensure the two are can communicate with one another.

Before we get started, I wanted to briefly state what a domain controller is and some of what it can do:<br>

- A domain controller is a server on a network that performs several functions:
- Authentication – Verifying user’s credentials who are trying to access the network.
- Authorization - Who can use what based off their permissions.
- Group Policy – Configuration of settings for users and computers.
- Active Directory – Database of all users, computers, and resources in the network.<br>


All right, now that we know that, off we go!<br>
First up, we’ll need to create a resource group.
![1](https://github.com/user-attachments/assets/9f998dbc-aeec-46ce-92db-fa8ee04ec50a)<br><br><br><br>




We’ll set up a resource group by filling out the necessary fields:<br>
- The resource group name – can be whatever you want.
- Region – I chose US East 2
![2](https://github.com/user-attachments/assets/23e44b4f-51e4-4248-837c-00652e954acc)<br><br><br><br>



Click Review and Create at the bottom of the page to continue to validation.
![3](https://github.com/user-attachments/assets/aa578283-e130-49ff-8e99-da77ce5ebf85)<br>
Click create at the bottom of the screen.<br><br><br><br>

 


Voila, our resource group has been created.
![4](https://github.com/user-attachments/assets/64442ee0-eee9-4f69-b32c-e0dd695fa6d4)<br><br><br><br>



Now, we’ll create a Virtual Network. Type Virtual Networks into the search bar within Azure and then click create.
![5](https://github.com/user-attachments/assets/58e53d96-fd95-4dbd-a973-ebfdb3d2add0)
![6](https://github.com/user-attachments/assets/2e50759f-48eb-4f70-944e-119532142796)<br><br><br><br>



We’ll want to fill in the necessary fields here, pay close attention to the resource group and region. We want the resource group to be the one we just made; in my case it was vm-lab-test. We want the region to be exactly the same as what we selected for our resource group. 
We can name the network what we want, so I’ll name it vm-network.
![7](https://github.com/user-attachments/assets/adb71e23-425c-487b-8b67-df35d858732f)
When we’re done, we’ll click the blue button at the bottom that says review + create and on the following screen review the information one last time and then click the blue button at the bottom labeled create.<br><br><br><br>


Azure should be creating your virtual Network now.
![8](https://github.com/user-attachments/assets/dbf5c423-9f04-40b2-a326-dc8702616ba1)<br><br><br><br>



When that’s done, lets type virtual machine into the Azure search bar and then click create, then select the first option: Azure Virtual Machine.
![9](https://github.com/user-attachments/assets/ee2f296a-e83d-4e8e-8750-8740083cd073)
![10](https://github.com/user-attachments/assets/4bda0237-74f1-4cec-baed-f75aa24a270b)
![11](https://github.com/user-attachments/assets/48783d1d-3c8c-493a-9758-aac897bb9703)<br><br><br><br>


 



Here, we’re going to setup the Domain Controller. Here are the necessary fields we need to fill out:<br>

- Resource Group – make sure this is the same resource group we created.
- Virtual Machine Name – You can name it whatever you want but we’ll use DC-1.
- Region – Make sure it’s the same as what we selected for our resource group and virtual network.
- Image – We’ll want to select Windows Server 2022 Datacenter: Azure Edition – x64 Gen2
![12](https://github.com/user-attachments/assets/07779d71-e5de-4976-9fb5-2a56f7203171)<br><br><br>



Scroll down to the next section to the next fields we need to fill out:<br>
 
- Size – Here, we’ll choose Standard_E2s_v3 – 2 vcpus, 16GiB memory. This is basically going to affect the speed of the Virtual machine, having 2 virtual cpus with 16 Gigabytes of memory will be fine for what we’re going to need it for.
- Username – You can type what you want here and for the passwords. 
- Password
- Confirm Password<br>

Now that we’re all done, let’s click the button at the bottom labeled Next: Disks > to proceed.
![13](https://github.com/user-attachments/assets/f14ed3f6-6087-4770-b357-df7f68117b9f)<br><br><br><br>


 

We don’t need to change or fill in anything on this page, what we’re looking for is on the next page. So, we’ll click the button bellow labeled Next: Networking >

![14](https://github.com/user-attachments/assets/a6e520cd-1816-4a81-95e8-5aa7c6557654)<br><br><br><br>

 

On this page we want to make sure that the Virtual Network is set to the same one we created. In my case it was vm-network.
![15](https://github.com/user-attachments/assets/17e61a85-b2cb-4679-b0a9-9d92dace7ad1)<br><br><br><br>



Once we’ve checked that, we’ll click the blue button at the bottom labeled Review + create. On the next page Azure will begin the validation process once, it’s completed press the blue button at the bottom labeled create.
![16](https://github.com/user-attachments/assets/a9ff2801-477a-48c2-a10b-407909cb7934)<br><br><br><br>



Then Azure will start creating the Virtual Machine. Once that’s done, we’ll click on, create another Virtual Machine.

![17](https://github.com/user-attachments/assets/3729887e-6cc2-46a6-a17c-5891e488dfd1)<br><br><br><br>



Now we’re going to create the client virtual machine. This process is going to be similar to creating the domain controller. The fields we’ll need to fill out are:<br>

- Resource Group – make sure this is the same resource group we created.
- Virtual Machine Name – You can name it whatever you want but we’ll use client-1.
- Region – Make sure it’s the same as what we selected for our resource group, virtual network, and domain control.
- Image – Windows 10 Pro, version 22H2 – x64 Gen2

![18](https://github.com/user-attachments/assets/82e6bf9b-56ca-4985-9d75-ed92f1be7b8c)<br><br><br><br>




Now we’ll scroll down to the next section to the next fields we need to fill which are same as last time:<br> 

- Size – Here, we’ll choose Standard_E2s_v3 – 2 vcpus, 16GiB memory. This is basically going to affect the speed of the Virtual machine, having 2 virtual CPUs with 16 Gigabytes of memory will be fine for what we’re going to need it for.
- Username – You can type what you want here and for the passwords. 
- Password
- Confirm Password
![19](https://github.com/user-attachments/assets/ce47e26d-4462-4dea-a1b1-52298840722d)<br><br><br><br>





We have one additional step; we need to click the box that says:
![20](https://github.com/user-attachments/assets/371b1b11-4af4-4db0-9ebc-1aff4c7a3c3b)<br><br><br><br>


When we’ve done that, we’ll click Next: Disks ><br>

Again, we’re going to skip this page because what we’re looking for is on the next page. Click Next: Networking ><br>

On the networking page, we’re looking to make sure that the Virtual Network is set to the same one we created. In my case it was vm-network.

![21](https://github.com/user-attachments/assets/f3d5f076-5f5b-4af8-a6dc-033fb7fe9e80)<br><br><br><br>


Once we’ve done that, the process is the same as the domain controller: We’ll click the blue button at the bottom labeled Review + create. On the next page Azure will begin the validation process once, it’s completed press the blue button at the bottom labeled create.<br><br><br>

**Quick Tip** -- <br>
If you get this error message:<br>
![22](https://github.com/user-attachments/assets/efb02529-73ae-42ee-9e56-0c61fffe77aa)<br><br><br><br>


What we’ll need to do is go back to the basics tab (we can click on the basics tab that’s highlighted in the image above) and click the box that says:<br>
![20](https://github.com/user-attachments/assets/ae06a294-f872-41a9-b413-ac1b390419a1)<br><br><br><br>
 

If it’s already checked, uncheck it and check it again.<br>
Once, we’ve done that, we can simply press review + create.<br>

**Quick Tip Over** ----<br><br><br>

Next up, we’ll want to set the DCs (Domain Controller) private IP address to static.<br>
We’re going to do this because A static IP address for the Domain Controller ensures its address never changes, so our network can always easily find it. This helps avoid problems with connecting to it or using services that rely on it, such as DNS. It also makes troubleshooting simpler if any issues come up.<br>

Okay, now we’ll go to the Virtual Machines page.
![23](https://github.com/user-attachments/assets/f620db72-0afa-4d50-9e88-534107282a61)<br><br><br><br>


Click on DC-1 virtual machine.
![24](https://github.com/user-attachments/assets/f16dce94-6826-4135-91cb-44c42103c002)<br><br><br><br>


In the menu to the right, click Network -> Network settings.
![25](https://github.com/user-attachments/assets/3f615abc-5984-409e-acb7-a0e313c18e82)<br><br><br><br>

Click the network interface/IP configuration which is the virtual – NIC (Network interface card).
![26](https://github.com/user-attachments/assets/2415aab3-be73-4a24-aa69-e4107cdeef55)<br><br><br><br>
 

Click on ipconfig1
![27](https://github.com/user-attachments/assets/f9c4792a-902c-44e1-9c1d-d50d25505162)<br><br><br><br>


In the menu that pops out on the right, under Private IP address settings, change the private IP address from dynamic to static. Then click save.
![28](https://github.com/user-attachments/assets/1617913a-897f-43a8-a142-bfae21797be2)<br><br><br><br>



Now, we’ll want to take note of the public IP address and the private IP address – we’ll use the private IP address later.
![29](https://github.com/user-attachments/assets/ba306d12-edc7-479e-8c87-21cf1494e7f0)<br><br><br><br>


Up next, we’re going to set Client-1’s DNS settings to DC’s private IP address.<br><br>
The reason we want to connect Client-1 (and other clients if we had a bigger network) to the Domain controller is so the domain services we configured would be applied to Client-1 as opposed to the settings on the virtual network’s DNS server which has no idea about what we configured on our DC. Configurations such as how many DCs we have (In this case, it’s just the one DC. You can have more than one in a single domain, but there can only be one primary DC.) and their configurations.
This will enable us to join the domain later, when we create one for DC-1.
Also, while it might seem convenient to use the Virtual Network DNS server instead or creating a VM, this isn’t typically done because a VNDNS is not designed to perform the functions of a domain controller.<br>

On the virtual machines page, click on Client-1.
![39](https://github.com/user-attachments/assets/1d5b2702-9c8e-4176-9a39-3a5752165308)<br><br><br><br>


In the menu that opens, click Networking -> Network Settings -> The Virtual Network Interface Card.
![40](https://github.com/user-attachments/assets/0c510459-2c19-4248-b078-0905c14b453d)<br><br><br><br>


Settings -> DNS Severs -> Under DNS Servers<br>
By default, client -1 will be using the V-net’s DNS server but we’re going to select custom and type in the private IP address of DC-1.
![41](https://github.com/user-attachments/assets/78582ce7-3a1f-41dd-b99d-e337b6e8e47f)<br><br><br><br>


Then click save.<br>


![42](https://github.com/user-attachments/assets/77e62a70-902a-43f6-97b4-ad2d98a63bb5)<br><br><br><br>


Go back to the main Virtual Machines page, select the box next to Client-1 and then click on restart so the settings we configured can be applied. 
![45](https://github.com/user-attachments/assets/407fc21f-a5f7-4e7a-9fde-4f9dad6e9d29)<br><br><br><br>



After Client-1 finishes restarting, we’re going to log into DC-1 so we can disable the firewalls. Open remote desktop and type in the Public IP address for DC-1 and use the credentials you created for DC-1 and log in.<br><br> 

**Quick Tip** --<br><br><br>
If you forget your username or password, go to the virtual machines main page and click on the virtual machine who’s credentials you’ve forgotten, in this case let’s say it’s DC-1.
![30](https://github.com/user-attachments/assets/897fd676-30e2-4cd5-b0ad-482e6ad45793)<br><br><br><br>



A menu will pop up on the right, select Help, then reset password.
![31](https://github.com/user-attachments/assets/fc347e32-1109-4b46-88bc-8bceca2983e8)<br><br><br><br>



Here you’ll be shown your username and you’ll be able to enter a new password.
![32](https://github.com/user-attachments/assets/f8410c4a-ed3e-4872-b375-92533fc650a3)<br><br><br><br>


When you’re done, click the blue update button at the bottom, give it a few seconds after it updates and try to log in.<br><br>

**Quick Tip Over** ----<br><br><br>


Once we’ve logged in, we’re going to disable the Firewall to enable our client to communicate with our domain controller.<br>
So, in the Windows search bar type run, in the run app type wf.msc.<br>
![33](https://github.com/user-attachments/assets/b2fafd3a-2925-4bbf-ab7b-c7fb8e87091c)<br>
![34](https://github.com/user-attachments/assets/4d453ce5-ff2d-4f41-953e-ee48ef2698cd)<br>
Press OK.<br><br><br><br>


When the Windows Defender Firewall with Advanced Security window opens up, we’ll click on Windows Defender Firewall Properties.

![35](https://github.com/user-attachments/assets/7fc38b3a-77d5-4d4e-ba83-a42930a7ea09)<br><br><br><br>


We’ll right click on Windows Defender Firewall with Advanced Security on Local Computer and go to properties.

![36](https://github.com/user-attachments/assets/d2d53dbc-9c51-4498-92de-9641ddab6b0e)<br><br><br><br>



In the properties window that opened up to Domain Profile, where it says Firewall state, we’re going to change it from on to off.
![37](https://github.com/user-attachments/assets/7bfb9195-852e-487a-930d-abd8327f080b)<br><br><br><br>


We’ll want to do this for the next two tabs as well, Private Profile, and Public Profile.

![38](https://github.com/user-attachments/assets/edc1e2cd-aaf8-4df1-9fa7-37f9cc9d6fbf)<br><br><br><br>


When we’re done, we’ll click apply then okay.<br>

Next, we’re going attempt to ping DC-1 to ensure that we can communicate with it. Again, this will be important later when we create a domain for DC-1 and try to join it.<br>
- We’ll log into client-1 using remote desktop. 
- Select no for all the options that are in the menu you’re presented with.
- Once we’ve logged in, we’ll go to the Windows search bar and type in PowerShell and open the Windows PowerShell app.
- We’re going to ping DC-1 to make sure it’s accepting traffic from Client-1.
- In PowerShell, type Ping and the private IP address of DC-1 which in my case is 10.0.0.4.

![43](https://github.com/user-attachments/assets/dbf4c88d-adf5-489e-b32a-c739c91410b8)<br><br><br><br>



Press enter and we should get a reply back.
![44](https://github.com/user-attachments/assets/782cd6be-2813-495f-82b0-b46281d33186)<br><br><br><br>



To ensure that the DNS Server is in fact set to DC-1’s private IP address, in PowerShell you can type ipconfig/all and near the bottom where it says DNS Server it should display DC-1’s private IP address, in my case, it’s 10.0.0.4.

![46](https://github.com/user-attachments/assets/e004d017-eb2a-4b5a-a279-ea254683b2eb)<br><br><br><br>



If it isn’t displaying DC-1’s private IP address, a mistake has been made, maybe Client-1 wasn’t restarted after we customized the IP address to point at DC-1’s private IP address? If that’s the case, restarting the Client-1 will resolve the issue.
![45](https://github.com/user-attachments/assets/87c0a9d3-c379-4b7f-82c2-d38a974b1fc7)<br><br>





And we’ve finished setting up our Virtual Machines DC-1 and Client-1 in Azure.









