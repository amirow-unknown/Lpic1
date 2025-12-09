---
name: lpic
lesson: "24"
topic: hard and soft(symbolic) links
number: "24"
---
- imagine you have a file with any type, now you wanna use that file but in other name and you want a file which when you run it, it refers to that first file. ***so use hard link or soft(symbolic) link.***
![[Screenshot_2025-11-23_17-29-43.jpg]]
## commands:
- ***ln mainfile linkfile*** ---> hardlink of linkfile to mainfile
- ***ln -s mainfile linkfile*** ---> softlink of linkfile to mainfile
- ***ln -s maindirectory linkdirectory*** ---> softlink of maindirectory to linkdirectory
- ***unlink linkedfile*** ----> unlink the linkedfile 
- ***unlink linkeddirectory ***---> unline the linkeddirectory
## Tip's:
- in both of hard and soft links, when you modify main file, the linked files gonna be modifyed.
- In hardlink, when you delete main file, the linked file doesn't remove or error and contains the content.
- In softlink, when you delete main file, the linked file doesn't work cause that linked file need to the main file
- you can only link directories by soft link not hard links
