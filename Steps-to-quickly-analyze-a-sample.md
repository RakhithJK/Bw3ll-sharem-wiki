## Initial Setup of SHAREM Shellcode Analysis Framework
The setup instructions should be followed. These are reproduced here, but this will differ slightly once it is on GitHub, after it has been released publicly. Right now it is available via Google Drive for Black Hat reviewers.

At a high-level, what we are doing is installing a package locally. The steps below should be followed closely.

To run this, it must be on a Windows machine.
All OSs are supported, but for ease of use to demo it, Windows is recommended (more detailed instructions are needed for other OSs). 

_Note: SHAREM will extract Windows DLLs, inflate them by a set amount as specified by PE file, and save them into a special directory, allowing these to be loaded into the emulation. For other OSs, these would need to be imported – but in an “inflated” state._

## Install setups
1. Obtain the SHAREM code from the Google drive
2. From the \sharem directory, run install.bat
3. Next,  an ssdeep wrapper for Windows must be installed. Go to https://github.com/MacDue/ssdeep-windows-32_64 and follow the instructions in the readme for ssdeep after downloading the code for this Windows version of ssdeep.

_Note:_ this is the only Windows ssdeep -- other ways of installing ssdeep are for Linux -- and this step must be completed in order for the framework to work, as ssdeep is required, and this one dependency causes issues with the install script.

## When You Run the Emulation for the First Time

SHAREM will go and acquire DLLs from the Syswow64 directory. It will expand them slightly, each one according to what is in the pe file, so that they are similar to how they would be in memory. It will also map functions to addresses contained in those DLLs. This initial setup will be performed once, and it will take several minutes. If it hangs up after more than several minutes, hit enter. After it is done, this step need not be completed ever again. This step will run automatically if required – no special actions are required, other than to go into the emulation menu (l) and type z.

In order to set up the emulation, navigate inside the sharem_cli directory. Shellcode.bin is any shellcode.

`py main.py -r32 shellcode.bin`

Alternatively, from the main directory, you can run it with 

`py sharemMain.py -r32 shellcode.bin`

The initial set up should be ran by launching SHAREM. It will launch a process to begin setting up the emulation, and it will provide a message indicating this as well. Once complete, enter z (may need to restart the program). If it hangs up on setting up the emulation, this process may need to be repeated. Once completed, it will begin by saying Emulating x86_32 shellcode.

![setupEmulation](https://user-images.githubusercontent.com/114108866/191625501-46a00c77-f91c-408b-9d97-df57501ab1e7.png)

Ideally, this should be set up on a modern Windows 10 system with Python installed – older versions of Windows 7 potentially could be temperamental, although it does work on some we tested. A modern Windows 10 should present no problems.

To run the program, please provide a shellcode .bin or .txt (ASCII of shellcode binary) as input, using the -r switch

E.g.
`py sharemMain.py -r32 shellcode.bin`

Or from the sharem_cli directory:

`py main.py -r32 shellcode.bin`