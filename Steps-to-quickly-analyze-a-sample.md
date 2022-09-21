## Initial Setup of SHAREM Shellcode Analysis Framework
The setup instructions should be followed. These are reproduced here, but this will differ slightly once it is on GitHub, after it has been released publicly. Right now it is available via Google Drive for Black Hat reviewers.

At a high-level, what we are doing is installing a package locally. The steps below should be followed closely.

To run this, it must be on a Windows machine.
All OS's are supported, but for ease of use to demo it, Windows is recommended (more detailed instructions are needed for other OS's). 

_Note:_ SHAREM will extract Windows DLLs, inflate them by a set amount as specified by PE file, and save them into a special directory, allowing these to be loaded into the emulation. For other OSs, these would need to be imported – but in an “inflated” state.

## Install setups
1.	Obtain the SHAREM code from the Google drive
2.	From the \sharem directory, run install.bat
3.	Next,  an ssdeep wrapper for Windows must be installed. Go to https://github.com/MacDue/ssdeep-windows-32_64 and follow the instructions in the readme for SSDeep after downloading the code for this Windows version of ssdeep: https://github.com/MacDue/ssdeep-windows-32_64/blob/master/README.md

_Note:_ this is the only Windows ssdeep -- other ways of installing SSDeep are for Linux -- and this step must be completed in order for the framework to work, as SSDeep is required, and this one dependency causes issues with the install script.