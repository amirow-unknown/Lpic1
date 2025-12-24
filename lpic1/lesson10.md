---
name: lpic
lesson: "10"
topic: package management
number: "10"
---
we have a mirrorlist file and it's configuration files are different from vary distributes.
- ### Debian
	#apt-get and #apt and #dpkg 
	#apt and #apt-get both are package manager in debian which look to mirrorlist and use those mirrors to update, download, search, etc.
	#dpkg is a tool to install #deb  files.
	- you can find #mirror and #apt configs in #/etc/apt/ directory
- ### RPM and YUM in redhats
  in #redhats we have #yum, #dnf package managers
  `we don't deepin redhats and debians yet!`
  - #rpm:
	  #-i -> install packagename.rpm
	  #-U -> if package has installed, it upgrades it, unless install it
	  #-e -> earase, means remove the package from system
	  - query in #RPM:
		  #-q -> used to send query with it's switches
		  #-qi -> information of package
		  #-qc -> packages configuration files
		  #-qa -> shows all installed packages
		  #-qR -> dependencies of a package requires
		  #-qf -> shows package owning file
		  #-ql -> lists the files of a package installs
- ### Pacman (Arch based)
	this is my favorite so let's learn it:
	pacman categorize packages which installed in 2 category:
	1- #packages which are installed by `pacman -S`or`pacman -U file.zst`
	2- #packages which are installed as #dependency cause they are required by other packages.
	- ##### switches:
	#-S -> `pacman -S package1 package2 ...` to install packages
	#-R ->`pacman -R pkgname`only unistall and remove package not it's dependencies and configuration files.
	#-Rs -> `pacman -Rs pkgname`removes package and it's dependecies
	#-Rns ->`pacman -Rns pkgname`remove package and it's depencies and configuration files.
	#-Syu ->`pacman -Syu`updating the system and packages:
		#-S -> synchronize the database
		#-y -> refresh local cache
		#-u -> system update
		#how_it_works? your arch synchronize which mirrors and then refresh your local cache with new value and then run system update.
	#-Q -> to see all packages 
		#-Qs -> `pacman -Qs zsh tmux` -> esearching for one or multiple package
	#-F ->`pacman -F pkgname`-> search the pkgname in local database.
	#-Ss -> `pacman -Ss pkgname`-> search the repos(mirrors) to your package name.
	#paccache ->`paccache -r` -> to remove pacman cache
	#pactree -> `pactree zsh` -> shows a tree of zsh require dependencies.
	- ==how to install unofficial packages==?
	- #-U -> `pacman -U packagename.pkg.tar.xz` -> install th `pkg.tar.xz` file for arch.
	- #-U -> `pacman -U https://adjnneneffe/sfe/fefe/ex.pkg.tar.xz` -> install remove packages which is not from official repo and mirror.
	- #Qi -> `pacman -Qi packagename` -> to see package information





