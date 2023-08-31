
---
layout: default
title: Storage Types
parent: Hardware
---
Written by @jheden

# Hard drives
* Hard drives, in short HDDs, use magnetism to store data on spinning platters that are either made of metal or have metal coating
* The two main speeds of the platters in consumer hard drives are 5400 RPM and 7200 RPM.
* We also differentiate two different methods of storing the data on the platters - SMR and CMR
# Solid state drives
* Solid state drives, or as you see them called more often - SSDs, are a newer and much faster type of storage (at least most of them). They utilize transistors in NAND flash to store information
* Similarly to HDDs, they come with different connectors and in different form factors
# USB Flash Drives
* USB flash drives are one of the smaller storage media out there
* They come in variety of sizes and shapes, though nowadays you will usually see a small stick about the length of the pinkie finger and able to store anywhere from 8 up to hundreds of gigabytes
* They, similarly to SSDs, usually use NAND flash, but it tends to be slower, lower quality stuff
# Optical media
* CDs, DVDs and BluRays are disk media that utilize lasers to read and write data on the drive
* CDs can usuall store up to 700 MB, DVDs tent to max out at 4.7 GB and BluRays can store up to 128 GB of data
# Floppy disks and tape
* Old media format that uses magnetism to store data. Similarly to HDDs it has a spinning platter, but here the platter is spun by the floppy drive from the outside
* They come in various formats and sizes with floppies maxing out at 2.88 MB and modern tape media (LTO) maxing out at around 18 TB uncompressed or 45 TB compressed (up to 576/1440 TB LTOs are planned)

## Connectors
### HDDs
* Most common port / interface: SATA
* SATA connector can transfer up to 750 MB/s, Depending on the generation
* Enterprise HDDs often come with a SAS connector that can do up to 2.8ish GB/s. That also necessitates the drive running faster
* Old HDDs used to come with an IDE or a SCSI connector, but we don't talk about that
### SSDs 
* 2 common form factors - 2.5" (with SATA) & M.2 
* Nowadays, the m.2 is taking over in popularity with m.2 SSDs often being cheaper than 2.5" for the same size
* M.2 can support the NVMe protocol (see below) and so they can be a lot faster
### M.2 Keys
 * M.2 SSDs have a gap or gaps in the PCIe m.2 connector. These gaps are called keys. They differ in length and position, and as such have different names.
 * There are 2 main types of keys - M-key and B-key. There is also a combination of both - M+B-key
 * NVMe SSDs come with an M-Key, which means the gap is on the right side of the SSD when the m.2 connector is aiming upwards
 * SATA m.2 SSDs can come either with B-key, but that is pretty unusual, or more commonly with M+B-key.

## Form factors
### HDDs
* HDDs usually come in two form factors nowadays - 2.5", that is used in external HDDs or in older laptops, and 3.5" that is used in desktop PCs. The number signifies the width of the drive
* Older HDDs used for example in iPods or earlier MacBook Airs used 1.8" HDDs
* Modern 2.5" HDDs usually are about 7 mm thick, older about 9 mm thick
### SSDs
* SSDs today come either in the 2.5" form factor or in a special form factor for m.2 SSDs
* The M.2 formfactor is a tiny multi purpose form factor incorporating a PCIe based connector (see Connectors and Keys above)
* Most 2.5" SSDs are about 7 mm thick, though older models can come in the 9 mm thickness
* M.2 SATA SSDs don't differ in physical form factor from NVMe SSDs, but the keys on the connector 
### Optical media
* CDs, DVDs and BluRays are usually 120 mm in diameter, though 200mm and also in their mini variant, which is 80 mm wide
### Floppy disks and tape
* Floppy disks come in 8", 5.25", 3.5", 3" and 2" variants
* Tape storage comes in variety of sizes, though the one that is interesing today is LTO or Linear Tape-Open, which is sized at 102 x 105.4 x 21.5 mm

## Protocols
* SATA HDDs use the AHCI protocol
* In SSDs, the speed can differ greatly based on the protocol used. Todays consumer SSDs most commonly utilize either the NVMe protocol, or AHCI which is a protocol for SATA
* Generally, NVMe SSDs are faster, though there are some really bad ones that are an exception
### RAID
* RAID is a protocol used for combining storage in order to add redundancy to it (thus better data security), to better the performance or a balance of both
* There are various levels of RAID that add varying options for **striping** - aka splitting the data across the drive array - and **mirroring** - making backups of the stored data on the array
* RAID typically requires a special controller for optimal performance, but even consumer boards now often support both RAID and AHCI

# Technologies in SSDs and HDDs
# HDDs
## SMR
 * SMR stands for **S**hingled **M**agnetic **R**ecording. You can imagine the data being stored partially overlaping each other like shingles on a roof
 * Generally cheaper but slower method, used on lower end consumer drives usually
## CMR
 * CMR means **C**onventional **M**agnetic **R**ecording. In this case, the data don't overlap and are written next to each other normally
 * A faster method, usually used in smaller sized consumer drivers or higher end options
## Cache
 * Cache in HDDs is usually a relatively small amount of high speed memory that stores information on where data is located on the drive so it can be found faster. You can imagine it like when you are in a hotel and the front desk person has your name next to the number of your room
# SSDs
## Flash storage
 * SSDs usually use some sort of NAND flash. Today we have 5 main types - SLC, MLC, TLC, QLC, PLC
 * generally the more cells (see below) the NAND flash has, the cheaper, slower in direct writes to the flash and less durable it is
 * today we usually use 3D-NAND (or V-NAND), which means we can stack cells on top of each other for better storage density
### SLC
 * SLC, or single level cell NAND is the fastest variant with the most endurance. It stores one bit of information
### MLC
 * Stores 2 bits in a single cell
### TLC
 * Stores 3 bits per cell, and is probably the most common flash used in SSDs today. It strikes a balance between endurance, speed and price, at least for now
### QLC
 * Stores 4 bits per cell. It is usually used in cheaper SSDs or when manufacturers want to cheap out
### PLC
 * 5 bits per cell. At the moment it is not used in consumer SSDs
## Cache and DRAM, (p)SLC
 * Some SSDs come with DRAM, which, similarly to cache on HDDs, stores sort of a map that helps the SSD quickly locate data the system wants
 * Lack of DRAM impacts speeds on SATA SSDs worse than on NVMe SSDs. That is because NVMe SSDs can take advantage of something called **H**ost **M**emory **B**uffer, or **HMB**
 * HMB is a part of your PCs RAM, usually 64 MB or sometimes 32 MB, that again stores a kind of a map of where data is (L2P Mappings)
### (pseudo)SLC cache
 * Most modern SSDs utilize something called SLC cache. That can either mean they come with a bit of actual SLC NAND to use as cache, or they can convert part of their size and run it as if it was SLC, even despite being TLC or QLC or any other type (that means they will store only 1 bit per cell and leave the rest empty). 
* There are two types of SLC cache - static and dynamic. Static, as the name suggests, doesn't change. It is usually smaller. Dynamic (p)SLC cache can change depending on how full the drive is or sometimes even depending on the workload being put onto the SSD
