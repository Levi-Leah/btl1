# Detection and Analysis Phase

* Common Events & Incidents
  * **Remote to Local Scanning**
    * external public IP address is scanning the public IP addresses owned by the organization
    * typically conducted to see what IP addresses are used by the organization, which of them are in use, and what ports are open
    * we would want to collect logs from perimeter firewalls and web application firewalls
    * detection
      * The rule would look for multiple connections within a small timeframe to a number of different ports on the system
      * web servers should only ever be contacted on ports 80 (http) and 443 (https)
      * a remote system that starts connecting on 93, 1195, 1959, and other random non-standard ports is most likely scanning or fingerprinting the system
    * impact
      * older systems could be affected by scanning if there is no scalability, and the actor is performing an intense scan
      * could potentially use up a lot of bandwidth and lead to other systems not being able to connect to it, causing a denial-of-service (DoS)
  * **Remote to Local DoS/DDoS**
    * one (DoS) or more (DDoS) external IP addresses are sending a high volume of requests or malformed packets to a target system in an attempt to crash it
    * detection
      * We can use rules that monitor the number of requests the systems in the DMZ receive and establish a baseline for the levels of “normal” traffic that is expected to be received
      * then create a rule that will generate an alert when a threshold higher than the baseline is observed
    * impact
      * have the potential to take systems offline
      * can result in loss of customer trust, a decline in sales, and potentially even damage to the affected system
  * **Local to Local Scanning**
    * an internal private IP address is scanning another, or multiple, private IP addresses
    * sending out requests and receiving replies, using these to determine what systems are active and perform fingerprinting activities to identify the operating system and any running services on other hosts
    * detection
      * SIEM rules can be configured to generate alerts when one private IP is making rapid connections to other internal private IPs
      * thresholds or patterns should be used to prevent false positives
      * internal vulnerability scanners should be whitelisted from any L2L scanning rules
    * impact
      * an internal system has been compromised, the likely next step for an attacker once persistence has been achieved would be to identify other systems in the same network so they can perform lateral movement
      * they will identify other systems by conducting scans using ARP, UDP, TCP, or ICMP to see what other IPs are in use, and what ports and services are running on them, looking for a way into the machine
  * **Login Failures**
    * detection
      * in win env

      | Status and Sub Status Codes | Description (not checked against "Failure Reason:")                                               |
      |-----------------------------|---------------------------------------------------------------------------------------------------|
      | 0xC0000064                  | User name does not exist                                                                         |
      | 0xC000006A                  | User name is correct but the password is wrong                                                  |
      | 0xC0000234                  | User is currently locked out                                                                    |
      | 0xC0000072                  | Account is currently disabled                                                                   |
      | 0xC000006F                  | User tried to log on outside their day of week or time of day restrictions                      |
      | 0xC0000070                  | Workstation restriction, or Authentication Policy Silo violation (look for event ID 4820 on domain controller) |
      | 0xC0000193                  | Account expiration                                                                              |
      | 0xC0000071                  | Expired password                                                                                |
      | 0xC0000133                  | Clocks between DC and other computer too far out of sync                                        |
      | 0xC0000224                  | User is required to change password at next logon                                               |
      | 0xC0000225                  | Evidently a bug in Windows and not a risk                                                       |
      | 0xC000015B                  | The user has not been granted the requested logon type (aka logon right) at this machine        |

    * in win env, we can monitor Windows Security Log Event ID 4625, and set thresholds to detect multiple login failures against the domain controller for the same username
  * impact
    * users that are locked out can’t work, resulting in a decline in productivity
    * login failures where the username is not recognized (0xC0000064) or the account is locked out because of too many failed logins (0xC00000234) could be signs of an attacker that is trying to gain access to internal accounts using a username and password wordlist or employing a dictionary attack

---

* **Using Baselines & Behaviour Profiles**
  * **Baselining**
    * Baselining refers to the recording and profiling of what is considered to be “normal” on a system or in a network
      * can include network utilization, protocol field values, active hours, user activity, port numbers, and any factor that could change
    * baseline can be consistently compared to the current state of the network to identify any anomalies
    * the process of identifying potentially malicious events using differences between the status of the current network and the baselined network is categorized as **anomaly-based detection**
  * **Anomaly-Based Detection**
    * anomaly-based detection is an effective defense mechanism against new and unprecedented attacks and threats
    * unlike signature-based detection which is based upon factors such as file hashes, where any variants of malware cannot be detected, anomaly-based detection allows detection for malicious activities and network behavior, which are hard to discretely define
    * detecting anomalies in network traffic allows for an excellent detection mechanism against DoS/DDoS attacks and attacks through an encrypted channel
    * since network, system, or application behavior is abstract, unpredictable, and highly dynamic, many false positives are generated
    * baselining networks can take a substantial amount of time which grows with the complexity and scale of the network, causing implementation delays
    * baselining process should be repeated after time intervals and after significant changes to the network, and finely adjusted to provide both an updated picture of the network and reduce false positives
  * **Enhanced Detection**
    * Baselining and anomaly-based detection can be incorporated into a wider group of security controls, systems, and procedures in order to improve the organization’s overall security posture