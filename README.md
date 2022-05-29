# Site-to-Site-VPN

# What is the purpose of a Site-to-Site VPN connection?
- Site-to-site VPN is used when you want to connect an large infrastructures like an entire on-premise data center to a virtual network

# Same as point-to-site, we will use a Virtual Network gateway 

# Continuation of Point-to-Site VPN connection demo
# Use Case: Simulate a company setup 
- Create a new VM that will act as the company on a new network
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170848216-9d0fe159-bddf-48a7-9654-a2d25c0b4c1b.png" height="50%" width="50%" alt="review of vnets and VMs"/>

<p/>

- On-Prem company setup will need a routing device that has public IP address
- Install Windows Server 2019 which will have the public IP address 
- Select "Remote Access" > Select DirectAccess and VPN and Routing > Install
- This will route traffic via the site-to-site VPN connection

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170848474-9426ae2c-c826-4fd9-9751-74b01004897a.png" height="90%" width="90%" alt="review of vnets and VMs"/>

<p/>

# Create a Local Network Gateway
- It will have information about the company setup and will be attached on the virtual network gateway
- It will understand the client's network details
- Add the public IP address of companyvm 
- Address space: is the private IP address space of companyvm

# Take the public IP of companyvm and use it as the IP address for the local network gateway
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170848674-33be7472-61f4-42a3-9150-5e51344b0e6e.png" height="90%" width="90%" alt="review of vnets and VMs"/>

<p/>


# Take the address space of companyvm and use it as the address space for the local network gateway
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170848702-996a8327-51a7-427f-9562-c68a768e913d.png" height="90%" width="90%" alt="review of vnets and VMs"/>

<p/>

# Local gateway now has all the info of the companyvm

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170848749-ce1b4848-b7a6-4294-a8bd-48591850b250.png" height="90%" width="90%" alt="review of vnets and VMs"/>

<p/>

# Create a site to site connection on the Virtual Network Gateway and link the local network gateway
- Navigate to the virtual network gateway > connections > add > select site-to-site connection and link the local network gateway that was created
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170848855-b1113d49-d50b-40dc-ae95-96b5ad51cca3.png" height="40%" width="40%" alt="review of vnets and VMs"/>

<p/>


