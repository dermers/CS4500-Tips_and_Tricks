# VSCode with WSL (for Windows 10)

## Windows Subsystems for Linux

1. Get WSL from the Microsoft/Windows store
	1. Search "WSL" in the store
	2. Click "Get the apps" on the "Linux in Windows?" banner
	3. Pick your distro
	   - Ubuntu was the first one they made, and the one I can verify works
2. Start WSL
	1. Install g++
	2. Install valgrind
	
Note: to navigate to your windows files, cd to /mnt/[c/d/etc]/...

## VSCode

1. Install VSCode for windows from [here](https://code.visualstudio.com/docs/?dv=win)
2. Open it


### Extensions

1. Click on extensions on the left side
2. Search for and install "Remote - WSL"
	1. Click on the green '><' symbol in the bottom left and select Remote-WSL: New Window
	2. Navigate to the top of you folder hierarchy for your code
	3. Note: the windows folders are in /mnt/[drive]/... 
3. Search for and install "C/C++"
4. (Optional) Search for and install "Todo Tree", now any "// TODO"s you write will be highlighted and can be navigated through a tree like file hierarchy on the left side (in the todo tree extension's panel).
