# Cisco Packet Tracer FTP Server

A Virtual Server that implements File Transfer Protocol.

FTP is a protocol used to transfer (send and receive) files. It is a Layer 7 Application of the Open Systems Interconnection (OSI) Model.

## Table of Content

- [Features](#features)
- [How to Run](#how-to-run)
  - [Uploading Stage](#uploading-stage)
  - [Downloading Stage](#downloading-stage)
- [Configurations](#configurations)
  - [ISR4331 Router Configuration](#isr4331-router-configuration)
  - [PC-PT PC1 Configuration](#pc-pt-pc1-configuration)
  - [PC-PT PC2 Configuration](#pc-pt-pc2-configuration)
  - [Server PT Server 1 Configuration](#server-pt-server-1-configuration)

## Features

- Upload files to the FTP Server.
- Download files from the FTP Server.
- Access to Read, Write, Delete, Rename and List (RWDNL) rights/privileges when you log into the server.

## How to Run

- Open **FTP-Server.pkt** file in Cisco Packet Tracer.
- Select PC1 to display its interface.
- Goto the Desktop Tab and run the Text Editor app.
- Type any custom message in the Text Editor.
- Close the Text Editor to save your text document.
- Click Save in the pop-up window.
- Provide a filename with the filename extension. (eg: **hello.txt**) and click **ok** to save.
- Open Command Prompt in Packet Tracer.
- Ping the FTP Server by typing the command below and hit the ***Enter*** key on your keyboard:

```console
ping 10.10.10.2
```

- Repeat the step above if you receive a Request timed out message.
**NB. Ping command is used to check whether a host is up and running on a network.**
- Type: `ftp` (in command prompt and press ***enter*** to see the ftp command usage)
- Now type and hit ***Enter:***

```console
ftp 10.10.10.2
```

- Provide the username. **(Username is: cisco)** and hit ***Enter***
- Provide the password **(Password is: cisco)**

>NB. Password is not visible when entering/typing your password, press **enter** when done to login.

### Uploading Stage

- Type the `dir` command and press ***Enter*** to list all files on the FTP Server:

```console
dir
```

>You can confirm the **hello.txt** file created earlier is not in the list)

- We can now upload the text file to the FTP Server by typing the command below and press ***Enter:***

```console
put hello.txt
```

- Now type the `dir` command to see a list of all files:

```console
dir
```

>You'll find **hello.txt** file in the list of Server files.

### Downloading Stage

- Close PC1 Command Prompt and exit PC1 interface.
- Launch PC2.
- Goto Desktop and Launch Command Prompt.
- First let confirm that we don't have the hello.txt file on PC2.
- You can do that by typing the `dir` in command prompt and press ***Enter:***

```console
dir
```

- Connect to the FTP Server by typing the command below and press ***Enter:***

```console
ftp 10.10.10.2 
```

- Provide the username. **(Username is: cisco)** and press ***Enter***
- Provide the password **(Password is: cisco)**

>NB. Password is not visible when entering/typing your password, press **enter** when done to login.

- Download **hello.txt** file from the FTP Server by running the command:

```console
get hello.txt
```

- Exit the FTP Server by using the `quit` command and press ***Enter:***

```console
quit
```

- You can confirm the download by typing `dir` (in command prompt to list all your files in your directory):

```console
dir
```

- You should see the **hello.txt** file in your directory.

## Configurations

Below is the configuration for the FTP-Server.
I have already configured the FTP Server with these configurations so there's no need to do it again.

**This serves as a guide to those wanting to create similar projects from scratch.**

### ISR4331 Router Configuration

1. Click the Router to inspect it.
2. Select the config tab.
3. Under INTERFACE tab, select **GigabitEthernet0/0/0**
4. Make sure Port Status is on, Bandwidth and Duplex is set to auto.
5. In the IP Configuration section, provide an IP address: **10.10.10.1**
6. A Subnet Mask will be provided automatically by clicking the Subnet Mask field.
7. Select **GigabitEthernet0/0/1** below **GigabitEthernet0/0/0** in the INTERFACE tab.
8. Make sure Port Status is on, Bandwidth and Duplex is set to auto.
9. In the IP Configuration section, provide an IP address: **192.168.0.1**
10. A Subnet Mask will be provided automatically by clicking the Subnet Mask field
11. Exit the Router Interface to save changes.

### PC-PT PC1 Configuration

1. Click PC-PT PC1 icon to open its interface.
2. Goto the Desktop Tab and select IP Configuration.
3. Set the IP Address to: **192.168.0.2**
4. A Subnet Mask will be provided automatically by clicking the Subnet Mask field.
5. Configure the Default Gateway by specifying: **192.168.0.1** in the field.
6. Close the IP Configuration Window and exit PC1 interface to save changes made.

### PC-PT PC2 Configuration

1. Click PC-PT PC2 icon to open its interface.
2. Goto the Desktop Tab and select IP Configuration.
3. Set the IP Address to: **192.168.0.3**
4. A Subnet Mask will be provided automatically by clicking the Subnet Mask field.
5. Configure the Default Gateway by specifying: **192.168.0.1** in the field.
6. Close IP Configuration Window and exit PC2 interface to save changes made.

### Server PT Server 1 Configuration

1. Click the Server to open the Server's interface.
2. Goto the Desktop Tab and select IP Configuration.
3. Set the IP Address to: **10.10.10.2**
4. A Subnet Mask will be provided automatically by clicking the Subnet Mask field.
5. Configure the Default Gateway by specifying: **10.10.10.1** in the field.
6. Close IP Configuration Window to save changes made.
7. Goto to the config tab and rename Sever1 to FTP Server.
8. Move to the Services Tab and select **FTP** under SERVICES
9. You can setup a custom Username and Password or use the default settings.
10. Enable: Read, Write, Delete, Rename and List (RWDNL) options by checking their checkbox to get full access on the FTP Server.
