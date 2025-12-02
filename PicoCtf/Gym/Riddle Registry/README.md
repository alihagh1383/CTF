**Forensics**
```
Hi, intrepid investigator! 📄🔍 You've stumbled upon a peculiar PDF filled with what seems like nothing more than garbled nonsense. But beware! Not everything is as it appears. Amidst the chaos lies a hidden treasure—an elusive flag waiting to be uncovered. Find the PDF file here Hidden Confidential Document and uncover the flag within the metadata.

```
[Hidden Confidential Document](confidential.pdf)

---
# Solve
#### S 1
> pdfinfo confidential.pdf 
 
```
Author:          <Base64 Text>
Producer:        PyPDF2
Custom Metadata: no
Metadata Stream: no
Tagged:          no
UserProperties:  no
Suspects:        no
Form:            none
JavaScript:      no
Pages:           1
Encrypted:       no
Page size:       612 x 792 pts (letter)
Page rot:        0
File size:       182705 bytes
Optimized:       no
PDF version:     1.7
```
#### S 2
> echo `<Base64 Text>` | base64 --decode

```
picoCTF{<Flag>}
```

# Finish
