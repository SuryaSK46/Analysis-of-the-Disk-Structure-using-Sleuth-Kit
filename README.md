# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls.exe C:\forensics\disk.dd

# Step 2: View file system details
fsstat.exe -o 2048 C:\forensics\disk.dd

# Step 3: List files
fls.exe -r -o 2048 C:\forensics\disk.dd

# Step 4: Recover a file
icat.exe -o 2048 C:\forensics\disk.dd 6 > C:\forensics\image.jpg
```
## OUTPUT:
Disk Structure Analysis Results

<img width="1105" height="285" alt="478741038-14310d1d-0168-4429-940a-0b052167033c" src="https://github.com/user-attachments/assets/f5447528-427c-48b5-967f-43d26c07faee" />

Create Disk

<img width="1086" height="512" alt="478741044-a82a5510-7348-4a2c-8ad0-b3f4e22dbf6f" src="https://github.com/user-attachments/assets/4c46e85c-2505-45fb-897a-cdb1ffbc134f" />

mmls mmls disk.dd

fls fls -f fat -o 0 disk.dd

<img width="636" height="285" alt="image" src="https://github.com/user-attachments/assets/6cf3756a-d6bf-4002-bf3f-0a04f33808a0" />

<img width="979" height="639" alt="image" src="https://github.com/user-attachments/assets/eb194f48-0a64-4618-9b12-562efa0289a2" />

<img width="706" height="293" alt="image" src="https://github.com/user-attachments/assets/908df980-6c9b-4254-b901-bb6ddb1711a2" />

<img width="627" height="465" alt="image" src="https://github.com/user-attachments/assets/500a2069-fd59-4014-9cdf-0aef983aa3c3" />


## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
