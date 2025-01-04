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

* **Dumping RAM**
  1. File > Capture Memory
  2. Add filepath e.g. `~/dir/memorydump.mem`
  * You can output it to other tools such as Volatility for analysis purposes
* **Hard Drive Imaging**
  * IRL
    ![](images/Screenshot%20from%202025-01-04%2019-45-20.png)
    * hard drive gathered from a crime scene will be connected to a forensic workstation with a clean hard drive attached
    * write-blocker will be used between the workstation and the suspect hard drive
    * analyst will then start a bit-by-bit copy of the suspect’s hard drive to the blank one
      * can take an extremely long amount of time
  * We can create a system `.img` file using FTK Imager
    1. File > Create Disk Image
    2. Select source
    3. Fill out evidence item info
    4. Select output destination
    5. Set format type to `.E01` file
        * This filetype is used by analysis tools, such as the enterprise-grade forensics triage software EnCase
    6. Set the Image Fragment Size to 0MB
       * disk image won’t be split into smaller segments; will be all in one file
  * alternatively, use `ProcDump`
    * system administrator tool that is in the Sysinternals suite of tools from Microsoft
    1. Run PowerShell as admin
    2. Get PID of the running process (e.g. malware running on a system):

        `Get-Process | findstr -I <PROCESS_NAME>`

    3. Run `ProcDump`:

        `.procdump.exe -ma <PID>`

---

## Live Forensics

* branch of digital forensics that focuses specifically on computers and other IT systems that are powered on
* volatile artifacts often only exist while a system is turned on, and shutting the system off would cause these artifacts to be lost
* it’s crucial to collect it, but not jeopardize other data that could be affected by aspects such as SSDs that use Garbage Collection or TRIM
* the possibility that evidence is stored in RAM is very high
* while there are ways to preserve it, acquiring this information while the system is online is the most effective
* live forensics can battle methods criminals use to prevent analysis:
  * full disk encryption
    * can sometimes be reversed by extracting the encryption key from RAM
  * using live CDs instead of an installed OS
  * cloud storage
    * cloud or other internet-based storage can be detected and downloaded while the machine is still running and connected to the service provider

---

## Live Acquisition: KAPE

* Kroll Artifact Parser and Extractor
* can target essentially any device or storage location, find forensically useful artifacts, and parse them within a few minutes
* during a digital investigation:
  * disk imager should be initialized to collect a full disk image of the target system
  * KAPE should be run alongside to immediately collect important evidence, even before the full disk image has been acquired
* possible to deploy KAPE on a large scale using PowerShell to download, run, and send the results from KAPE back to the security team
* Ypu can retrieve Windows event logs, antivirus logs, file system metadata, log files, deleted files, emails, and absolutely tons more
* `kape.exe`
* `gkape.exe` - GUI
  ![](images/Screenshot%20from%202025-01-04%2019-56-20.png)
  1. Choose target source
  2. Select targets
  3. Choose target destination

---

## Evidence Destruction

* **Degaussing**
  * when exposed to the powerful magnetic field of a degausser, the magnetic data on a tape or hard disk is neutralized or erased
  * guaranteed form of hard drive erasure
  * guarantee that your information is no longer retrievable

---

* **File Shredding**
  * can sometimes be the same as manually deleting a file or folder
  * not a secure method of deleting digital evidence, as there is the possibility it can be recovered
  * some file shredding programs utilize different methods to overwrite or sanitize the data that has been selected for shredding
    * [DoD 5220.22-M Wipe Method](https://www.lifewire.com/data-sanitization-methods-2626133)
      * Writes a zero and verifies the write
      * Writes a one and verifies the write
      * Writes a random character and verifies the write

---

* **Physical Shredding**
  * destroying physical storage media so that it can’t be reassembled and accessed
  * hard drive, USB, or other hardware will be shredded into small pieces using industrial-grade destruction equipment
  * destroys the drive platters, mechanisms, and the electronic components rendering the data unrecoverable

---

* **Hydraulic Crusher**
  * uses a hydraulic press with a metal rod that is pushed straight through the hard drive
  * punching a hole with approximately 3,400 kilos of force pressure completely destroys the drive platters, rippling and fracturing the magnetic surfaces and rendering the drive data unrecoverable
  * other methods can include bending the hard drives until they snap

---

* **Overwriting**
  * useful in case you want to reuse the equipment as it doesn't result in physical destruction
  * e.g. write zeros to a hard drive, overwriting any existing data
  * Windows offers a function called Diskpart that allows you to completely clear a hard drive from the command prompt

