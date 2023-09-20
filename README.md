<h1>Forensic Image Conversion and Analysis</h1>


<h2>Description</h2>
This project involves a comprehensive exercise in forensic image conversion and analysis using tools like FTK Imager and WinHex. I delve deep into the technicalities of forensic imaging and analysis which is a critical skill in the field of digital forensics. This hands-on project is structured into several sections which that go through various tasks including forensic image conversion, working with alternate data streams (ADS), and parsing Master File Table (MFT) records. It includes the following tasks:
<br />
<br />
- <b>Forensic Image Conversion using FTK Imager</b> 
<br />
- <b>Working with Alternate Data Streams</b>
<br />
- <b>Parsing MFT Records</b>
<br />


<h2>Software and Utilities Used</h2>
- <b>FAT32-formatted device</b>
<br />
- <b>FTK Imager</b>
<br />
- <b>WinHex</b>
<br />
- <b>MFT Stampede</b>

<h2>Environments Used </h2>
- <b>Windows 10 Pro</b>


<h2>Lab Walkthrough</h2>
<h3>Forensic	Image	Conversion	using	FTK	Imager</h3>
<p align="center">

On FTK Imager, select create disk image <br/>
<img src="https://i.imgur.com/4tFE89F.png" height="80%" width="80%" alt="Log into Windows"/>
<br />
<br />
Select image file as source evidence type<br/>
<img src="https://i.imgur.com/Ec8uGji.png" height="80%" width="80%" alt="Investigate FAT32"/>
<br />
<br />
Enter the path of the source image file<br/>
<img src="https://i.imgur.com/noG809v.png" height="80%" width="80%" alt="check quota and security tabs"/>
<br />
<br />
Check the option to “Verify images after they are created”, “Precalculate Progress Statistics”, and
“Create directory listings of all files in the image after they are created”.<br/>
<img src="https://i.imgur.com/bzrMycj.png" height="80%" width="80%" alt="check quota and security tabs"/>
<br />
<br />
Add an image destination, select E01 as the format, and fill out the corresponding information like case number, description, examiner.<br/>
<img src="https://i.imgur.com/tv1myV4.png" height="80%" width="80%" alt="hide file using ADS"/>
<br />
<br />
Give it a name and select the path it will be stored. Split the image into 10 MB chunks using a compression level of “1”. Do not use AD Encryption.<br/>
<img src="https://i.imgur.com/ON05HVK.png" height="80%" width="80%" alt="check ads"/>
<br />
<br />
Analyze the image by answering the following questions:
<br />
<br />
(We look under image properties for the first 5 questions)
<img src="https://i.imgur.com/eNJutxZ.png" height="80%" width="80%" alt="check ads"/>
<br />
<br />
1 - How many E01 segments were created during the image conversion?
<br />
<br />
3 Segments
<br />
<br />
2 - What is the total file size in bytes of the raw forensic image?
<br />
<br />
2147483650 bytes
<br />
<br />
3 - According to the imaging log, how many sectors were located in the raw image?
<br />
<br />
4,194,304 sectors
<br />
<br />
4 - What is calculated MD5 hash value of the raw image?
<br />
<br />
d9361d55e6c5aa4e915767e17a455d62
<br />
<br />
5 - What is the calculated SHA1 hash value for image verification (i.e., the SHA1 hash value
of the E01 image)?
<br />
<br />
b9f5fbc22627907a0f868d2a6950e3d40e9954c7
<br />
<br />
6 - According to the directory listing, how many deleted files are present in the forensic
image?
<br />
<br />
A total of 42 files of different sizes can be found on the [unalocated space] folder on the partition, which are likely fragments of deleted files.
<img src="https://i.imgur.com/EgB49ik.png" height="80%" width="80%" alt="check ads"/>
<br />
<br />
7 - According to the directory listing, what is the file size in bytes of the largest .log file on
the forensic image?
<br />
<br />
It seems that CBS.log under the CBS folder is the largest .log file on the image.
<img src="https://i.imgur.com/Z6GqV2r.png" height="80%" width="80%" alt="check ads"/>
<br />
<br />
8 - According to the directory listing, how many .JPG images are stored on the forensic
image?
<img src="https://i.imgur.com/BmxmblF.png" height="50%" width="50%" alt="check ads"/>
<img src="https://i.imgur.com/52p2U8N.png" height="50%" width="50%" alt="check ads"/>
<br />
<br />
It seems that there's a total of 5 .JPG images
<br />
<br />
<h3>Working with Alternate Data Streams</h3>

On an NTFS formatted drive (such as the C:\ drive) and using Notepad, create a text file and
name it “Project1” (do not insert any text into the file). <br/>
<img src="https://i.imgur.com/wYUPKM0.png" height="80%" width="80%" alt="dir /r"/>
<br />
<br />
Create an alternate (additional) data stream for the project1 using the command line and name “ads.txt”. Insert your last
name as the only text within the alternate data stream. <br/>
<img src="https://i.imgur.com/Hm8ci4F.png" height="80%" width="80%" alt="dir /r"/>
<br />
<br />
Verify that the ADS has been created properly by typing “notepad project1.txt:ads.txt” at the command line <br/>
<img src="https://i.imgur.com/BMnibZH.png" height="80%" width="80%" alt="analyze first partition"/>
<br />
<br />
Answer the following questions regarding the ADS:
<br />
<br />
1 - Check the size of the project1.txt file in Windows (right click on the file, select
Properties). What is the size of the file displayed in the Windows Properties?
<br />
<br />
0 bytes
<br />
<br />
2 - Open the NTFS drive you're working with as a physical device in WinHex and locate the
MFT record that corresponds with the “Project 1.txt” file you created (right click on the
file à Navigation àGo to FILE Record). Based on examination at the hexadecimal level,
how can you determine that this file has an alternate data stream?
Open drive C in WinHex
<img src="https://i.imgur.com/y9sRV6W.png" height="80%" width="80%" alt="analyze next 3 partitions"/>
<br />
<br />
Navigate to the location where "Project 1.txt" is saved, right-click on it, and select "Navigation" followed by "Seek FILE Record" to access its MFT record.
<br />
<img src="https://i.imgur.com/R1oVdJb.png" height="80%" width="80%" alt="analyze next 3 partitions"/>
<br />
<br />
Analyze the attributes for the MFT record by looking at the hex values, notice there is a second $DATA attribute (signature of 80 00 00 00).
<img src="https://i.imgur.com/1k7OxyZ.png" height="80%" width="80%" alt="analyze next 3 partitions"/>
<br />
We can determine the file has an ADS because it has a second $DATA attribute on its MFT record, for which we can see the name "ads.txt" on the ASCII translation ob the right
<br />

3- Attempt to copy Project1.txt to a FAT32 formatted device. When you tried to copy the file, what happened? Why did this happen?
<br />
<br />
<img src="https://i.imgur.com/Fg72m8q.png" height="80%" width="80%" alt="analyze next 3 partitions"/>
<br />
Windows warns you that the file can be copied but there are "properties" that won't be copied, this is referring to the ADS, because the FAT32 does not support ADS.
<br />
<br />
<h3>Working with Alternate Data Streams</h3>
On WinHex open the MFT Record file <br/>
<img src="https://i.imgur.com/C9Kikec.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
<br />
Answer the following questions regarding the MFT record:
<br />
<br />
1 -What is the type and allocation status of this item?
<br />
<br />
Offsets 22 and 23 (decimal) have the flag "01 00" meaning it's a file and it is alocated.
<img src="https://i.imgur.com/C9Kikec.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
<br />
<br />
2 - What is the MFT record number (decimal value) of this file/directory?
<br />
<br />
The record number can be found on offsets 44-47 (decimal) and it includes 4 values, it is stored in little endian so we must reverse it before we use a hex calculator to convert it to decimal, the result is 126438.
<img src="https://i.imgur.com/ZtGDPKa.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
<br />
To answer questions 3-6, find the identifier 10 00 00 00 for the standard attribute and parse the values using MFT Stampede (remember to reverse it given the little endian format)
<img src="https://i.imgur.com/t1LzAAJ.png" height="50%" width="50%" alt="log into Kali Linux"/>
<img src="https://i.imgur.com/gBGeQlm.png" height="50%" width="50%" alt="log into Kali Linux"/>
<br />
<br />
3 - What is the creation timestamp in the $STANDARD_INFORMATION attribute?
<br />
<br />
Fri, 30 Oct 2020 19:23:02
<br />
<br />
4 - What is the modified timestamp in the $STANDARD_INFORMATION attribute?
<br />
<br />
Fri, 30 Oct 2020 19:23:03
<br />
<br />
5 - What is the record update timestamp in the $STANDARD_INFORMATION attribute?
<br />
<br />
Fri, 30 Oct 2020 19:23:03
<br />
<br />
6 - What is the accessed timestamp in the $STANDARD_INFORMATION attribute?
<br />
<br />
Fri, 30 Oct 2020 19:23:06
<br />
<br />
7 - What is the name of this file/directory?
<br />
Find the identifier 30 00 00 00 for the $FILENAME attribute
<img src="https://i.imgur.com/dOrdNTc.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
Find the value that represents the file name, the ASCII translation on the right will help identify it
<img src="https://i.imgur.com/dOrdNTc.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
The file name is WorkingFile.zip
<br />
<br />
8 - How many timestamps are included in this MFT Record?
<br />
<br />
8 Time Stamps total across the $STANDARD_INFORMATION AND $FILENAME attributes
<br />
<br />
9 - What is the starting cluster of this file/directory? What is the run length of the first data run?
<br />
<br />
Find the identifier 80 00 00 00 for the $DATA attribute
<img src="https://i.imgur.com/20T6qc0.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
Find the resident flag, this one has a value of 01, meaning it is non-resident
<img src="https://i.imgur.com/bxeERUA.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
On the non-resident header, find the 2 byte offset to dataruns value, convert it to decimal (remember it's in little endian) and count that number from the start of the $DATA attribute, the first data run will start there
<img src="https://i.imgur.com/itBnFUA.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
Parse the data run to find the run length of the data run and the starting cluster of the file
<img src="https://i.imgur.com/yZY1EN5.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
The starting cluster for this file is 13745615.
<br />
The run length of the first data run is 15.
<br />
<br />
10 - How many $DATA (0x80) attributes does this file/directory have?
<br />
<br />
This file has a total of 3 $DATA attributes.
<br />
<br />
11 - What is the MFT record number for the parent of this file/directory?
<br />
Find the record number reference of parent directory and convert it to decimal (remember the little endian format)
<img src="https://i.imgur.com/sf7nblp.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
The record number of the parent directory is 103054.
<br />
12 - Is this file/directory fragmented? How do you know?
<br />
Use the run length from question 9 to find the second data run.
<img src="https://i.imgur.com/QcGOuRI.png" height="80%" width="80%" alt="log into Kali Linux"/>
<br />
We know the file is fragmented because it has multiple data runs.
<br />
<br />

<h2>Conclusion </h2>
This project embarked on a meticulous journey through the intricacies of forensic image conversion and analysis, establishing a potent framework for delving deep into the realms of digital forensics. Here are the significant takeaways and conclusions drawn from this endeavor:

<b>Comprehensive Skill Development:</b> The project facilitated a deep understanding and skill development in forensic image analysis, an essential skill in the contemporary digital forensics domain. This was significantly aided by hands-on experience with tools like FTK Imager and WinHex.

<b>Hands-On Experience with ADS:</b> Working with Alternate Data Streams (ADS) proved to be an enlightening experience, offering insights into the hidden layers of file systems and how they can be utilized for forensic analysis.

<b>Deep Dive into MFT Records:</b> Parsing Master File Table (MFT) records was a challenging yet rewarding task, unveiling the deep-seated data structures and timestamps that are essential in forensic investigations. The MFT Stampede was particularly useful in this regard.

<b>Practical Application of Concepts:</b> The project not only imparted theoretical knowledge but also emphasized practical applications, providing a real-time simulation of forensic analysis processes. This will undoubtedly prove invaluable in real-world forensic analyses.

<b>Understanding File System Properties:</b> The project threw light on the nuanced differences between various file systems like NTFS and FAT32, particularly concerning features like ADS, helping in grasping the broader picture in digital forensic analysis.

<b>Enhanced Proficiency with Forensic Tools:</b> Through the series of tasks undertaken during this project, there was a noticeable enhancement in proficiency with using digital forensic tools and utilities, setting a strong foundation for future endeavors in the field.

<b>Preparation for Advanced Analysis:</b> This project served as an excellent precursor to more advanced analyses in the realm of digital forensics, paving the way for deeper exploration and research in this rapidly evolving field.

<b>Visual Engagement:</b> The addition of visual aids in the walkthrough provided a visual, immersive learning experience, allowing for a more straightforward and practical approach to understanding the concepts at hand.
