# office2hashcat

The goal of this script is to make it very easy to convert
Password-protected Microsoft Office Files to so-called "hashes"
which hashcat can crack.

hashcat mode
------------

| MODE | DESCRIPTION                                     |
| ---- | ----------------------------------------------- |
| 9400 | MS Office 2007                                  |
| 9500 | MS Office 2010                                  |
| 9600 | MS Office 2013                                  |
|25300 | MS Office 2016 - SheetProtection                |
| 9700 | MS Office <= 2003 $0/$1, MD5 + RC4              |
| 9710 | MS Office <= 2003 $0/$1, MD5 + RC4, collider #1 |
| 9720 | MS Office <= 2003 $0/$1, MD5 + RC4, collider #2 |
| 9810 | MS Office <= 2003 $3, SHA1 + RC4, collider #1   |
| 9820 | MS Office <= 2003 $3, SHA1 + RC4, collider #2   |
| 9800 | MS Office <= 2003 $3/$4, SHA1 + RC4             |

Use the following command to view supported modes:

```sh
hashcat --help | grep -i office
```

usage
-----

```sh
office2hashcat.py dummy.docx | tee dummy.docx.hashcat
hashcat -m $MODE -a 0 dummy.docx.hashcat wordlist.txt
```
