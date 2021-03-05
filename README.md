# 2020-FYP-Wi-Fi-Penetration-Test-Tool(writer:Ma Kam Wa)

To create a graphical user interface (GUI) that enable user to have a penetration test for the security level of the wireless router including optimized password cracking application to crack the encrypted password in a faster and easier way.Generate a report to the user after the penetration test and give suggestion of how to strengthen the security control of their wireless router’s configuration such as password strength, security level of the enabled Wi-Fi protocol (WPA&WPA2 Personal/Enterprise and WPA3 Personal). Both individual and organization is able to secure their wireless router after the test and protect their asset.

# detail of the Project
Hong Kong Institute of Vocational Education (Chai Wan)

Information and Network Security (IT114104) Final Year Project,Grade A

## Collaborators

Ma Kam Wa,Andy Main program,GUI design,WIFI connection and server tool,stress testing
Hui Chun Fung, Bosco,WiFi WPA/WPA2/WPA3 hacking
Lin Lok Hei, Alexcrack password

Supervisor: Dr. Lam Shu Chiu

# (there i would show the part i had done)

## Step

![image](https://user-images.githubusercontent.com/51657418/110147445-a3f42980-7e16-11eb-8ca2-7c425f7830be.png)

# Getting Started
Before running the program,please perpare the environment and hardware

# Set up environment

## Hardware

    1.computer
    2.one Wi-Fi adpter[for aircrack-ng]
    3.one Wi-Fi router [be attack target]
    4.end device[be attack target]
    5.a server with powerful gpu (Used : pc with GTX1080 x 4 )

## Software

    1.Kali-Linux OS [set up in VMware]
    2.Aircrack-ng (tried verison 1.5.2)
    3.hcxdumptool,hcxtools,hostapd-wpe[for WPA3 attack]
    ---3.1  Hcxdumptool:is a tool that can capture handshakes from not connected clients and PMKID from access points. It is able to capture handshakes from 5GHz clients on 2.4GHz (KaliTools, 2018). Useful for performing Client-Less attack.
    ---3.2  Hcxpacptool is a tool that shows the info of pcap/pcapng file and convert it to other hash format accepted by hashcat and John the Ripper (KaliTools, 2018).
    ---3.3  Hostapd-wpe:A replacement virtual radius server to the FreeRADIUS-WPE called Hostapd-wpe.
            Provide IEEE 802.1x Authenticator and Authentication Server impersonation attacks to obtain client credentials, establish connectivity to the client, and launch other attacks where applicable (KaliTools,2016).


    4.python
    5.John the Ripper,Hashcat,Crunch[password cracking]
   
# GUI Design

## WI-FI Pentest Tool

This WI-FI Pentest Tool is designed for testing the target Wi-Fi router. It’s included different attack method of WP2&WP3 wireless attack, such as DE-link attack, AP-Less attack, Client-Less attack. The advantages of the GUI is that the user can click the button to execute the command to saving time which make the penetration test
more effectively and it helps the user to record the useful data. So, let’s start with the options design.

![image](https://user-images.githubusercontent.com/51657418/110150310-14507a00-7e1a-11eb-9dac-4de766c22d40.png)


This page displays the wireless adapter interface, chipset, hardware driver.

**Tools:** Aircrack-ng
**Command:** airmon ng


Attack Method page

![image](https://user-images.githubusercontent.com/51657418/110150505-4f52ad80-7e1a-11eb-9650-09814001efa5.png)


After select the wireless adapter, there are fewer button which can execute the attack’s command. 
It would show on below, let us click DE-link button first.

## Attack Vector: De-authentication
## Scenario 1: WPA/WPA2 Personal Standard

![image](https://user-images.githubusercontent.com/51657418/110150632-714c3000-7e1a-11eb-9455-ea517816385c.png)



This page shows the scanning result on the table that each result would upload on the table.

Select and double click the table bar when your target was shown on the bottom table.

**Tools: Aircrack-ng**
**Command:      airmon-ng start wlan0**
              **airodump-ng wlan0mon**
              

![image](https://user-images.githubusercontent.com/51657418/110150723-8b860e00-7e1a-11eb-959e-d1de7fd7086b.png)



After the user selected the target, the application would ask for confirmation since it would shut down the WIFI connection of the targeted device.

**Tools: Aircrack-ng
Command:     aireplay-ng -0 10 -a {BSSID} -c {device mac address} wlan0mon**


![image](https://user-images.githubusercontent.com/51657418/110150771-99d42a00-7e1a-11eb-9177-2e005a943c9f.png)



After the user clicked the “DE-link start” button, a loading page will be directed. It means the application is launching the de-link attack to the target.

![image](https://user-images.githubusercontent.com/51657418/110150798-a062a180-7e1a-11eb-8c3f-a9644f4c5376.png)



After a few seconds, if the application captured the 4-way handshake successfully, a result page will be directed, and a message will be pop up to inform the user the attack is completed as expected.


## Scenario 2: WPA3 Personal Standard 

![image](https://user-images.githubusercontent.com/51657418/110150892-bf613380-7e1a-11eb-9a20-c9f5383f6622.png)



This page shows the scan result on the table that each result would upload on the table.

Select and double click the table bar when your target showed on the bottom table.

**Tools: Aircrack-ng
Command:      airmon-ng start wlan0
airodump-ng wlan0mon**

![image](https://user-images.githubusercontent.com/51657418/110150926-c8ea9b80-7e1a-11eb-928b-54635094fe18.png)



Next, a message will be pop up to inform the user downgrade attack could be applied to the targeted device.

![image](https://user-images.githubusercontent.com/51657418/110150968-d7d14e00-7e1a-11eb-94ef-82f5c7af7c2c.png)

After the user selected the target, the application would ask for confirmation since it would shut down the WIFI connection of the targeted device.

**Tools: Aircrack-ng
Command:     aireplay-ng -0 10 -a {BSSID} -c {device mac address} wlan0mon**

![image](https://user-images.githubusercontent.com/51657418/110151001-e15ab600-7e1a-11eb-98f0-2751a73e2855.png)



After the user clicked the “DE-link start” button, a loading page will be directed. It means the application is launching the de-link attack to the target.

![image](https://user-images.githubusercontent.com/51657418/110151015-e7509700-7e1a-11eb-95ab-9b557a8acfcd.png)



After a few seconds, if the application captured the 4-way handshake successfully, a result page will be directed, and a message will be pop up to inform the user the attack is completed as expected.



## Attack Vector: AP-Less attack
## Scenario: WPA/WPA2 Personal Standard

![image](https://user-images.githubusercontent.com/51657418/110151729-cb99c080-7e1b-11eb-8a3c-ec75335580b4.png)


This page shows the different attack methods to the target. First, click the “AP-less” button to perform further action.

![image](https://user-images.githubusercontent.com/51657418/110151764-d3596500-7e1b-11eb-9e85-dcb606d3c46a.png)



In this page, information of wireless access point will be display on the table.

All scanning information including the previous scan result, will be recorded in the file and the application will read the file’s information and display it in this tab.

If ESSID changed, the column of ESSID would be updated. Select and double click the table bar when the target is on the list.

**Tools: Aircrack-ng
Command: airodump-ng -c {channel} --bssid {BSSID} -w {the files location} wlan0mon**

![image](https://user-images.githubusercontent.com/51657418/110151797-de13fa00-7e1b-11eb-8330-f08a73541ee2.png)


After the user clicked the “AP-less” button, a loading page will be directed. It means the application is launching the AP-less attack and building a rogue wireless access point for the target to associate with.

![image](https://user-images.githubusercontent.com/51657418/110151816-e3714480-7e1b-11eb-94ea-d09d61bf4e2b.png)


If the user associated with the rouge wireless access point and the 4-way handshake is captured successfully, a result page will be directed, and a message will be pop up to inform the user the attack is completed as expected.



## Scenario: WPA3 Personal Standard

![image](https://user-images.githubusercontent.com/51657418/110151847-eb30e900-7e1b-11eb-89b7-67f1e36885be.png)


This page shows the different attack methods to the target. First, click the “AP-less” button to perform further action.

![image](https://user-images.githubusercontent.com/51657418/110151863-f1bf6080-7e1b-11eb-9829-e2d4b7687ad3.png)


In this page, information of wireless access point will be display on the table.

All scanning information including the previous scan result, will be recorded in the file and the application will read the file’s information and display it in this tab.

If ESSID changed, the column of ESSID would be updated. Select and double click the table bar when the target is on the list.


**Tools: Aircrack-ng
Command: airodump-ng -c {channel} --bssid {BSSID} -w {the files location} wlan0mon**

![image](https://user-images.githubusercontent.com/51657418/110151902-fedc4f80-7e1b-11eb-8ac3-d554289c4738.png)


After the user clicked the “AP-less” button, a loading page will be directed. It means the application is launching the AP-less attack and building a rogue wireless access point for the target to associate with.

![image](https://user-images.githubusercontent.com/51657418/110151950-0ef42f00-7e1c-11eb-8044-106f51fa6511.png)


If the user associated with the rouge wireless access point and the 4-way handshake is captured successfully, a result page will be directed, and a message will be pop up to inform the user the attack is completed as expected.

## Scenario: Enterprise Standard Attack

![image](https://user-images.githubusercontent.com/51657418/110151990-19aec400-7e1c-11eb-81b9-0db51fae8466.png)


This page shows the different attack methods to the target. First, click the “AP-less” button to perform further action.

![image](https://user-images.githubusercontent.com/51657418/110151997-1e737800-7e1c-11eb-8f0d-8fb0cae92426.png)


In this page, information of wireless access point will be display on the table.

All scanning information including the previous scan result, will be recorded in the file and the application will read the file’s information and display it in this tab.

If ESSID changed, the column of ESSID would be updated. Select and double click the table bar when the target is on the list.

This page would detect user selection, if the AP using “MGT” Authentication, the GUI would prepare the Enterprise (MGT) Standard Attack command.
 
**Tools: Aircrack-ng, hostapd-wpe
Command: (1) sed -i '15c ssid="+{ESSID}+"' /etc/hostapd-wpe/hostapd-wpe.conf
         (2) airmon-ng check kill
         (3) hostapd-wpe /etc/hostapd-wpe/hostapd-wpe.conf
**

![image](https://user-images.githubusercontent.com/51657418/110152060-35b26580-7e1c-11eb-9888-3212feff435d.png)


After the user clicked the “AP-less” table row, a loading page will be directed. It means the application is launching the Enterprise Standard attack and building a rogue wireless access point for the target to associate with.

![image](https://user-images.githubusercontent.com/51657418/110152077-3ba84680-7e1c-11eb-93fc-90f739817298.png)


If the user associated with the rouge wireless access point and the 4-way handshake is captured successfully, a result page will be directed, and a message will be pop up to inform the user the attack is completed as expected.

## Attack Vector: Client-Less 
## Scenario: WPA/WPA2 Personal Standard

![image](https://user-images.githubusercontent.com/51657418/110152352-9641a280-7e1c-11eb-9b24-d6e0b28c2da9.png)


This page shows the different attack methods to the target. First, click the “Client-less” button to perform further action. 

![image](https://user-images.githubusercontent.com/51657418/110152370-9c378380-7e1c-11eb-92ae-5c520cd7968d.png)


In this page, information of wireless access point will be display on the table.

All scanning information including the previous scan result, will be recorded in the file and the application will read the file’s information and display it in this tab.

If ESSID changed, the column of ESSID would be updated. Select and double click the table bar when the target is on the list.

**Tools: Aircrack-ng **
**Command: echo "BSSID" > filter.txt **


![image](https://user-images.githubusercontent.com/51657418/110152461-bd986f80-7e1c-11eb-952c-d63159cad799.png)


After the user clicked the “Client-less” button, a loading page will be directed. It means the application is launching the Client-less attack to the wireless router and capturing the PMKID from the wireless router.

![image](https://user-images.githubusercontent.com/51657418/110152478-c5f0aa80-7e1c-11eb-8440-07c061c11df3.png)

If the user associated with the rouge wireless access point and the PMKID is captured from the wireless router successfully, a result page will be directed, and a message will be pop up to inform the user the attack is completed as expected.

## MAC-Spoofing

It is a good practice to change the mac address before doing a penetration test because the MAC filtering function may be enabled for some wireless routers. 

![image](https://user-images.githubusercontent.com/51657418/110152526-d43ec680-7e1c-11eb-81e5-d86f741282d1.png)

This page shows clients that have connected to wireless access points before.
Select and double click the table bar to change the wireless adapter’s MAC address to camouflage as the one of above client on the table.

![image](https://user-images.githubusercontent.com/51657418/110152545-da34a780-7e1c-11eb-9b84-367b1a595a9b.png)


Another page will be directed and shows any client that is connected to the targeted wireless access point. In the middle of the table, ESSID with client BSSID will be displayed.


If the user wants to change the MAC address with manual operation, the user can insert the MAC address in the text area which is under the row with “add MAC-address to MAC spoofing” description and click “add” button to perform MAC spoofing.


![image](https://user-images.githubusercontent.com/51657418/110152575-e1f44c00-7e1c-11eb-90ff-49e01b8bfd0b.png)










