# perl_script

stupid little scripts.


## mailsend.pl

simple mail sender.

```
mailsend.pl [-debug] [-from] [-to] [-subject] [-message] [files ...]
  -debug   ... not send
  -from    ... email address
  -to      ... email address
  -subject ... subject string
  -message ... sjis textfile for mailbody
  files    ... attach files
```



## texttable.pl

a command-line tool convert TSV into ascii-text-table.

```
texttable.pl [options] file
    -d,   --delim=s   field Delimiter
    -t,   --title     divide first line as Title
    -r,   --right     Right Align
    -n,   --noline    No line
```

```
$ cat a.tsv.txt
Name OS Since
alice MacOS 2013/11/01
bob Windows 2012/03/03
john Linux 2001/07/01

$ texttable.pl -t a.tsv.txt
+-------+---------+------------+
| Name  | OS      | Since      |
+-------+---------+------------+
| alice | MacOS   | 2013/11/01 |
| bob   | Windows | 2012/03/03 |
| john  | Linux   | 2001/07/01 |
+-------+---------+------------+
```



## caesar.pl

print caesar cipher.

```
$ perl caesar.pl cqrbrbrc
00: CQRBRBRC
01: DRSCSCSD
02: ESTDTDTE
03: FTUEUEUF
04: GUVFVFVG
05: HVWGWGWH
06: IWXHXHXI
07: JXYIYIYJ
08: KYZJZJZK
09: LZAKAKAL
10: MABLBLBM
11: NBCMCMCN
12: OCDNDNDO
13: PDEOEOEP
14: QEFPFPFQ
15: RFGQGQGR
16: SGHRHRHS
17: THISISIT
18: UIJTJTJU
19: VJKUKUKV
20: WKLVLVLW
21: XLMWMWMX
22: YMNXNXNY
23: ZNOYOYOZ
24: AOPZPZPA
25: BPQAQAQB
```


