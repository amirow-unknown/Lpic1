---
name: lpic
lesson: "11"
topic: VMM, guest machine, hypervisor
number: "11"
---
# Virtualization
- to have more OS on our pc we can use #VM(virtual machine) which runs #virtual_os. 
- the to run #VMs we need a #VMM(virtual machine manager) or #hypervisor, such as VMware or Virualbox or sandbox. ***the simple workflow of hypervisors***:
	hardware -> OS(main and first os) -> hypervisor(Virtualbox, ...) -> Virtual Machine.
- #notice -> your intel or amd cpu must support hypervisor ability(32bit doesn't).
- we have #kvm in linux as a #hypervisor.
- #bare_metal_hypervisor -> they don't need to a guest OS(main os) and directly runs on main hardware, but we ignore it.
- how to install a Virtual machine?
	install a hypervisor on your host os(main os)
	run it and give requier fields such as ram, cpu cores, storage, ....
	give a iso file or booted cd or usb to install the guest os.
#### #clone?
	- to have a same virtual machine in your hypervisor you can clone it.
	- if you have more #hypervisor and wanna to have same #VM on your all #hypervisor, there are some option such as #OVF(open virtualization format) or #OVA(open virtualization archive) or #tempate. -> *we ignore this section cause we don't need it*
	- #notice -> if you wanna using #clone option, cause this process, copies all configurations of os, you must change the cloned os some configurations such as #NIC-mac, #NIC-ip, #ssh-fingerprints, #hdd-uuid and #virtual_machine-UUid 
### container:
- imagine you use an OS, you need to run or test or ... which need a different architecture such as linux.
- you can run a #container_engine such as #docker .
- it doesn't have guest, only runs your apps and it's require dependencies.:
- hardware -> host OS -> container engine -> different isolated container which runs different or same services.
- #main perpose of using containers, are their lightweigth and so on. ==we gonna learn about it later==
