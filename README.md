## Office password decryptor

Usage:
-----------------------------------------

1. Download [hashcat](https://hashcat.net/hashcat/). Download the binary file and unzip it.
2. Download [office2john.py](https://github.com/openwall/john/blob/bleeding-jumbo/run/office2john.py).
3. Run the following command in the terminal:
```bash
python office2john.py Demo.xlsx > hash
```
4. Open hash and save it in ANSI format, e.g.
```ANSL
$office$*2007*20*128*16*91660773a2b016a40d772a940cbd26e5*c52ac3aa23e39c8ebdc03b6a9288ecdc*88196542506ec10996acdc6659d01c6601464b7d
```
5. Run the following command in the terminal (password is consist of only numbers, from 1 to 999999):
```bash
Hashcat -m 9400 ../hash.txt -a 3 --increment --increment-min 1 --increment-max 6 ?d?d?d?d?d?d --self-test-disable --show
```
6. Parameter selection.
```
Office97-03(MD5+RC4,oldoffice$0,oldoffice$1)：-m 9700
Office97-03($0/$1, MD5 + RC4, collider #1)：-m 9710
Office97-03($0/$1, MD5 + RC4, collider #2)：-m 9720
Office97-03($3/$4, SHA1 + RC4)：-m 9800
Office97-03($3, SHA1 + RC4, collider #1)：-m9810
Office97-03($3, SHA1 + RC4, collider #2)：-m9820
Office2007：-m 9400
Office2010：-m 9500
Office2013：-m 9600

?l = abcdefghijklmnopqrstuvwxyz, lowercase.
?u = ABCDEFGHIJKLMNOPQRSTUVWXYZ, uppercase.
?d = 0123456789, numbers.
?s = !"#$%&'()*+,-./:;<=>?@[]^_`{|}~, symbols.
?a = ?l?u?d?s, all.
?b = 0x00 - 0xff, all.
```

References:
-----------------------------------------
https://zxacn.com/articles/2019/08/02/1564729501559.html

https://github.com/openwall/john
