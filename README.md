<h1>Reconnaissance with HPING </h1>


<h2>Description</h2>
Hping is a TCP/IP packet assembler and analyzer. In this lab, I learned to use hping to create
packets as well as perform different network functions with the packets.
<br />



<h2>Environments Used </h2>

- <b>Kali Linux</b> 
- <b>pfSense</b>
- <b>OWASP Broken Web App</b>

<h2>Utilities and Language </h2>

- <b>Terminal</b>

<h2>Program walk-through:</h2>

<p align="center">
With hping, a packet can be crafted with a specific protocol. Type the "hping3 -1 192.168.68.12" command
 using ICMP as the protocol followed by pressing the Enter key. After about 6 packets are transmitted, press CTRL+C to stop hping from running.<br/>
<img src="https://i.postimg.cc/Ss6Qk3Bs/Screen-Shot-2022-09-25-at-9-44-07-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />
  
  
  
  
  
<br />
Try a different ICMP type using a timestamp ICMP Type 13. Enter the "hping3 –c 3 -1 –V –C 13 192.168.68.12" command
below, limiting the number of packets sent to 3 and get feedback using the
verbose option. <br/>
<img src="https://i.postimg.cc/Jn0wdgRv/Screen-Shot-2022-09-25-at-9-49-06-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />







<br />
Enter the "hping3 –c 5 –T -1 -V 192.168.68.12" command below to perform traceroute functions using ICMP.<br/>
<img src="https://i.postimg.cc/ydhHR9YY/Screen-Shot-2022-09-25-at-9-53-42-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />


<br/>
<br/>
<br/>
<b> Using hping for Port Scanning </b>
<br/>
<br/>
<br/>




<br />
Within the Terminal window, click File and select New Window to launch a new
one. Enter the "tcpdump –i eth0" command in the new terminal to start capturing packets. Let tcpdump run in the background uninterrupted. <br/>
<img src="https://i.postimg.cc/3Rhwz3kN/Screen-Shot-2022-09-25-at-9-59-33-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />







<br />
Hping can craft packets sending various TCP flags set to test the ports being
scanned. Send a packet with SYN set from a source port of 5151, which is
arbitrarily chosen, to port 80 of the OWASP VM. Return to the other Terminal
window and enter the "hping3 –S –c 1 –s 5151 –p 80 –V 192.168.68.12" command to run a simple test..  <br/>
<img src="https://i.postimg.cc/XJ8QCKm8/Screen-Shot-2022-09-25-at-10-04-54-PM.png" height="80%" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />








<br />
Change focus to the terminal running tcpdump and notice a SYN [S] flag was sent
with a received Reset [R] flag.<br/>
<img src="https://i.postimg.cc/Tw7Nsq0P/Screen-Shot-2022-09-25-at-10-09-10-PM.png" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />





<br />
Change focus to the other terminal window and try the same scan against the
firewall by entering the "hping3 –S –c 1 –s 5151 –p 80 –V 192.168.9.1" command. <br/>
<img src="https://i.postimg.cc/s2Z0LZ8P/Screen-Shot-2022-09-25-at-10-14-05-PM.png" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />








<br />
Change focus to the terminal running tcpdump and notice a SYN [S] flag was sent
with a received Reset [R] flag. <br/>
<img src="https://i.postimg.cc/B639cg6P/Screen-Shot-2022-09-25-at-10-18-54-PM.png" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />





<br />
Change focus to the other terminal and enter the "hping3 –S –c 1 –s 5151 –p 22 –V 192.168.9.1" command  to try a
different port, SSH port 22, against the firewall. Notice 100% packet loss due to port 22 being closed on the firewall. <br/>
<img src="https://i.postimg.cc/QCY0dpny/Screen-Shot-2022-09-25-at-10-25-00-PM.png" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />





<br />
 Initiate a port scan against the firewall, defining a range. Enter the "hping3 –S -8 20-80 –c 1 –s 5151 –V 192.168.9.1" command.<br/>
<img src="https://i.postimg.cc/0yKnfKbp/Screen-Shot-2022-09-25-at-10-29-36-PM.png" width="80%" alt="Configuring Advanced Ethernet Options Steps"/>
<br />





