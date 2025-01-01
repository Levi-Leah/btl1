# Digital Forensics Fundamentals

## Intro to Data Representation

| Denary | Binary | Octal | Hexadecimal |
|--------|--------|-------|-------------|
| 0      | 0000   | 0     | 0           |
| 1      | 0001   | 1     | 1           |
| 2      | 0010   | 2     | 2           |
| 3      | 0011   | 3     | 3           |
| 4      | 0100   | 4     | 4           |
| 5      | 0101   | 5     | 5           |
| 6      | 0110   | 6     | 6           |
| 7      | 0111   | 7     | 7           |
| 8      | 1000   | 10    | 8           |
| 9      | 1001   | 11    | 9           |
| 10     | 1010   | 12    | A           |
| 11     | 1011   | 13    | B           |
| 12     | 1100   | 14    | C           |
| 13     | 1101   | 15    | D           |
| 14     | 1110   | 16    | E           |
| 15     | 1111   | 17    | F           |

* data formats you're likely to encounter at work
  * Binary
    * One bit contains a single binary value — either a 0 or a 1.
    * One byte contains eight bits, which means it can have 256 (28) different values.
  * Base64
    * reversible encoding algorithm that allows for the transformation of data from the original form to strings
    * works on images and binary files into text strings, which can be reversed to retrieve the original data in it’s original form
  * Hexadecimal
  * Octal
  * ASCII

---

## Hard Disk Drive (HDD) Basics

* typically where a lot of digital evidence is stored and collected
* non-volatile memory hardware device that controls the positioning, reading and writing of the hard disk
* used as the main storage device in a desktop computer or laptop
* store an operating system, software programs and user-created files
* found in drive bays and are connected to the motherboard via an ATA, SATA, or SCSI cable, and also connected directly to a power supply unit (PSU)
* **Platters**
  * the circular disk on which magnetic data is stored in a HDD
  * hard drives typically have several platters which are mounted on the same spindle
  * can store information on both sides, requiring two heads per platter
* **Sectors**
  * a sector is a subdivision of a track on a magnetic disk or optical disc
  * each sector stores a fixed amount of user-accessible data, traditionally 512 bytes for hard disk drives, while newer HDDs use 4096-byte (4 KiB) sectors
  * sector is the minimum storage unit of a hard drive
  * most disk partitioning schemes are designed to have files occupy an integral number of sectors regardless of the file’s actual size
    * files that do not fill a whole sector will have the remainder of their last sector filled with zeroes
    * operating systems typically operate on blocks of data, which may span multiple sectors
  * nowadays, each physical sector is made up of two basic parts:
    * header area
      * also called ID
      * header may also include an alternate address to be used if the data area is undependable.
    * data area
      * contains the sync bytes, user data, and an error-correcting code (ECC) that is used to check and possibly correct errors that may have been introduced into the data.
* **Clusters**
  * a group of sectors within a disk by which disk files are organized
  * most files fill many clusters of disk space
  * each cluster possesses its own unique ID
* **Slack Space**
  * the leftover storage that exists on a computer’s hard disk drive when a computer file does not need all the space it has been allocated by the operating system
  * should always be examined cause we can find the remaining data from previous files allocated in the same cluster
    * if a user deleted files that filled an entire hard drive cluster, and then saved new files that only filled half of the cluster, the latter half may include leftover information from the deleted files that we can retrieve

---

## Solid State Disk Drive Basics (SSD)

* SSDs are where a lot of digital evidence is stored and collected
* flash-based memory is significantly faster, allowing SSDs to speed up computers significantly because of their low read-access times and fast throughput
* data is written to “pages”, and once there’s enough, it’s written to a “block” on the actual drive

---

* **Garbage collection**
  * background process handled by the SSD controller and the operating system
  * used to optimize space and improve efficiency
  * goal is to keep as many empty blocks as possible so that when the SSD needs to write data, it can do so without waiting for a block to be erased
  * SSD’s controller looks for any pages that are no longer being used
    * deleted data and modified data
  * it then moves used pages to new blocks, leaving behind the data that is no longer needed
  * the controller then erases the block
  * **in forensics**:
    * there’s always the risk that garbage collection will identify the blocks as unwanted, and the controller will erase the blocks in order to free up space
    * if a computer is using SSDs, it needs to be powered off immediately
      * hard shut-down
      * pulling the plug so the power supply unit (PSU)
      * shutting down the system via the OS could execute a malicious script that will destroy data and could ruin an investigation

---

* **Trim**
  * files sent to the Recycle Bin are not immediately deleted; it just tells the OS that the files can be overwritten; deleted files can still be partially recovered
    * deleted file is 174,192 bytes.
    * new file of 121 bytes is written in its place.
    * leaves 174,071 bytes of the deleted file available for recovery.
  * Power the system off with a hard shut-down or pull the plug to prevent files from being overwritten

---

* **Wear Levelling**
  * technique used in SSDs to extend the memory's lifetime
  * performed by the SSD's micro-controller or firmware
  * ensures all physical cells in the SSD receive an equal number of writes to prevent overuse of specific blocks
  * 2 basic algorithms:
    * Dynamic wear leveling
      * blocks that undergo rewriting are repositioned to new blocks
      * algorithm selects an empty block on which to write the data
      * number of writes to each block is tracked by the controller
      * data blocks that are not frequently updated are not moved which can lead to uneven block wear
    * Static wear leveling
      * blocks of static data are moved when their block erase count falls below a certain threshold
      * leads to more effective leveling, enhanced longevity of the device, but slightly slower write performance

---

## File systems

* means of classifying and organizing files and storing data
* used in storage devices such as optical disks and magnetic storage disks
* used to control how data is stored and retrieved on a storage medium
* each FS has a different structure and logic, speed, flexibility, security, size, etc.
* FS is a set of data types used for:
  * Data storage
  * Hierarchical categorization
  * Data management
  * File navigation
  * Accessing the data
  * Recovery of data 

---

* **FAT16**
  * File Allocation Table is the method of using a table to mark the position of files
  * design for small partitions
  * OG FS used in DOS and Windows 3. x
  * if the File Allocation Table is lost or damaged, the data on the hard disk can’t be used because the OS is unable to locate the files

---

* **FAT32**
  * revised version of FAT16
  * can be used to create larger partitions
  * supports long filenames
  * uses 32 bits of data for identifying data clusters on the storage device
  * introduces w/ Win98
  * advantages:
    * compatible with a huge variety of devices
      * smartphones, tablets, computers, digital cameras, gaming consoles, surveillance cameras, etc.
    * cross-compatible with almost all OSs launched since 1995
      * Windows 
        * Windows 95 OSR2, Windows 98, XP, Vista, Windows 7, 8, and 10
      * MacOS
      * Linux
  * disadvantages:
    * only work with files that are less than 4 GB
    * only works with partitions with a maximum capacity of 8 TB
    * no data protection in case of power loss
    * does not include any built-in file compression features
    * not designed to be secure and does not include any built-in encryption features

---

* **NTFS**
  * proprietary journaling FS developed by Microsoft
  * introduced with  Windows NT 3.1
  * the default FS of the Windows NT family
  * has several technical improvements over FAT and High-Performance File System (HPFS)
    * improved support for metadata and advanced data structures to improve performance, reliability, and disk space use
    * more elaborate security system based on access control lists (ACLs) and file system journaling.
  * supported in other desktop and server OSs
    * Linux, BSD
      * have a free and open-source NTFS driver, called NTFS-3G
      * read and write support
    * macOS
      * read-only support for NTFS, but
        * write support disabled by default due to being unstable

---

* **EXT3**
  * Third extended filesystem
  * journaled file system commonly used by the Linux kernel
  * the default file system for many popular Linux distributions
  * changes made in the journal, which is a circular log present in the file system, is monitored by ext3 which is called journaling
  * in a non-journaled filesystem, data recovery and detecting the errors involved more time
    * we may have to go through the entire data structure of the directory 
  * in a journaled filesystem, the journal keeps track of the changes done in the FS
    * to detect the errors or recover data, after a crash, you just need to read the journal instead of processing the whole data structure

---

* **EXT4**
  * Fourth Extended Filesystem
  * maximum volume size of data supported by ext4 is 1exbibyte and file size is up to 16 tebibytes
  * maximum length of the filename is 56 bytes
  * fragmentation in terms of physical blocks where data is stored, is replaced by extents
    * extent is a data storage area that reduces file fragmentation and file scattering
    * increased the performance

---

