# Intro to Wireshark

* **Wireshark Startup Window**
    ![](images/Screenshot%20from%202025-01-13%2016-22-53.png)
  * **Start Capture**
    * The blue button in the top left corner starts capturing inbound and outbound packets, with the specified capture filters, on the specified interface
  * **Open Saved Files**
    * Wireshark traffic capture files can be saved in several formats, such as .cap, .pcap or .pcapng, and can be opened in the Main Window for analysis
  * **Capture Filter**
    * You can write expressions in the capture filter to limit the types of packets that Wireshark captures
      * e.g. the not arp capture filter, Wireshark avoid capturing Address Resolution Protocol packets
      * can be saved for reuse
  * **Capture Interface Selection**
    * Wireshark lists all available interfaces that it can capture on, with a graph of the recent network activity on each of those interfaces
    * select an interface that you want to capture traffic on
      * e.g. `en0` for Wi-Fi traffic and `vboxnet0` for virtual network traffic
    * it is recommended that promiscuous mode be turned on for capturing interfaces
      * Promiscuous mode allows Wireshark to capture packets that are received on an interface but not actually addressed to the host
        * e.g. frames transmitted on a wireless network with different MAC addresses
        * allows Wireshark to capture other hosts’ traffic and have a broader picture of the network
        * can be managed by clicking on the cog-shaped button in the top menu bar, and toggling the setting for a specific interface or for all interfaces
        ![](images/Screenshot%20from%202025-01-13%2016-24-18.png) 
* **Wireshark Main Window**
  ![](images/Screenshot%20from%202025-01-13%2016-26-36.png)
  * where all of the capturing and analysis happens
  * **Menu Bar**
    * used to manage the capture
    * In the far left section, you can start, stop and restart the capture, and manage capture interface settings
    * The magnifying glass icon is used to find a specific packet using a display filter or by a string or bytes within the packet
  * **Display Filter**
    * used to display only specified packets
    * You can construct an expression by specifying header fields and optionally, the values that they should match
    ![](images/Screenshot%20from%202025-01-13%2016-32-29.png) 
  * **Panes**
    * 3 main panes:
      * **Packet List**
        * aggregates major information on the packets that Wireshark captures, in columns
        * should display the packet number (the later the packet was captured, the higher this number is), time since the start of capture, the source and destination IP addresses, the protocol, the packet length and a summary of the packet headers or contents
      * **Packet Headers**
        * provides information on each individual packet
        * organizes packet header fields and values in layers – from Layer 1 frame information to Layer 7 protocol contents
        ![](images/Screenshot%20from%202025-01-13%2016-36-07.png) 
      * **Hex Dump & ASCII**
        * On the bottom pane, you can see the hexadecimal and ASCII representation of the entire packet
        ![](images/Screenshot%20from%202025-01-13%2016-38-18.png)

---

