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

* **Applying Display Filters**
  * controls which packets are shown in the packet list
  * `tcp.port == 80`
    * displays packets that have a source or destination port of 80 (HTTP)
  * `tcp.window_size_value >= 8000`
    * displays TCP packets with a window size of 8000 bytes or over
  * filter statements can be chained by using logical operators
    * `&&` - and
    * `||`, `or` - or
    * `not`, `!` - not
    * `ip.dst_host == 192.168.1.7 && tcp`
      * display TCP packets addressed to 192.168.1.7
    * `ntp or udp.port == 20000`
      * display either NTP traffic or UDP traffic from/to port 20000
    * To follow a stream, right-click on a packet within the stream, and click **Follow** > **TCP/UDP/SSL/HTTP Stream**
    ![](images/Screenshot%20from%202025-01-13%2016-47-11.png)
    * HTTP requests should be highlighted in red and HTTP responses in blue
    * To add a packet header value as a column, right-click the header field and select Apply as Column
    ![](images/Screenshot%20from%202025-01-13%2016-49-00.png)

---

* **Viewing Capture Statistics**
  * Wireshark collects different statistics about the traffic in the capture file
    * e.g., percentage proportions of protocols, the number of bytes transmitted to different hosts, the IP addresses of all the hosts that has appeared in the capture
  * helpful when identifying potential exfiltration vectors and the exfiltrating host based on network usage
  * can also identify data exfiltration through unusual or unused protocols
    * If you notice a very small portion of FTP traffic in a large network that doesn’t use FTP, it might be worth it to check out the FTP traffic and make sure the traffic is legitimate
    * Quite a few of network analysis challenges in CTFs dealing with data exfiltration can be solved by identifying unusual protocols from the Protocol Hierarchy window
  * **Protocol Hierarchy**
    * displays the percentages of the number of packets or bytes in a protocol conversation against the entire traffic
    * protocols are organized in layers from Layer 2 to Layer 7
    ![](images/Screenshot%20from%202025-01-13%2016-52-41.png) 
    * To check a specific protocol traffic in the packet list, right-click on a protocol and select **Apply as Filter** > **Selected/Not Selected**
  * **Conversations**
    * provides a wealth of information on the traffic, including which hosts have communicated to other hosts, on which ports, and with a total of how many bytes and packets in the conversation
    * great for identifying the different MAC or IP addresses that a host has communicated with, and the volume of traffic between them
    * can be very helpful in investigating data exfiltration attempts, as it can identify the attacker by IP address
    * If a host has been transmitting many packets and bytes to an unidentified IP address without receiving many packets in return, an exfiltration could have been occurring
    ![](images/Screenshot%20from%202025-01-13%2016-55-46.png)
    * you can right-click on a line, select **Apply as Filter** > **Selected/Not Selected** and choose the direction of traffic to apply a filter for the line
  * **Endpoints**
    * shows all of the different hosts that appear in the capture and the amount of packets/bytes they sent and received
    * useful in sorting hosts by their network activity, by either transmission or receiving volume, or by both
    * If a host has been receiving much more traffic than they have been transmitting, the host is probably downloading a large file
    *  if the host has been transmitting more than they have been receiving, the host is probably uploading files or backing up to remote storage
    ![](images/Screenshot%20from%202025-01-13%2016-58-22.png)

---

```[cli]
!tcp && eth.src != 0a:00:27:00:00:00
Statistics > Conversations
# see downloaded files ands save them
Wireshark > File > Export Objects
md5sum cr4ckx0r.zip | cut -c 1-5
FTP code 230 for successful login
FTP ctrl+F RETR to search for downloads
View > Time Display Format > Date and Time of Day
```