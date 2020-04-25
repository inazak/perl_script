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


## cartesian.pl

print cartesian product.

```
# $ perl cartesian.pl 1,2 3 4,5
# 1 3 4
# 1 3 5
# 2 3 4
# 2 3 5
```


## merge.pl

merge two files using a key. key is the string before tab for each line.

```
$ cat a.txt
001     AAAA
002     BBBB
003     CCCC
004     DDDD
005     EEEE
$ cat b.txt
001     XXX
003     YYY
005     ZZZ
$ perl merge.pl a.txt b.txt
001     AAAA    XXX
002     BBBB
003     CCCC    YYY
004     DDDD
005     EEEE    ZZZ
```


## pingb.pl

run ping in background.

```
pingb.pl [options]        ipaddress_or_hostname  (foreground)
pingb.pl [options] --exec ipaddress_or_hostname  (background)


Options:

  -i, --interval n  time to wait interval for ping, in second
                    default is 10 sec

  -d, --days n      number of days to continue
                    default is 7 days

  -h, --help        display this help


example below is performed `ping` every 5 second for 3 days.
  ./pingb.pl -i 5 -d 3 localhost

example below is performed `ping` background.
logfile is recorded in /tmp/YYYYMMDD-hhmmss_hostname_pingb.log .
  ./pingb.pl --exec localhost
```

current pingb use below command pipeline.

```
ping -W 1 -q -c 3 $host |\
  awk -F'/' 'END{ print (/^rtt/? "ok "$6" ms":"NG") }' |\
  xargs -I_ date +"%c $host _"

```



## lift1.pl

move folder in subfolder to current folder. this script works on *windows only*.

```
  there is no option, no argument.
  
  $ lift1.pl

  For example, if the folder structure is as follows,

  current/ ---+-- a/ ---+--- 001/
              |         +--- 002/
              |         +--- 003/
              |
              +-- b/ ---+--- 004/
                        +--- 005/

  The result is as follows.

  current/ ---+--- 001/
              +--- 002/
              +--- 003/
              +--- 004/
              +--- 005/
```


## rip1.pl

move files in subfolder to current folder.
this script works on *windows only*.

```
  there is no option, no argument.
  
  $ rip1.pl

  For example, if the folder structure is as follows,

  current/ ---+-- a/ ---+--- 001.jpg
              |         +--- 002.jpg
              |         +--- 003.jpg
              |
              +-- b/ ---+--- 004.jpg
                        +--- 005.jpg

  The result is as follows.

  current/ ---+--- a___001.jpg
              +--- a___002.jpg
              +--- a___003.jpg
              +--- b___004.jpg
              +--- b___005.jpg
```

failsafe interruption works if the target
file is not one of the following.

```
jpg|jpeg|png|bmp|tiff|txt|zip|rar|lnk|url|mp3|pdf
```


