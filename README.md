 <h1>Active Directory Home Lab</h1>

<h2>Description</h2>
In this home lab, I will demonstrate how to create an Active Directory Home Lab using Orable Virtualbox and add 1000 users with Powershell.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Diskpart</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> 

<h2>Architecture walk-through:</h2>

<p align="center">

 
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/e5dc0805-82b4-4b61-afce-0c53ad401f24)

<br />
<br />


<h2>Program walk-through:</h2>

<p align="center">
I’m using Oracle VirtualBox to create the virtual environment, as well as Windows 10 ISO and a Server 2019 ISO to install the two operating systems on two separate virtual machines. <br/>
 
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/92ed38c0-8199-4928-abe8-9f9e83de9750)

</br></br>

![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/39ee9777-5ae5-4476-955c-775f6bbb6778)

</br></br>

![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/e934585a-2aca-4c82-b533-1422d81d3c92)

After I downloaded and installed everything, I created my first virtual machine, which is going to be the domain controller that will house Active Directory. 

![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/aaf97988-7cf1-40d9-a42f-b6a91fa8312c)

</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/67c564bb-3abd-422b-9865-18826cc19762)

</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/b5294bf6-fbbe-412e-9303-463c79d5f29a)

</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/86d8cfd2-9f47-4c78-a281-8f3e06c12614)

<br />
<br />

I’m going to give this virtual machine two network adapters, one is going to be used to connect to the outside Internet and the other one that's going to be used to connect to the Virtual Box thereby creating a private network that the clients are going to connect to. 
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/b8a3eeb0-11a3-4475-8cec-43adafef9a84)
</br></br>

![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/618cd873-1cdf-42f5-8940-1a22676cabac)
</br></br>

![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/6d15089a-2af7-44de-aeb1-666bba1de573)
</br>

![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/afcf1b96-7bbe-4ad4-ab59-ffa332547b01)

</br></br>
I selected the desktop experience to make the process easy to follow:
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/7f1ea876-4b9b-428b-bea3-c2f6a277d011)
</br></br>
Accept all the license agreements
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/e73d7f2d-6100-4d78-9439-1b7531b84397)
</br></br>
I selected the Custom Install as I wanted to choose what I wanted
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/7cfb6488-590d-463d-b482-0b5e27f7c141)
</br></br>

Once I have installed the software I can login to my server
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/ba5273cf-d9c2-4c3b-8312-59508e6c96c0)
</br></br>
The first thing I will do is set up the network configuration inline with my archicture diagram here:
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/feb59ff3-10c3-470c-a34e-ff45c4dc9791)
</br></br>
I visit my networks settings inside the DC machine to start making changes
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/996de5f5-ad9d-4f23-84a6-019819f51af9)
</br></br>
There should be two network adapters (according to the vm settings I updated earlier)
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/692d0326-c2ea-4417-a2f9-f9c6948ec940)
</br></br>

I right click on each adapter and check the Status of each - one of the IPV4 is reflective of my internet address - so that's the adapter linked to the internet.
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/8e715361-18ac-423d-a825-323c78a067d1)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/6fbe7880-6ed8-4a2a-b35f-4af31349561b)
</br></br>
I check the other one for completeness and it's not connected to the internet. It has an ip address that was automatically assigned by the VM - so I rename in to Intranet.
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/0e8109a5-a902-49a6-aeb2-3ed39e75f0d0)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/0f4a1e78-6b50-4ee5-a27e-944d3c1a1abf)

</br></br>
To make my PC easy to find I will rename it to DC (it currently has a long weird name)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/06cf14e0-b2d5-4a29-914b-0af5a55064f7)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/0fb9df7f-2175-44cd-9f8d-d8be153f6400)
</br></br>
So  now that I have setup the internal NIC and the external NIC I will set the IP address as per my architecture diagram:
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/f69f2ebd-1f83-4270-b614-47ff0671fec1)
</br></br>
I will not be adding a default gateway as the domain controller will serve as the gateway. And after I install Active Directory, AD will install DNS, so the server will use itself as the DNS. So for the server, I just enter the loopback ip address that points to itself
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/02fd82e8-92d2-4f17-a38e-638a349da70b)
</br></br>
Now that the two NICS have been set up with the ip addresses, I can install Active Directory services and create a domain.
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/59b07348-9f43-41e8-ada5-96af78233ea1)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/ee3e5b5c-b9ab-49f9-afd9-f4e9366cd90b)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/92890e5f-96a9-4af1-9b7f-157ae538c046)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/b88ab55f-7a04-42c0-af2e-6221cd67bc56)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/5c4ce57f-10aa-45ca-bc35-6db0f9bec106)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/defb4f46-55ba-40b3-aceb-965304562c26)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/4b0aff93-83ca-44af-b26e-513977f7ab99)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/32fe64f6-e57c-40c8-aedf-a2e683842a9f)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/533d621c-d21c-4a5e-b51c-ca873dfc8afa)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/1cb0e581-9853-4f44-a972-d556cec8c78c)

</br></br>
Now that we have installed AD, I can promote this computer to the domain by adding a new forest and I'll name the new domain mydomain.com
</br></br>

![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/a826daae-cd4d-478d-9aaa-23ea0c22b774)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/8af858f7-2414-4c01-a264-27b5906d5fa2)

</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/1a5da1a7-2ad8-48e1-8c46-8e6772328134)

</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/fb7d412d-80ca-4daf-8dea-6c22b0c1d687)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/5156c15f-fd96-455e-bab9-567f7f2ddfae)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/ae1cb47e-a503-4b21-b364-565671fae204)
</br></br>
Now when I login I can see mydomain
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/9eccb936-adb9-431a-8617-2ec5d38af38e)
</br></br>
Now I will  setup my own admin account on the newly created domain instead of using the systems default account
</br></br>
I will  start by creating an organisational unit where my admin account will reside
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/028c6394-73c2-434e-a92c-e249a8199850)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/367cb104-64c8-4b02-a5cb-5942bf71568c)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/69535ed8-f816-4b2e-893b-8b456e5b13bb)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/724ddad5-a355-4a37-9238-ba0eebdde3d5)
</br></br>
Then I will create  an admin user inside the ADMIN organisation  unit
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/7c4be1fc-1503-4c79-b5b2-809fdd977903)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/6abb970e-0ee7-49aa-a9d8-9a5c6de0cce5)
</br></br>
Then once my user is created, I will update it's properties to ensure it's a member of the organisational unit
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/36b26828-3a9a-4229-a5e9-c55f6d9aebf6)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/0feac841-be82-4ea7-8a55-202a3f63e452)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/2f2ed718-4679-45b5-963f-e539b0d9f7e7)
</br>
Now that I've created my own admin account, I logout of the default account and log back into my  domain using my own admin account
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/1c544930-140c-4e7e-887e-32988e066b90)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/f032b7f1-1f1c-4558-a053-7ff9f6a1ee11)

</br></br>
Now that I've logged into my admin account, the next step is to install the Remote Access Server and the Network Address Translator
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/9849edc6-bbe4-4c85-9025-ec1761e4951d)
</br></br>
The purpose of this is to allow the Windows 10 Client (that I haven't created yet) to be on the virtual network but still be able to access the internet  through the domain controller. So I will install the RAD and NAT on the domain controller.
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/fd4796a3-9f19-4a4d-9928-a8f88777bd93)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/c4b942bb-0b7a-4566-8af0-59f38b3dd970)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/dc0be657-ea82-413f-b640-a6f429d3d402)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/021f16f4-99c9-4759-a156-06b3e2d00972)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/38ace432-0492-4117-9055-bc3cd0b216a9)
</br></br>
Now I can setup the Routing and Remote access and the NAT
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/e942fdac-78f2-4518-8d75-b1aa81ccb3a9)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/733367af-cb26-458a-8027-c6da8162e3a3)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/83bd71fa-3728-4f90-8f3e-8e8bd5322f0f)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/001bbcfd-eeb1-471b-a2fb-6c5c45bf3436)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/87993b04-f823-470e-8f8d-b42f60f86e55)
</br></br>
From here I select the externally facing NIC (which I labelled as "Internet" earlier)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/faa27d06-5d6d-440c-a5a4-db03c3613c47)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/22fda133-3579-4227-b643-f1dd4c8ff219)
</br>
Now I can see that my remote access server has been correctly configured and if we install a Windows 10 client it should be able to get to the internet
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/d82ee13b-ab8c-47f9-934f-27a0e1f08ebc)
</br></br>
Now I will set up a DHCP server on the domain controller which will allow the Windows 10 clients to get an IP address to browse the internet even though they are on the private network (just like any corporate network).
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/c724130c-942f-42f7-a2ff-db2af802327b)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/6d6078e7-e155-4192-9427-4dfc40b70bb2)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/54de2021-7a49-495c-aa84-96d7b319e345)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/7b83d56a-1dfe-448e-ba2a-64060c8edcb6)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/2ebce9bc-f814-40cb-8f26-3d5037e6746a)
</br></br>
Now the DHCP role has completed installing I can go to the DHCP to setup the scope
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/a1e97d18-e6d4-4ef4-9d6f-cdc0bf166113)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/3d34fbae-48ea-4e0e-9d58-35a604a5a20b)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/9efed0d1-57d3-45f3-b9c8-f1c8e6ab972e)
</br>
This is the scope that I have defined in my architecture diagram, and I will implement it here
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/4d6d9050-78ed-4f60-892c-f6a345d537c1)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/744aa2aa-e1b5-4a6d-91dc-defbd8ccd0bd)
</br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/5c14d753-8806-44ed-8c1d-3a149f933a7b)
</br></br>
I will just set the IP lease to be 8 hours (it soesn't really matter since this is a lab environment)
</br></br>
![image](https://github.com/nobudlamini/ActiveDirectoryLab/assets/150668386/39521433-bc78-443c-8454-a871ed5f00c2)
</br></br>
I will setup the DHCP options here










