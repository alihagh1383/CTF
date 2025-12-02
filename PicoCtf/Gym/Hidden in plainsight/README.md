```

You’re given a seemingly ordinary JPG image. Something is tucked away out of sight inside the file. Your task is to discover the hidden payload and extract the flag. Download the jpg image .

```
[Image](https://challenge-files.picoctf.net/c_amiable_citadel/1b638a2799b26ff08169f1703b4f0f2738599d68ffafe63b8f6ea303b3d596ab/img.jpg)

---
# Solve

#### S 1
> exiftool img.jpg

```
ExifTool Version Number         : 13.36
File Name                       : img.jpg
Directory                       : .
File Size                       : 73 kB
File Modification Date/Time     : 2025:11:07 22:47:40+03:30
File Access Date/Time           : 2025:12:02 15:40:39+03:30
File Inode Change Date/Time     : 2025:12:02 15:40:38+03:30
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Comment                         : <Base64 Text>
Image Width                     : 640
Image Height                    : 640
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 640x640
Megapixels                      : 0.410
```

#### S 2
> echo `<Base64 Text>` | base64 --decode

```
steghide: <Base64 Text>
```

#### S 3
> echo `<Base64 Text>` | base64 --decode

```
 <Password>
```

#### S 4
> steghide extract -sf "img.jpg" -p `<Password>`

*Save flag.txt*

 #### S 5
> cat flag.txt

```
picoCTF{<Flag>}
```