```
As a Threat Intelligence Analyst investigating Operation Dream Job, you have identified that the Lazarus Group utilized a variety of custom-built malware and tools to facilitate their operations. Your task is to analyze and gather intelligence on the malware utilized by this APT.
```
# Solve
### S 1
```bash
7z e DreamJob-2.zip
```
> pass: `hacktheblue`

### S 2
##### MITRE ATT&CK
[DRATzarus](https://attack.mitre.org/software/S0694) is a remote access tool (RAT) that has been used by [Lazarus Group](https://attack.mitre.org/groups/G0032) to target the defense and aerospace organizations globally since at least summer 2020. [DRATzarus](https://attack.mitre.org/software/S0694) shares similarities with [Bankshot](https://attack.mitre.org/software/S0239), which was used by [Lazarus Group](https://attack.mitre.org/groups/G0032) in 2017 to target the Turkish financial sector.[1](https://www.clearskysec.com/wp-content/uploads/2020/08/Dream-Job-Campaign.pdf)

### S 3
##### MITRE ATT&CK
Enterprise 	T1622 	Debugger Evasion 	
DRATzarus can use `IsDebuggerPresent` to detect whether a debugger is present on a victim.[1]

### S 4
##### MITRE ATT&CK
[Torisma](https://attack.mitre.org/software/S0678) is a second stage implant designed for specialized monitoring that has been used by [Lazarus Group](https://attack.mitre.org/groups/G0032). [Torisma](https://attack.mitre.org/software/S0678) was discovered during an investigation into the 2020 Operation North Star campaign that targeted the defense sector.[1](https://www.mcafee.com/blogs/other-blogs/mcafee-labs/operation-north-star-behind-the-scenes/)

...
Enterprise 	T1573 	.001 	Encrypted Channel: Symmetric Cryptography 	
Torisma has encrypted its C2 communications using XOR and VEST-32.[1]

### S 5
|   |   |   |   |   |
|---|---|---|---|---|
|Enterprise|[T1027](https://attack.mitre.org/techniques/T1027)|[.002](https://attack.mitre.org/techniques/T1027/002)|[Obfuscated Files or Information](https://attack.mitre.org/techniques/T1027): [Software Packing](https://attack.mitre.org/techniques/T1027/002)|[Torisma](https://attack.mitre.org/software/S0678) has been packed with Iz4 compression.[[1]](https://www.mcafee.com/blogs/other-blogs/mcafee-labs/operation-north-star-behind-the-scenes/)|
|||[.013](https://attack.mitre.org/techniques/T1027/013)|[Obfuscated Files or Information](https://attack.mitre.org/techniques/T1027): [Encrypted/Encoded File](https://attack.mitre.org/techniques/T1027/013)|[Torisma](https://attack.mitre.org/software/S0678) has been Base64 encoded and AES encrypted.[[1]](https://www.mcafee.com/blogs/other-blogs/mcafee-labs/operation-north-star-behind-the-scenes/)|
> LZ4 compression

### S 6 
```bash
7z x DANGER.zip 
```
> Pass in DANGER.txt

### S 7
Upload Iso To https://www.virustotal.com

> https://www.virustotal.com/gui/file/56dabf1ddd5c9a93a6f35dd7f210367baee545296838d321dfea6ee49575c9af/relations

in Relations > Dropped Files
```
2025-12-10 48/ 72 Win32 EXE [InternalViewer.exe](https://www.virustotal.com/gui/file/adce894e3ce69c9822da57196707c7a15acee11319ccc963b84d83c23c3ea802)
```

### S 8
in INTERNALVIEWER.EXE Detaile We can see 

```
Names

- InternalViewer.exe
- INTERNALVIEWER.EXE
- SumatraPDF.exe
- sus.exe
- 38032a4d12d9e3029f00b120200e8e68.virus
```

### S 9
```
History

Creation Time                2020-05-12 19:26:17 UTC
First Seen In The Wild       2020-08-13 08:44:50 UTC
First Submission             2020-06-05 09:20:22 UTC
Last Submission              2025-12-13 05:03:45 UTC
Last Analysis                2025-12-10 11:32:39 UTC
```

### S 10
```
Basic properties

MD5
38032a4d12d9e3029f00b120200e8e68

SHA-1
382bdd11c605882ccb149f0d23707a7ee5f4b89a

SHA-256
adce894e3ce69c9822da57196707c7a15acee11319ccc963b84d83c23c3ea802

Vhash
01703e0f7d60101011z11z47z1015z13z1fz

Authentihash
b3e6feff06e2d9f7ad612ee8bea2d9a44ff08fe853df6c617d4327d86c4627a3

Imphash
38c0cbb9bf97b36d1b93444db348f0cf

Rich PE header hash
7b48cfd5fb55dd3bce52f3cd5b9e93c0

SSDEEP
196608:b/Z/jeANdErYddD7iIvDhXUgCnXAdNxjmrrNLqgCLbfIjvp8jU:b/ZbeAkYfnxvS7wH/IjiU

TLSH
T110B6335F25473176EE5B68B5E31CF9F0954EA4636E8220708E1DEAF280F59C3E6B6103

File type
Win32 EXE
executable
windows
win32
pe
peexe

Magic
PE32+ executable (GUI) x86-64, for MS Windows

TrID
[UPX compressed Win64 Executable (64.7%)](https://www.virustotal.com/gui/)   [UPX compressed Win32 Executable (25%)](https://www.virustotal.com/gui/)   [Win16 NE executable (generic) (4.6%)](https://www.virustotal.com/gui/)   [OS/2 Executable (generic) (1.8%)](https://www.virustotal.com/gui/)   [Generic Win/DOS Executable (1.8%)](https://www.virustotal.com/gui/)

DetectItEasy
[PE64][Packer: UPX (3.96) [NRV,brute]][Compiler: Microsoft Visual C/C++ (19.21.27702) [LTCG/C++]][Linker: Microsoft Linker (14.21.27702)][Tool: Visual Studio (2019 version 16.1)]

Magika
PEBIN

File size
10.02 MB (10507264 bytes)
```
> UPX = Ultimate Packer for eXecutables

### S 11
```bash
strings Salary_Lockheed_Martin_job_opportunities_confidential.doc | grep -o 'http.\{1,\}'
```
#Out 
```
https://markettrendingcenter.com/lk_job_oppor.docx
http://schemas.openxmlformats.org/drawingml/2006/main" bg1="lt1" tx1="dk1" bg2="lt2" tx2="dk2" accent1="accent1" accent2="accent2" accent3="accent3" accent4="accent4" accent5="accent5" accent6="accent6" hlink="hlink" folHlink="folHlink"/>
```

### S 12
```bash
exiftool Salary_Lockheed_Martin_job_opportunities_confidential.doc | grep -o 'Author .\{1,\}'
```
#Out 
```
Author                          : Mickey
```
### S 13
```bash
exiftool Salary_Lockheed_Martin_job_opportunities_confidential.doc | grep -o 'Modified .\{1,\}'
```
#Out 
```
Modified By                : Challenger
```
### S 14
Upload docm To https://www.virustotal.com
https://www.filescan.io/uploads/693d60d4900ee247e8436783/reports/7b0dc22c-3d0c-408d-9b3a-20cc1a339099/details

in File Details > _Extracted files_ We have 
```
File Details

FileMagicDescription: 

PE32 executable (DLL) (GUI) Intel 80386, for MS Windows, UPX com... (71)

Size: 

397.00 kB

Hashes

MD5: 

14d79cd918b4f610c1a6d43cadeeff7b

SHA-1: 

ecd042eabdeae16532b9602be5786e408c3a622d

SHA-256: 

23d73fc8f10588944d8dc2073ce6af6d159943f11ac0c140c9b2e67fb0ad8b89

Imphash:

ae9fc9e8f316d54ccf9679a9b1a52945

Authentihash:

e27858e998d15563df7208f86b7ce7f8... (64)

Ssdeep:

12288:yatQvpCmnfUQbaxUuAtHOFSt9+... (56)

Extended details

Emulation action origin: 

WriteBinaryFile

Entropy: 

8.0

IsEmbedded: 

true

Name: 

%USERPROFILE%\AppData\Local\Microsoft\Notice\wsuser.db
```
> %USERPROFILE%\AppData\Local\Microsoft\Notice\wsuser.db

 