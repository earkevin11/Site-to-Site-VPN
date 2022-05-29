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


# Configure the routing service on the simulated company setup
- Scroll to the right hand corner and open the getting started wizard 
- Select deploy VPN only > right click on companyvm > configure and enable routing and remote access > custom configuration > demand-dial connection and LAN routing 
- Start the service

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170848916-b65520f6-0bb9-4cd1-ae5d-c0acffc59f79.png" height="80%" width="80%" alt="review of vnets and VMs"/>

<p/>

- Click on Network Interface 
- Right click and create a new demand-dial interface > call it Azure > select IKE2 

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170848916-b65520f6-0bb9-4cd1-ae5d-c0acffc59f79.png" height="80%" width="80%" alt="review of vnets and VMs"/>

<p/>

- User will be prompted to give a IP address > add the public IP address of the virtual network gateway created

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170849324-0c652b88-2847-49a7-9293-a352c56af6a9.png" height="80%" width="80%" alt="review of vnets and VMs"/>

<p/>

# Now admins must give information about the azure side similar to how we input all of the companyvm info into the local gateway
- Admins must add routing details
- Refer to udemy video #113
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170849443-b841e703-7829-4948-981e-5a6afe70b5ee.png" height="80%" width="80%" alt="review of vnets and VMs"/>

<p/>

- Take the address space of the virtual network created for point-to-site vm, which is 10.0.0.0/16
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170849404-339918a0-b96e-46cd-9e8b-35770025a3cf.png" height="80%" width="80%" alt="review of vnets and VMs"/>

<p/>

# Right click on the Azure NIC created and click on properties > security > preshare key for authentication and enter abc123 (key that you created)
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170849467-a28fb91f-617e-48c1-a568-e4ac784abdf5.png" height="80%" width="80%" alt="review of vnets and VMs"/>

<p/>
- See that it is now connected
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170849474-04a45047-f7f3-4561-b940-2df91302d9c2.png" height="80%" width="80%" alt="review of vnets and VMs"/>

<p/>

# Navigate within companyvm to the point-to-sitevm's private ip address
- 10.0.0.4/vpn%20connection%20point%20to%20site.html
- ^ Remember, this is the HTML page that you created
- There is a successful site-to-site connection once users can reach the private IP webpage

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170849510-003e4e84-27ae-4c2a-af76-aa9417fd219d.png" height="80%" width="80%" alt="review of vnets and VMs"/>

<p/>

# Admins can also set up a peering connection where between two virtual networks and an on-prem site companyvm can still access it
- See the two virtual networks that have a peering connection
- Companyvm can access resources from both virtual networks
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/170850443-73be77a6-484b-459a-9061-d66de80bdbbf.png" height="150%" width="150%" alt="review of vnets and VMs"/>

<p/>



