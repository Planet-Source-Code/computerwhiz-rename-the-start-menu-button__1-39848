<div align="center">

## Rename the Start Menu Button


</div>

### Description

This article will show you how to rename the Windows Start Menu button in Win 9x and WinXP ....
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[ComputerWhiz](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/computerwhiz.md)
**Level**          |Beginner
**User Rating**    |4.8 (24 globes from 5 users)
**Compatibility**  |VB 3\.0, VB 4\.0 \(16\-bit\), VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__1-1.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/computerwhiz-rename-the-start-menu-button__1-39848/archive/master.zip)





### Source Code

Warning: I shall not be liable for any damages or injuries. Before you start, you should make a backup copy of explorer.exe, and know how to restore it.
1. Windows 9x
The name of the Start Menu button is in explorer.exe. Since Windows won't let you modify the file, you must make a copy of it, modify the copy, then boot into DOS and replace the original file by the modified version. Make sure you back up explorer.exe before you start.
Load the file into an hexadecimal editor, and search for the following hexadecimal bytes:
53 00 74 00 61 00 72 00 74 (= "Start"). You will find these bytes more than once, but you should only have to change the last occurrence.
Replace S, t, a, r, t by whatever you want, but leave the 00's in. If your new string is shorter than "Start", you can either overwrite the extra letters with blanks, or you can change the length byte. Just before the first byte (53) there is a 00 and before it a 05: this is the string's length. If the new string is "New" then this byte should be set to 03 -- this way the Start Menu button will not be longer than the string. The new string must not be longer than the original one, else Windows will not work.
Note: The icon is in user.exe
2. Windows XP
You can use the method described above if you want: In the US version of Windows XP Pro, the string is at 0EE36F (Classic-style button) and 0EE096 (XP-style button). But instead, we are going to use Resource Hacker (542KB).
2.1. Bypassing Windows File Protection
1. In Windows Explorer, click Tools, Folder Options, then View. Uncheck Hide protected operating system files and check Show hidden files and folders.
2. There is a file named filelist.xml in \windows\system32\Restore. Right click the file, then click Properties, and uncheck Read-only. Open filelist.xml in Notepad, and add the line shown in red below, then save the file and close Notepad.
<exclude>
   <rec>%sytemroot%\explorer.exe</rec>
   <rec>%windir%\system.ini</rec>
   <rec>%windir%\tasks\desktop.ini</rec>
   <rec>%windir%\win.ini</rec>
   <rec>*:\AUTOEXEC.BAT</rec>
   <rec>*:\CONFIG.MSI</rec>
   <rec>*:\CONFIG.SYS</rec>
</exclude>
3. In \windows\system32\dllcache, you will find a backup copy of explorer.exe. Rename it to explorer.bak.
2.2. Changing the name of the Start Menu button

