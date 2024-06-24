# Network Traffic Analysis with Wireshark
## Introduction

In today’s digital age, understanding how data travels across networks is more important than ever. Whether you’re a network enthusiast, a student, or someone looking to dive into cybersecurity, knowing how to analyze network traffic can give you a significant edge. This is where Wireshark comes in.

Wireshark is a free and open-source tool that helps you see what’s happening on your network at a very detailed level. Think of it as a magnifying glass for your network, allowing you to capture and analyze data packets — the tiny pieces of information that make up network communication. With Wireshark, you can troubleshoot network problems, improve security, and learn more about how networks operate.

In this article, we’ll start from the very basics and guide you through everything you need to know to get started with Wireshark. You’ll learn how to install the software, capture network traffic, and understand the data you see. We’ll also cover some common scenarios where Wireshark can be incredibly useful.

By the end of this guide, you’ll have a good grasp of how to use Wireshark to explore your network, solve problems, and gain valuable insights. So, let’s get started on your journey to becoming a Wireshark pro!

## 1. What is Wireshark?
### 1.1 Overview
Wireshark is a network packet analyzer. A network packet analyzer presents captured packet data in as much detail as possible.

It is particularly useful for troubleshooting network issues, analyzing network protocols and ensuring network security. Networks must be monitored to ensure smooth operations and security.

Wireshark is available for free, is open source, and is one of the best packet analyzers available today.

### 1.2 Key Features
- Capture live packet data from a network interface.
- Display packets with very detailed protocol information.
- Filter and search for specific packets of interest.
- Color-code packets for easier analysis.

## 2. Installing Wireshark
### 2.1 Windows Installation
- The official Windows packages can be downloaded from the Wireshark main page or the download page. Installer names contain the version and platform.
- You can choose to install several optional components and select the location of the installed package. The default settings are recommended for most users.
- The Wireshark installer contains the latest Npcap installer.
- If you don’t have Npcap installed you won’t be able to capture live network traffic but you will still be able to open saved capture files. By default the latest version of Npcap will be installed. If you don’t wish to do this or if you wish to reinstall Npcap you 
 can check the Install Npcap box as needed.

### 2.2 macOS Installation
- The official macOS packages can be downloaded from the Wireshark main page or the download page. They are signed by Wireshark Foundation. Packages are distributed as disk images (.dmg) containing the application bundle. Package names contain the platform and version.
- To install Wireshark simply open the disk image and drag Wireshark to your /Applications folder. macOS packages automatically update.
- In order to capture packets, you must install the “ChmodBPF” launch daemon. The installer package includes Wireshark along with ChmodBPF and system path packages.

### 2.3 Linux Installation
- Wireshark can be installed on various Linux distributions using their respective package managers.
- If your distribution uses yum, use the following command to install Wireshark together with the Qt GUI:
 ```yum install wireshark wireshark-qt```
- For installation from debs under Debian, Ubuntu and other Debian derivatives ,If you can just install from the repository then use
 ```apt install wireshark```

## 3. Getting Started with Wireshark
### 3.1 Launching Wireshark
You can start Wireshark from your shell or window manager.

When you first open Wireshark, you’ll be greeted by the main interface. Here’s an overview of the key components you’ll see:


### 3.1.1 Menu Bar
Located at the top, the menu bar provides access to various functions and settings in Wireshark, such as File, Edit, View, Capture, Analyze, Statistics, Telephony, and Help.


### 3.1.2 Toolbar
Directly below the menu bar, the toolbar offers quick access to common actions like starting and stopping captures, opening files, saving captures, and applying filters.


### 3.1.3 Capture Interfaces
In the central part of the screen, you’ll see a list of available network interfaces. These are the network adapters on your computer that you can use to capture network traffic. Each interface is listed with details such as its name, IP address, and current traffic activity.


### 3.1.4 Interface Graphs
Next to each interface, you’ll see a graph displaying the current traffic on that interface. This can help you choose the right interface for capturing the traffic you’re interested in.


### 3.1.5 Display Filter Bar
Just below the toolbar, the display filter bar allows you to enter expressions to filter the captured packets. For example, you can type http to show only HTTP packets.


## 3.2 Capturing and Analyzing Traffic
### 3.2.1 Starting a Capture
- From the initial interface, choose the network interface you want to capture traffic from. Look for an interface with activity, indicated by the moving graph next to it.
- Click the blue shark fin icon on the toolbar or double-click the selected interface to start capturing packets.
- The following interface will be displayed

### 3.2.2 During Capture
Once you start capturing, the interface will display real-time data:

1. Packet List Pane (Top pane)
- This pane fills up with packets as they are captured. Each row represents a single packet, displaying columns for:
- No.: The packet number in the order it was captured.
- Time: The timestamp when the packet was captured relative to the start of the capture.
- Source: The originating IP address of the packet.
- Destination: The receiving IP address of the packet.
- Protocol: The protocol used in the packet (e.g., TCP, UDP, HTTP).
- Length: The size of the packet in bytes.
- Info: Additional protocol-specific information about the packet.
2. Packet Details Pane (Bottom left pane)

This pane shows detailed information about the selected packet. It breaks down the packet into its protocol layers, such as Ethernet, IP, TCP, etc. You can expand each layer to see detailed fields and values.

3. Packet Bytes Pane (Bottom right pane)

This pane displays the raw data of the selected packet in both hexadecimal and ASCII formats. This view is useful for low-level analysis.

### 3.2.3 Stopping a Capture
- Click the red square icon on the toolbar to stop capturing packets. You can also use the Capture menu and select Stop.
- After stopping the capture, you can save the captured packets for later analysis. PCAP (Packet Capture) files are the standard format for storing network traffic captured by tools like Wireshark.
- Saving your capture as a PCAP file allows you to analyze the data offline, share it with colleagues, and keep a record of network events for future reference. PCAP files store raw network packets, including metadata such as timestamps and capture interface information, making them an essential resource for detailed network analysis.

## 3.3 Analyzing Captured Traffic
### 3.3.1 Applying Display Filters
Display filters in Wireshark are powerful tools that help you focus on specific packets within your captured data. Here’s how to use them:

1. Using Display Filters
Enter a filter expression in the display filter bar located just below the toolbar to narrow down the packets shown in the packet list pane. For example:

- http to show only HTTP packets.
- ip.addr == 192.168.1.2 to display packets with the specified IP address.
- tcp.port == 80 to view packets on TCP port 80.

2. Common Filters

Use these common display filters for various analysis tasks:

- dns for DNS traffic.
- icmp for ICMP traffic (e.g., ping requests and responses).
- tcp for all TCP traffic.
- udp for all UDP traffic.

3. Filter Expressions

Combine multiple conditions using logical operators (and, or, not):

- ip.src == 192.168.1.1 and tcp.port == 80 to show packets from a specific IP address and TCP port.
- http or dns to display either HTTP or DNS packets.
- not tcp to exclude all TCP packets.

### 3.3.2 Following TCP/UDP Streams
Following streams in Wireshark allows you to view an entire conversation between two endpoints, making it easier to analyze specific sessions like HTTP requests and responses:

1.Follow TCP Stream
- Right-click on a HTTP packet in the packet list pane.
- Select Follow > TCP Stream from the context menu.
- A new window will open displaying the entire TCP conversation between the source and destination IP addresses.

2. Follow UDP Stream

- Right-click on a DNS packet in the packet list pane.
- Select Follow > UDP Stream from the context menu.
- A new window will open showing the complete UDP conversation.

3. Stream Window Features

- The stream window presents the data in a readable format, color-coded by direction:
- Red text indicates data sent from the source to the destination.
- Blue text indicates data sent from the destination to the source.
- Use the drop-down menu to switch between ASCII, EBCDIC, Hex Dump, and C Arrays representations of the stream data.

## 4. Advanced Features
### 4.1 Customizable Color Rules
- Navigate to View > Coloring Rules to define custom color schemes based on various packet attributes such as protocols, IP 
 addresses, or specific data patterns.
- Visual differentiation helps quickly identify important packets or anomalies in the traffic flow.
 Facilitates focused analysis by highlighting critical information, improving efficiency in troubleshooting and network 
 monitoring.

### 4.2 Pane Selection and Font Preferences
- Access Edit > Preferences to customize display settings including pane layout and font styles.
- Adjust pane configurations to prioritize relevant information based on your analysis needs.
- Modify font sizes and styles to improve readability and accommodate personal preferences during prolonged analysis 
 sessions.



## Conclusion
In conclusion, Wireshark is an excellent tool for analyzing network traffic, playing a vital role for security analysts in network analysis. As I embarked on my journey to become a SOC analyst a few months ago, Wireshark has been instrumental in my learning process. I plan to share my progress through guides and write-ups as I continue to develop in this field. Thank you for reading. Please leave a comment below if you have any feedback or corrections, as your input will help me improve.

## References
- Wireshark Documentation: https://www.wireshark.org/docs/wsug_html_chunked/
- HackerSploit Wireshark Playlist: https://www.youtube.com/playlist?list=PLBf0hzazHTGPgyxeEj_9LBHiqjtNEjsgt
