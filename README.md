# devops-linux

## Bandit Level 1 → Level 2

**Challenge:** Read the contents of a filled called "-"

**Solution:**
```bash
ls . 
cat . 
exit .
```

**Explanation:**
- `ls` . list files in the directory
- `cat` . to read the contents of a file without opening 
- `exit` . terminates a SSH connection

**Password:**  6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR

**What I learned:** The `exit` command is used to terminate a SSH connection.

## Bandit Level 2 → Level 3

**Challenge:** Find the password in a file located in the home directory

**Solution:**
```bash
cat ./"--spaces in this filename--"
```

**Explanation:**
- `cat` . to read the contents of a file without opening 
- `./` . refers to the relative filepath

**Password:** PK8fYLZg2hnHSz83plBL1iEPKdD3QToB

**What I learned:** "./" refers to the relative path.

## Bandit Level 3 → Level 4

**Challenge:** Find the password in a hidden file located in the inhere directory

**Solution:**
```bash
cat ./"--Hiding-From-You--"
```

**Explanation:**
- `cat` . to read the contents of a file without opening 
- `./` . refers to the relative filepath

**Password:** 7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME

## Bandit Level 4 → Level 5

**Challenge:** Find the password in a human-readable file in the inhere directory.

**Solution:**
```bash
find -type f -size 1033c ! -executable
cat . 
exit .
```

**Explanation:**
- `find -type f -size 1033c ! -executable` . Finds files that are regular, filters by exact byte size and excludes executable files.

**Password:**  xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq

**What I learned:** '!' refers to is not.


## Bandit Level 5 → Level 6

**Challenge:** Find a file with these properties:
- Human-readable
- 1033 bytes in size
- Not executable
- 
**Solution:**
```bash
find -type f bandit7 -group bandit6 -size 33c 2>/dev/null
```

**Explanation:**
- `find -type f bandit7 -group bandit6 -size 33c 2>/dev/null` . This command searches the bandit7 directory for regular files that are owned by the group bandit6 and are exactly 33 bytes in size, while suppressing any error messages from appearing on the screen

**Password:**  6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG

**What I learned:** `2>/dev/null` simply sends all error messages to dev/null which is similar to a bustbin. 

## Bandit Level 5 → Level 6

**Challenge:** Find the password in a long txt file

**Solution:**
```bash
grep "millionth" data.txt
```

**Explanation:**
- `grep "millionth" data.txt` . Find the text "millionth" in the txt file

**Password:**  pXa26xhMWaC2SvDotA4r9EgZkulOeSBW

**What I learned:** grep is used to search for contents within a file whereas find is used to search for a specific filename, directory, filesize or permissions.

## Bandit Level 6 → Level 7

**Challenge:** Find the password that only occurs once

**Solution:**
```bash
sort data.txt | uniq -u
```

**Explanation:**
- `sort data.txt | uniq -u` . Find the text that only appears once.

**Password:**  Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3

**What I learned:** the -u argument specifies that the output should be unique.

## Bandit Level 7 → Level 8

**Challenge:** Find the password with human-readable strings, preceded by several '=' characters

**Solution:**
```bash
grep -a "=" data.txt
```

**Explanation:**
- `grep -a "=" data.txt` . Find the text that only appears once.

**Password:**  VR1ljMayciFxbnUokuQmJFw6QC9VKtub

**What I learned:** The "-a" argument tells grep to process a binary file as if it were plaintext.

## Bandit Level 8 → Level 9

**Challenge:** Find the password with human-readable strings, preceded by several '=' characters

**Solution:**
```bash
grep -a "=" data.txt
strings data.txt
```
**Explanation:**
- `grep -a "=" data.txt` . Find the text that only appears once.
- `strings data.txt` . Used this command to retrieve the password.

**Password:**  VR1ljMayciFxbnUokuQmJFw6QC9VKtub

**What I learned:** The "-a" argument tells grep to process a binary file as if it were plaintext.

## Bandit Level 9 → Level 10

**Challenge:** Find the password which is stored in an encrypted txt file.

**Solution:**
```bash
base64 -d data.txt

```
**Explanation:**
- `base64 -d data.txt` . This command decrypts the data.

**Password:**  EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl

**What I learned:** The argument "-d" decrypts the data.

## Bandit Level 10 → Level 11

**Challenge:** Find the password which is stored in a txt file where the letters have been rotated by 13 positions.

**Solution:**
```bash
tr 'A-ZA-z' 'N-ZA-Mn-za-m' < data.txt
```
**Explanation:**
- 'A-ZA-z' 'N-ZA-Mn-za-m' < data.txt . Perform a substitution cipher and read from data.txt.

**Password:**  B0s2khmbT9u0geKuOoVGW3JZKhndE3BG

**What I learned:** the "tr" command is short for translate.

## Bandit Level 11 → Level 12

**Challenge:** Retrieve the password form a file that has been substituted.

**Solution:**
```bash
A-ZA-z' 'N-ZA-Mn-za-m' < data.txt
```
**Explanation:**
- 'A-ZA-z' 'N-ZA-Mn-za-m' < data.txt . Perform a substitution cipher and read from data.txt.

**Password:**  pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro

**What I learned:** ROTI13 is a substitution cipher. 
 


## Bandit Level 12 → Level 13

**Challenge:** Retrieve the password form a file that has been repeatedly compressed.
**Solution:**
```bash
- mktemp -d
- cd /tmp/tmp.y2GILdTC6e
- cp /home/bandit12/data.txt /tmp/tmp.y2GILdTC6e
- mv /tmp/tmp.y2GILdTC6e/data.txt /tmp/tmp.y2GILdTC6e/data1.txt
- file data1.txt
- xxd -r data1.txt>data1
- file data1
- mv data1 data1.gz
- gzip -d data.gz
- file data1
- mv data1 data1.gz
- gzip -d data1.gz
- file data1
- mv data1 data1.bz2
- bzip2 -d data1.bz2
- file data1
- mv data1 data1.gz
- gzip -d data1.gz
- file data 1
- tar -xf data1
- file data1
- file data5.bin
- tar -xf data5.bin
- file data5.bin
- file data6.bin
- mv data6.bin data6.bin.bz2
- file data6.bin
- tar -xf data6.bin
- file data8.bin
- mv data8.bin data8.bin.gz
- file data8.bin
- cat data8.bin and head data8.bin

```
**Explanation:**
- 'mktemp -d'.  Create a temporary directory.
- 'cd /tmp/tmp.y2GILdTC6e'. Change directory to the new temporary directory.
- 'cp /home/bandit12/data.txt /tmp/tmp.y2GILdTC6e' . Copy data.txt file from the home directory to the newly created temporary directory.
- 'mv /tmp/tmp.y2GILdTC6e/data.txt /tmp/tmp.y2GILdTC6e/data1.txt'. Change the name of the data.txt file
- 'file data1.txt'. Checks the file type which is ASCII text
- 'xxd -r data1.txt>data1'. Convert hexdump file back to raw binary output
- 'gzip -d data.gz'. Extracts file contents back into a file called data.
- 'tar -xf data1'. Extracts specific files from the archive.
- 'cat data8.bin'. Display the contents of the data8 file
- 'head data8.bin'. Display the first 10 lines of the data8 file.

**Password:**  GROozWPO8QyN0mGrjUkID0WCYkZiQxrN

**What I learned:** the "tar" command is used to extract files.


## Bandit Level 13 → Level 14

**Challenge:** Retrieve the password through establishing a SSH connection

**Solution:**
```bash
- nano ~/bandit14.key
- chmod 600~ /bandit14.key
- ssh -i ~/bandit14.key bandit14@bandit.labs.overthewire.org -p2220
- cat /etc/bandit_pass/bandit14
```
**Explanation:**
- 'nano ~/bandit14.key'. Create a key

**Password:**  qQYQiHOBPR8zR61qxYqX45quvihF2uzk

**What I learned:**  The tilde (~) represents the current users home directory.


## Bandit Level 14 → Level 15

**Challenge:** Find a password by ssh'ing to port 3000.

**Solution:**
```bash
- nc localhost 3000
```
**Explanation:**
- 'nc localhost 3000'. Connects terminal to port 3000

**Password:**  aaWecNkG4FhxJQxz07uiwzVP6bJiYS65

**What I learned:**  nc stands for Netcat.

## Bandit Level 15 → Level 16

**Challenge:** Retrieve password on 30001 port

**Solution:**
```bash
- Openssl_Client_connect localhost: 30001
```
**Explanation:**
- 'Openssl_Client_connect localhost: 30001'. 

**Password:**  pbLYuZtTg4MgaqfJx8jbA9gKKGqM68A7

**What I learned:**  Openssl is used for TLS protocols

## Bandit Level 16 → Level 17

**Challenge:** Find the password on port 30001 on localhost using SSL/TLS encryption.

**Solution:**
```bash
- nmap -p 31000-3200 localhost
- nmap -sV -p 31046, 31518, 31691, 31790, 31960 local host
```
**Explanation:**
- 'nmap -p 31000-3200 localhost'. Find open and listening ports within the specified range.
- 'nmap -sV -p 31046, 31518, 31691, 31790, 31960 local host'. Find the SSL/TLS port

**Password:**  kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V

**What I learned:**  "-sV" is the argument for the version detection flag


