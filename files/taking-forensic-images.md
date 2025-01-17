# Taking Forensic Images

* Forensic images should be taken of the hard drives of affected systems, and also memory dumps to capture any artifacts that may be in RAM
* In some cases, the forensic image of the drive may be stored on a USB so that multiple analysts can analyze it, and make it easier to store, as opposed to only having one copy on a forensic laptop or workstation
* **FTK Imager and KAPE**
  * an incident responder with digital forensics skills would gain access to the affected system or systems, and use KAPE to quickly collect evidence from volatile locations such as RAM
  * Hard drives would then be connected to a hardware write-blocker, which is connected to a forensic laptop or workstation
    * allows the forensic analyst to take a bit-by-bit copy of the hard drive without their device altering anything on the suspect drive
  * Hashes will be compared between the original drive and the disk image to ensure that they are exactly the same
  * The newly-generated disk image will then be copied, and the original will be placed into secure storage
  * The forensics analysts will then collect evidence

---

* **Virtual Desktops**
  * take a snapshot of the virtual system
  * mount this snapshot in another virtual machine designed with forensics in mind, such as Sift
  * take a disk image of the mounted snapshot