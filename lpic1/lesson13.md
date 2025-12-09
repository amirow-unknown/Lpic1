---
name: lpic
lesson: "14"
topic: processing the text streams by filters
number: "14"
---
- Let's learn some commands and tools:
#cat -> to print the files' value
#zcat or #gzcat -> like cat but to print the files which has compressed(these commands don't extract, just print them)
#less -> to access the text file and search, paging, ...
	/ -> ***searching***
	press n -> ***to show next found word***
	? -> ***to search reverse***
	q -> ***quit***
#od -> dump files and input to ocal or other formats
```bash
echo "amir" | od #amir
#0000000 066541 071151 000012 0000005
echo -n "amir" | od #amir%
#0000000 066541 071151 0000004
echo "amir" | od 
#0000000   a   m   i   r  nl

echo -n "amir" | od 
#0000000   a   m   i   r
od -t -> #determining the format of dumping
	-a -> named charecter -> nl(\n) sp(space) ...
	-c -> character (shows scapes too) -> \n \t \b ...
	-d -> decimal
	-o -> octal
	-x -> hexadecimal
```
#spli -> to deviding the context of ditected file in numbers of file baed on lines, bytes, ....
	split filename -l 2 --> `to devide file context for each 2 lines`
	split filename -b4 --> `to devide file context for each 4 bytes`
#head and #tail -> ***head is from up to down ward and tails is opposite of head***
	-n -> shows how many lines
#cut -> to filter the context, based column:
	-f --> field number to show
		-f1,2,4-6 ---> field 1 and 2 and 4 to 6
	-d --> deteminator --> to seprate the columns based on what!
		-d" " ---> space
		-d: -----> symicolen
		-d, -----> comma
```bash
cut -f1 -d: /etc/passwd
root
bin
daemon
mail
ftp
http
nobody
dbus
systemd-coredump
systemd-network
systemd-oom
systemd-journal-remote
systemd-resolve
systemd-timesync
amir
```
#nl -> it works like command `cat -n`, prints line numbers
#sort -> it sort the lines by character, number,.....
	-c -> sort by number
#uniqu -> for repeated lines and words:
	uniqu ->  deletes the repeated lines by order not globally
	sort | uniqu -> deletes the all repeated lines
	uniqu -u -> shows the lines which exist once
	uniq -c -> shows the number of repeatation of each
#sed -> it's enaugh famous which doesn't need to be proved
	`sed 's\a\b'` -> a to b
	`sed 's\a\b\g'` -> a to b globaly
	...
#wc -> to check the counts of lines,characters,words,....
	`wc amir.txt` -> 18 18 123 amir.txt --> `18 lines, 18 words, 123 characters`
	wc -l ---> line number
	wc -c ---> character number
	 wc -w ---> word number
### #hash's
- used in password and username authentication, database, salting, iso and .... files
***some of them are***:
- md5sum
- sha256sum -> 256 bytes
- sha512sum -> means 512 bytes
- #note -> how many the hash be longer, it's more difficult to be broke.
- if even 1 byte of file changed, the hash gonna be changed, so it's good idea to use it in authorization and intigrity machanisms.
