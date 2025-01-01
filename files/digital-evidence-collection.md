# Digital Evidence Collection

## Equipment

* **Forensic Laptop or Workstation**
  * popular Linux distributions such as CAINE or DEFT can often be found on these laptops, as well as commercialized systems for law enforcement
* **Electro-Static Evidence Bags with Tamper-proof Stickers**
  * help protect any sensitive digital components from Electro-Static Discharge (ESD) during the transport of the evidence
  * having bags or stickers that are sealed, and the seal must be physically broken to gain access to the evidence within is critical to ensure the chain of custody
* **Labels**
* **Photographs**
  * to document how IT equipment was found to maintain the Chain of Custody
    * e.g., what cables were plugged in to a server, what external hard drives were connected to a laptop, what was on the screen, etc.
* **Grounding Bracelets**
  * ensure that when handling evidence, they do not inadvertently compromise or damage the evidence
* **Hardware Write-Blockers**
  * ensure that your evidence has not been tampered with
  * can either be software on your forensic laptop, or a hardware device that permits read-only access to data storage devices
* **Blank Hard Drives**
  * can be used in conjunction with write-blockers to copy the disk to another one without making any writeable changes to the media
  * need to be extremely high capacity, especially if bit-by-bit copies of suspect hard drives are being copied
  * size of the receiving drive must always be higher than that of the original drive

## Specialist Equipment

* **Wireless Stronghold/Faraday Boxes**
  * to block any wireless signals from reaching the evidence
  * prevents remote access or wiping
* **Specialized Write-Blockers**
  * used on cell phones, GPS devices, IoT devices, and other non-standard hard drives
* **Phone Jammers**
  * instead of blocking signals passively (like a Faraday box), it actively emits radio signals on the same frequency as mobile devices to disrupt communication between phones and nearby cell towers.
    * Faraday box is a physical enclosure (like a metal box) that blocks electromagnetic signals, ensuring no wireless signals (e.g., Wi-Fi, mobile, Bluetooth) can pass in or out.
* **Dedicated Flash Drives**
  * contain tools like Encase, FTK, CSILinux, and MacQuisiton

---

## ACPO Principles

* The main principles of the [ACPO Good Practice Guide for Computer-Based Electronic Evidence](https://www.digital-detective.net/digital-forensics-documents/ACPO_Good_Practice_Guide_for_Digital_Evidence_v5.pdf) are:
    1. That no action is taken that should change data held on a digital device including a computer or mobile phone that may subsequently be relied upon as evidence in court.
    2. Where a person finds it necessary to access original data held on a digital device, that the person must be competent to do so, and able to explain their actions and the implications of those actions on the digital evidence to a Court.
    3. That a trail or record of all actions taken that have been applied to the digital evidence should be created and preserved. An independent third-party forensic expert should be able to examine those processes and reach the same conclusion.
    4. That the individual that is leading the investigation has the overall responsibility to ensure that the ACPO principles are followed throughout the investigation.

---

## Chain of Custody

* primary purpose is to ensure that all of the evidence collected in a case has not been tampered with by an unauthorized individual and the original evidence remains unchanged
* court is able to dismiss the evidence if a clear Chain of Custody cannot be presented

---

* **Evidence Integrity Hashing**
  * before doing anything calculate the hash first
  * hash is calculated before and after handling and compared to confirm that no alterations have been made
  * hash does not necessarily have to be cryptographically secure, since it is only used to verify the integrity of the evidence
  * always hash the evidence using at least two methods – most popular ones being MD5 and SHA1
    * to avoid hash collision attack
    * SHA256 can be used to generate hashes, as they have not caused collisions before
  * if the evidence is physical, such as an external hard drive, you should use a hardware write blocker when you connect your workstation to the device
    * although software options are available, hardware write blockers are the most effective

---

* **Taking a Forensic Copy**
  * it is best to make a forensic copy of the original evidence if possible and perform analysis on the copy
  * many tools are available for this process
    * simpler bit-by-bit cloning using the `dd` command in Linux
    * forensic image generators that automatically add metadata and Chain of Custody information
      * Forensic Toolkit (FTK) and EnCase

---

* **Storing Digital Evidence**
  * physical evidence should be stored in antistatic bags which prevent damage through electric discharge to the data it holds
  * Faraday cages may be used, which prevents wireless communication and cellular signal exchange of the device within it
  * evidence should be kept within a locked container, which only the authorized examiners have access to, and kept within an authorized personnel’s watch during transportation

---

* **Chain of Custody Form**
  * form should include the description of the evidence when/where it has been acquired or transferred, and by whom, the contacts of the examiners, how the evidence has been accessed, collected or stored and other details regarding the evidence

---

## Disk Imager: FTK Imager

