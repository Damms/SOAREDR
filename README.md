# SOAREDR

# SOAR EDR Project
This project is based on the resources provided by [MyDFIR@](https://www.mydfir.com/)

## Objective
In this project I will grow my cybersecurity skill set by integrating SOAR and EDR to automate security workflows

![image](https://github.com/user-attachments/assets/60f03015-0484-440f-8699-e96d7f6717e4)

### Skills Learned

- Writing security stories
- Writing detection rules
- Integrating EDR to SOAR platform
- Creating automated security workflows

### Tools Used

- LimaCharlie (EDR)
- Tines (SOAR)
- Slack
- Virtual Machines (VMWare Workstation)
- [Lazagne](https://github.com/AlessandroZ/LaZagne)

### Prerequisites 
- Ability to create virtual machine or spin up server in the cloud to download EDR agent onto and perform emulated attacks on to generate security events.


## Steps

### Step 1 - Create LimaCharlie account and organiztion space

[LimaCharlie](https://limacharlie.io/)

### Step 2 - Spin Up Windows Server

The first step is to spin up a windows server to download the EDR agent onto and also to emulate attacks to generate security events. Spin up a virtual machine if your computer can handle the resource usage, otherwise you can use any cloud provider to spin up a window server.

From previous projects I already have a Windows Server VM created so I will utilize that.


### Step 3 - Install LimaCharlie agent on server

On you windows server navigate to LimaCharlie and download the installer. https://docs.limacharlie.io/docs/windows-agent-installation

Open powershell navigate to the installer and install via the below command

hcp_win_x64_release_<sensor_version>.msi -i <installation_key>

You can get the installation key from the LimaCharlie 

![image](https://github.com/user-attachments/assets/ffe96147-067b-4742-bfae-e1ac58b3ac77)

Install agent on server
![image](https://github.com/user-attachments/assets/20d1184c-1976-4541-aa11-eccd9f2dfab2)

agent showing as sensor in LimaCharlie
![image](https://github.com/user-attachments/assets/fe5da546-22d0-45eb-addc-3cf88159b503)

### Step 4 - Download Lazagne to emulate attacks

Download Lazagne using the github link below, Lazagne will be used to perform password harvesting attacks on our local computer to generate security eventts.

[Lazagne Github](https://github.com/AlessandroZ/LaZagne)

Lazagne
![image](https://github.com/user-attachments/assets/949d6625-43ae-475a-ae59-3296b74a86b3)

Events
![image](https://github.com/user-attachments/assets/9655ce1c-0072-42b7-87e9-ed21b3a97d79)

Create D&R Rule
![image](https://github.com/user-attachments/assets/f8a10531-0bdf-44af-88e4-32fe3c309a9d)

Test D&R Rule
![image](https://github.com/user-attachments/assets/2a9620d7-938a-42d3-a9be-f2512683cd6a)

D&R Detection
![image](https://github.com/user-attachments/assets/e90d9c8c-6513-42c6-9eb6-394411e533b9)

Create Output to Tines Webhook
![image](https://github.com/user-attachments/assets/7208556a-a179-4fa4-8863-e751b5529254)

Check detection events coming through to Tines
![image](https://github.com/user-attachments/assets/445b4780-8f57-4ace-a617-a2db92ec39d9)

Create connection to Slack
![image](https://github.com/user-attachments/assets/7522caa9-588d-4cc6-9335-391e8b241f63)

![image](https://github.com/user-attachments/assets/59c6a410-1971-43ff-b417-6e1b71ab0f4f)

Test connection to Slack
![image](https://github.com/user-attachments/assets/d81d9189-8688-4f66-9ac0-84a194955242)

Open events in Tines to get name of fields we want to include in message
![image](https://github.com/user-attachments/assets/d34c0e48-4ed7-4db2-a806-3e051bfcc6a6)

Add details to message
![image](https://github.com/user-attachments/assets/b2f040f9-7f93-4136-b824-638453efac5e)

Test Slack message with Details
![image](https://github.com/user-attachments/assets/496bdbca-8ff1-4cd6-a5e7-4fe72a8952ef)

Setup Trigger if User prompt selects dont isolate which will trigger a slack message
![image](https://github.com/user-attachments/assets/0cec6d78-3fde-494b-a47f-61cfef24ac91)

![image](https://github.com/user-attachments/assets/643c72c1-d9c2-4fd4-9788-5fb860caeef3)

Create API request to isolate computer in LimaCharlie using sensor id - you must also create a Credential in Tines using LimaCharlie API Key
![image](https://github.com/user-attachments/assets/3e4cc0ea-1aad-47a3-a744-1632c8d7aef3)


Re-emit user prompt and check API is Isolating endpoint
![image](https://github.com/user-attachments/assets/28bcda53-437b-44ad-917f-15c482a0b59a)

![image](https://github.com/user-attachments/assets/f9a15fe5-6370-426c-a2aa-c1bf8b399871)



Now it has isolated go into machine and try ping to validate machine is isolated
![image](https://github.com/user-attachments/assets/44765354-76a8-4318-837c-ddc1eeb42254)



