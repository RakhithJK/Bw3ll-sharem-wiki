The setup instructions should be followed. These are reproduced here, but this will differ slightly once it is on GitHub, after it has been released publicly. Right now it is available via Google Drive for Black Hat reviewers.

At a high-level, what we are doing is installing a package locally. The steps below should be followed closely.

To run this, it must be on a Windows machine.
All OS's are supported, but for ease of use to demo it, Windows is recommended (more detailed instructions are needed for other OS's). 

**Note:** SHAREM will extract Windows DLLs, inflate them by a set amount as specified by PE file, and save them into a special directory, allowing these to be loaded into the emulation. For other OSs, these would need to be imported – but in an “inflated” state.