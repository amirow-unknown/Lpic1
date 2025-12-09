---
name: lpic
lesson: "9"
topic: manage shared libraries
number: "9"
---
- what are the lib's(library) in linux and how day works?
	- in linux we use #sharing_library strategy which several services can use one library and we don't need to download that #shared_library for each one separately!
- where are those lib's directory and files?
	- directory #/lib -> includes libraries which are #32bits. 
	- directory #/lib64 -> includes libraries which are #64bits.
	- directory #/usr/lib64 -> linked to #/lib 
	- directory #/usr/lib32 and #/usr/lib64 -> for services which user has installed.
- linking:
	#linking -> when you develop a application or service, you gonna need to some libraries!. so there 2 types of how to use those require libraries for our service or app:
	#static:at this method, you must link your app to it's require libraries to use them staticlly, at this method, the #ELF(linux executable file format) gonna has big size and your space gonna decrease, the librarys' updates gonna be missed . 
	#dynamic: at this method, you as a developer must determine in your executable file i mean in #ELF that your file need to these `....` libraries and your service gonna use those shared libraries and then execute.
- how the services|apps finds shared libraries?
	- at first, when your service runs and needs to libraries, the system automatically runs #LD_LIBRARY_PATH which is built in variable of shell.
	- when you call #LD_LIBRARY_PATH it's value is #/etc/ld.so.cof which it can be a configuration file which shows the path of libraries to services which needed, or it can has more #SUB-configuration file.
	-  ==cat /etc/ld.so.conf==:
	- ##Dynamic linker/loader configuration.
     ##See ld.so(8) and ldconfig(8) for details.
     include /etc/ld.so.conf.d/*.conf
     include /usr/lib/ld.so.conf.d/*.conf
     - ==ls /etc/ld*==
     - /etc/ld.so.cache
     - /etc/ld.so.conf
     - /etc/ld.so.conf.d
    - ##### but let's go deeper:
     there is a command which called #ldconfig:
     it gonna process all libraries so fast and make a cach file which is #/etc/ld.so.cach 
     - `ldconfig` -> reload the /etc/ld.so.conf file
     - `ldconfig -v` -> shows the progress of reprinting the ld.so.cach and rereading ld.so.conf
     - `ldconfig -p` -> used to see what has saved in #ld.so.cach
     sudo ldconfig -p 
     2182 libs found in cache `/etc/ld.so.cache'
	 libzstd.so.1 (libc6,x86-64) => /usr/lib/libzstd.so.1
	 libzstd.so (libc6,x86-64) => /usr/lib/libzstd.so
	 libzmq.so.5 (libc6,x86-64) => /usr/lib/libzmq.so.5
	 libzmq.so (libc6,x86-64) => /usr/lib/libzmq.so
	 libzix-0.so.0 (libc6,x86-64) => /usr/lib/libzix-0.so.0
	 libzix-0.so (libc6,x86-64) => /usr/lib/libzix-0.so
	 libzimg.so.2 (libc6,x86-64) => /usr/lib/libzimg.so.2
	 libzimg.so (libc6,x86-64) => /usr/lib/libzimg.so
	 libz.so.1 (libc6,x86-64) => /usr/lib/libz.so.1
     ...
- commands:
	#ldd:this command shows that is our service #dynamic_executable or not, also shows it's #requirement_libraries.
	- `ldd /usr/bin/go` -> ``not a dynamic executable`` -> it means that the #go command is a #static_linked service not dynamic. 
	- `ldd /usr/bin/ls`->
	 ldd /usr/bin/ls
	 `linux-vdso.so.1 (0x00007fb1c6c38000)`
	 `libcap.so.2 => /usr/lib/libcap.so.2 (0x00007fb1c6bdf000)`
	 `libc.so.6 => /usr/lib/libc.so.6 (0x00007fb1c6800000)`
	 `/lib64/ld-linux-x86-64.so.2 => /usr/lib64/ld-linux-x86-64.so.2` `(0x00007fb1c6c3a000)`
- symbolic links for libraries:
	- during this lessons, have your even asked yourself what if a service #requirement_library_version doesn't match to #exist_library?
	 at this situation, we gonna use symbolic and linking the old library path to new version!
     - `ls /lib/libgstadaptivedemux-1.0.so.0 -lrth`
     - `lrwxrwxrwx 1 root root 35 Oct 14 22:06 /lib/libgstadaptivedemux-1.0.so.0 -> libgstadaptivedemux-1.0.so.0.2607.0`
