## Initial Setup of SHAREM Shellcode Analysis Framework
The setup instructions should be followed. These are reproduced here, but this will differ slightly once it is on GitHub, after it has been released publicly. Right now it is available via Google Drive for Black Hat reviewers.

At a high-level, what we are doing is installing a package locally. The steps below should be followed closely.

To run this, it must be on a Windows machine.
All OS's are supported, but for ease of use to demo it, Windows is recommended (more detailed instructions are needed for other OS's). 

_Note: SHAREM will extract Windows DLLs, inflate them by a set amount as specified by PE file, and save them into a special directory, allowing these to be loaded into the emulation. For other OSs, these would need to be imported – but in an “inflated” state._

## Install setups
1.	Obtain the SHAREM code from the Google drive
2.	From the \sharem directory, run install.bat
3.	Next,  an ssdeep wrapper for Windows must be installed. Go to https://github.com/MacDue/ssdeep-windows-32_64 and follow the instructions in the readme for SSDeep after downloading the code for this Windows version of ssdeep: https://github.com/MacDue/ssdeep-windows-32_64/blob/master/README.md

_Note:_ this is the only Windows ssdeep -- other ways of installing SSDeep are for Linux -- and this step must be completed in order for the framework to work, as SSDeep is required, and this one dependency causes issues with the install script.

## When You Run the Emulation for the First Time

1. SHAREM will go and acquire DLLs from the Syswow64 directory. It will expand them slightly, each one according to what is in the pe file, so that they are similar to how they would be in memory. It will also map functions to addresses contained in those DLLs. This initial setup will be performed once, and it will take several minutes. If it hangs up after more than several minutes, hit enter. After it is done, this step need not be completed ever again. This step will run automatically if required – no special actions are required, other than to go into the emulation menu (l) and type z.

In order to set up the emulation, navigate inside the sharem_cli directory. Shellcode.bin is any shellcode.

`py main.py -r32 shellcode.bin`

Alternatively, from the main directory, you can run it with 

`py sharemMain.py -r32 shellcode.bin`

One sample shellcode.bin is supplied for initial testing. Others are available in the shellcodes Gdrive. [Google Drive Link](https://drive.google.com/drive/folders/1E36ZOAaKFSeromzXd7zTq5fdGC36lg_N?usp=sharing)
Password is **SHAREM**. These shellcodes walk the PEB and discovering API addresses of functions and then calls those.

The initial set up should be ran by launching SHAREM. It will launch a process to begin setting up the emulation, and it will provide a message indicating this as well. Once complete, enter z (may need to restart the program). If it hangs up on setting up the emulation, this process may need to be repeated. Once completed, it will begin by saying Emulating x86_32 shellcode.

Ideally, this should be set up on a modern Windows 10 system with Python installed – older versions of Windows 7 potentially could be temperamental, although it does work on some we tested. A modern Windows 10 should present no problems.

To run the program, please provide a shellcode .bin or .txt (ASCII of shellcode binary) as input, using the -r switch
E.g.

`py sharemMain.py -r32 shellcode.bin`

Or from the sharem_cli directory:

`py main.py -r32 shellcode.bin`