---
name: lpic
topic: mail transfer agent (MTA), Printers
lesson: "33"
number: "33"
---
# ***MTA:***






# ***Printers:***
- `cups`, `lpq`,`lpc`, `lpr`, `lprm`

- #cups is a service to use printers and printing in linux, it has GUI via web and command line commands to send and get status of printers and their jobs
- after installing by `sudo pacman -S cups` you should enable it by `sudo systemctl start/enable cups`,
- it's configuration files are in `/etc/cups` directory and it's main config file is `/etc/cups/cupsd.conf`.
- the web interface address is `localhost:631` which you can change it by modifying `/etc/cups/cupsd.conf` file.
- the web interface has some parts which are 
- #administration ---> adding printers and other settings such as paper size and etc.
- #Jobs ---> files to print
- #Printers ---> printers and their cofigurations.
----
***Tools:***
- #lpc ---> printers control and troubleshooting program.
	- `lpc status` ---> shows status of printers
- #lpq ---> shows printers jobs
	- `lpq -a` ---> all printers and their jobs
	- `lpq -Pprintername` ---> shows selected printer jobs
- #lpr ---> sending job to printers
	- `lpr -Pprintername file_to_print.txt`
- #lprm ---> remove job
	- `lprm jobid`
	- `lprm -` ---> remove all jobs

#### to disable or reject jobs for printers:
how --> `command "printername"`
#cupsaccept ---> accept jobs
#cupsreject ---> reject jobs
#cupsdisable ---> disable printer
#cupsenable ---> enable printer
- -r used to comment
	- sudo cupsdisable myprinter -r 'it has no paper'
