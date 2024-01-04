# 🌐 Network Security Groups and Application Security Groups
In this walkthrough, we'll set up a virtual networking infrastructure and deploy virtual machines to test the network filters. 🖥️ 

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/12516c9a-a732-48d9-a45d-3351c560ed19)


## Task 1: 🛠️ Create a Virtual Networking Infrastructure
1. Sign into https://portal.azure.com 🌍
2. In the search bar, type "Virtual Network" and hit enter. 🔍
3. On the **Virtual Network blade**, click + Create 🆕

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/30e686e7-28d3-487d-b545-7a8a690268b6)

4.	On this page, specify the following settings and leave the others with their default values. 
   -	Subscription: The name of the subscription you are using
   -	Resource group: click create new and name accordingly 
   -    Name: myVirtualNetwork
   -    Region: East US 
5.	Click on the **IP Addresses** tab and set the IPv4 space to **10.0.0.0/16** and if needed in the Subnet name column, click **Default**, on the Edit Subnet blade, specify the following settings and click Save.💾

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/d133b50d-ea67-48b1-b5db-149773a2655a)


6.	On the **Review + Create** tab, click on Create. Wait for the template to be deployed.⏳

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/fb7018bd-f4ac-4884-9b26-77e65181bb58)


## Task 2: 🛡️ Create Application Security Groups

1.	In the search bar, type "Application security groups" and press the enter. 🔍
2.	Click on the + Create button and on the basics tab, specify the following settings:
- Resource Group: use the same resource group you created in the previous task
- Name: myAsgWebServer
- Region: East US 📍

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/82ccb95b-b547-47c4-a7f4-91542ea80b56)

3.	Click on **Review + Create** and wait for the validation to pass. Then click create.✅
4.	Navigate back to the **Application Security Group** and create another Security Group by clicking on the + Create button 🆕
5.	Specify the following settings:
- Resource Group: use the same resource group you created in the previous task
- Name: myAsgMgmtServer
- Region: East US 📍
6.	Click on **Review + Create** and wait for the validation to pass. Then click create.✅ 
7.	You should now see two application security groups.👀

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/97319582-8c9f-4340-86f4-46ddd56eda6c)


## Task 3: 🚦 Create a Network Security Group and Associate the NSG to the Subnet
1.	In the search bar, type **Network Security Group** and click enter.🔍 
2.	Create a new NSG and specify the following settings: 
- Subscription: the name of the subscription you want to use📝
- Resource Group: use the same resource group you created in the previous task
- Name: myNsg
- Region: East US 📍
3.	Click on **Review + Create** and wait for the validation to pass. Then click create.✅
4.	Go back into your Network Security Group by clicking on **“myNsg”**
5.	Under Settings in the left navigation panel, click on **Subnets** 

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/55381767-d69c-4bd8-8e03-03577629c36f)


6.	Click on + Associate and specify the following settings: 
- Virtual Network: myVirtualNetwork
- 	Subnet: default
7.	Click on **OK.**

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/03d0d7b4-f151-47f4-824f-c83faba1782a)


## Task 4: 🛡️Create inbound NSG security rules to all traffic to web servers and RDP to the servers.
1.	On the **myNsg** blade, click on **inbound security rules.**👆
2.	Review the default inbound security rules and click + Add

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/69598f0f-93fb-4c4f-9ee1-a79333637797)


3.	Specify the following settings to allow TCP ports 80 and 443 to the myAsgWebServers application security group and leave all other values with their default values. 

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/c7e2ca45-dd15-4806-8b8f-d7095e1acccd)


4.	Click on + Add to create the new inbound rule. Now we are going to create another inbound security rule.🚧
5.	Click on + Add and specify the following settings to allow the RDP port (TCP 3389) to the myAsgMgmtServers application security group and leave all other values with their default values. 

![image](https://github.com/asessomsblm/WalkThroughs/assets/152536988/c8f377b7-e9b8-4745-8d39-18a03b0e93c2)


6.	Click on add to create the new inbound rule. 

**Summary**: You've successfully deployed a virtual network, network security with inbound security rules, and two application security groups. Great job! 🎉
