---
title: 'File and Memory Forensics'
description: 'File Signatures, Metadata and Memory'
category: 'Forensics'
order: 1
---

## Forensics YAY!

Hey, ever wondered what really happens when you hit "Delete"? (Spoiler: it's almost never actually gone).
The art of recovering the digital trail left on a computer. There are plenty of methods to find data which is seemingly deleted, not stored, or worse, covertly recorded.

**Metadata**, often described as data about data, helps in understanding the history of a particular electronic file, including when the file was created, modified and accessed, among other information that can be used to describe the file.

[**File signatures**](https://en.wikipedia.org/wiki/List_of_file_signatures), or **magic numbers/header**, are unique byte sequences at the start of files that identify their format or type. They allow systems to recognize file types reliably, independent of file extensions.
For example, PDFs start with `25 50 44 46 2D`, and JPEGs start with `FF D8`. Magic numbers are essential for file verification, security, and data recovery.

---

### Tools

#### File & Hex Analysis
* `file`: used to determine file type
* `strings`: print the strings of printable characters in files
* `binwalk`: analyze, reverse engineer, and extract firmware images
* `xxd`: creates a hex dump of a given file or standard input; can also convert a hex dump back to its original binary form
* Hexeditor (alternatively [hexed.it](https://hexed.it/)): used to read and edit the actual data in files, particularly the file headers
* `exiftool`: used to read and write meta information in files

#### Steganography

Now we come onto [Steganography](https://ctf101.org/forensics/what-is-stegonagraphy/). Read about LSB stego too here.

* `steghide`: hide data in various kinds of images
* `stegseek`: fast steghide cracker that can be used to extract hidden data from files
* `zsteg`: PNG/BMP analysis
* `stegsolve`: used to analyze images in different planes by taking off bits of the image
* `ImageMagick`: "a free, open-source software suite, used for editing and manipulating digital images"
* `pngcheck`: get details on a PNG file (or find out if it is actually something else)
* `wavsteg`: python3 tool that can hide data and files in wav files and can also extract data from wav files
* `foremost`: carve and recover embedded or deleted files
* `Audacity`: analyze sound files (mp3, m4a, whatever)
* `Stegsnow`: program for concealing messages in text files by appending tabs and spaces on the end of lines, and for extracting messages from files containing hidden messages
* `gimp`: a tool for editing images
* [Forensically](https://29a.ch/photo-forensics/#forensic-magnifier)

---

### Challenges & Examples: SET A (File / Stego)

* RootMe [stego](https://www.root-me.org/en/Challenges/Steganography/)
* [Challenge 1](https://play.picoctf.org/practice/challenge/186?page=1&search=infor)
* [Challenge 2](https://play.picoctf.org/practice/challenge/423?category=4&page=1)
* [Challenge 3](https://drive.google.com/file/d/1kMcD5pWWbzCcz2kBA8ny5XKcsU1tEOk0/view?usp=sharing)
* [Example 1](https://kamransaifullah.medium.com/milkshake-stenography-challenge-solution-de046379bff5)
* [Example 2](https://noob-atbash.github.io/CTF-writeups/nahamcon-20/stego/stego.html)
* Try from [PicoCTF](https://play.picoctf.org/practice?category=4&page=1)

---

## Memory Forensics (DFIR: Digital Forensics and Incident Response)

DFIR covers disk and memory forensics, timeline reconstruction, registry analysis, artifact extraction, and incident reporting.

### Core Tools & Frameworks
* Volatility 2
* Volatility 3
* Autopsy/Sleuth Kit
* FTK Imager

### Volatility 2 vs Volatility 3

* Volatility 3 is Python 3 native; Volatility 2 historically used Python 2.
* Plugin architectures differ; many plugins reworked in v3.
* v3 has updated parsers and active development; v2 has many mature community plugins and writeups.
* Performance and cross-platform improvements exist in v3, but some v2 plugins may not have direct equivalents.
* Volatility 2 has some functionality not in v3, like clipboard content.

Volatility [cheatsheet](https://blog.onfvp.com/post/volatility-cheatsheet/)

### Challenges & Examples: SET B (Volatility)

* [Example 1](https://blog.pentesteracademy.com/analyzing-memory-dump-with-volatility-ii-cec8ede91706)
* [Challenge 1](https://cyberdefenders.org/blueteam-ctf-challenges/redline/)
* [Challenge 2](https://cyberdefenders.org/blueteam-ctf-challenges/brave/)

### Challenges & Examples: SET C (DFIR)

* [CyberDefenders](https://cyberdefenders.org/)
* [Challenge 1](https://cyberdefenders.org/blueteam-ctf-challenges/oski/)
* [Challenge 2](https://cyberdefenders.org/blueteam-ctf-challenges/webstrike/)
* [Challenge 3](https://cyberdefenders.org/blueteam-ctf-challenges/yellow-rat/)

### Other Resources

* CTF101 Memory forensics [here](https://ctf101.org/forensics/what-is-memory-forensics/)
* [Memlabs](https://github.com/stuxnet999/MemLabs): used by *bi0s* as part of their DFIR training, great starter resource
* [Malware & DFIR series](https://azr43lkn1ght.github.io/Malware%20Development,%20Analysis%20and%20DFIR%20Series%20-%20Part%20I%2f) by *bi0s*
* [VirusTotal](https://www.virustotal.com/gui/home/upload)

---

### Sources
* https://pclub.in/roadmap/2024/06/06/infosec-roadmap/
* https://github.com/Cryptonite-MIT/dfir-gita