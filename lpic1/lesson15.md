---
name: lpic
lesson: "15"
topic: redirect, streams, pipeline
number: "15"
---
- stdin ---> standard input ===> 0
- stdout ---> standard out put ====> 1
- stderr ---> standard error ====> 2

# Redirects:
`>` ---> sends #stdout to a file or ***overwrite*** the file if exists.
`>>` ----> write #stdout to a file or ***appends*** if file exists. 
`2>` ----> redirect #stderr to a file or ***overwite*** if exists
`2>>` ----> like `2>` but ***appends*** if file exists.
`&>` -----> redirect bot #stdout or #srderr to a file or ***overwrite*** it.
`&>>` -----> like `&>` but ***append*** if file exists.
`<` -----> redirect #stdin from the file 
`<>` ----> rediect #stdin  from the file and send #stdout to it.

- **you can use redirects together --->`ls amir oaa 2> error > output` --> so if you get error, your errors write on *error* file and if you get #stdout it write it in *output* file.**

- ***what are *&1* or *&2* or *&0*?*** 
	- `ls > A 2>&1` ---> write #stdout to file A and send #stderr to ***&1*** which is where your #stdout went, file A.

- What is the ***/dev/null*** ?
	it's a loop of nothing which used to send your non-useable stuff to it which don't need to save. such as #stderr 
	- example---> `ping google.com > ping.txt 2> /dev/null` --> #stdout goes to ping.txt and #stderr  goes to ***/dev/null***

- ### #pipe|
	- ls  ----> `amir Desktop`
	- ls | grep a ----> `amir`
- ### #xargs
	- ls | ls ---> `amir Desktop`
	- ls | xargs ls ---> 
		`amir: file1 file2 main.go`
		`Desktop: folder1 file3 file1`
	*-I ---> to set variable:*
		ls | xargs -I TEST echo "this is from TEST"
			this is from amir
			this is from Desktop

### #tee 
- if you wanna to run a command and save it's process and also see it
	- ls > amir ===> `you see nothing and most run cat amir to see`
	- ls | tee amir ===> you saw the process and also saved in file amir

