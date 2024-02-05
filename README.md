<h1>Active Directory Home Lab</h1>


<h2>Description</h2>
In this home lab, I will demonstrate how to create an Active Directory Home Lab using Orable Virtualbox and add 1000 users with Powershell.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Diskpart</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

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


