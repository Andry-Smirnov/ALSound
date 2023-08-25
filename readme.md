# Introduction

ALSound offer an easy way to play, capture and mix sounds for your FreePascal/Lazarus applications. It use OpenAL-Soft and LibSndFile libraries.

OpenAL-Soft is an improved software implementation of OpenAL, actively maintained by Christopher Robinson (https://github.com/kcat/openal-soft).
LibSndFile is a C library for reading and writing audio files (https://github.com/libsndfile/libsndfile).
You hardly have to know these libraries to use ALSound.

ALSound is also compatible with old version of OpenAL but advanced features may not work.
If a feature is not available, the requested action is simply ignored and in some cases, an error message is returned (like the design of OpenAL). Not all new features of OpenAL-Soft are implemented.

Tested under Linux and Windows, i386 and x86-64.
May work on other platforms with the appropriate compiled libraries.

For FreePascal/Lazarus  
lulu - 2022  
# Contents

'source' -> the source of ALSound.

'example' -> contains some examples to show how to integrate ALSound in your FreePascal/Lazarus programs. After compilation, the example executable are placed in folder "binary", sub-folder "$(TargetCPU)-$(TargetOS)"

'docs' -> In progress. Contains a copy of OpenAL documentation.

'binary' -> contains sub-folder for each actual supported platforms. The compiled binaries of OpenAL-Soft and LibSndFile are provided for Windows and Linux both i386 and x86-64 and can be found in their respective sub-folder. If you prefers to compile these libraries by yourself, please go to their respective github repository and follow the guideline.  
# Dynamic linking libraries

ALSound loads dynamically the two libraries at startup:

## Under Windows
> The dlls must be named 'soft_oal.dll' and 'sndfile.dll' and copied in the same folder (or in a sub-folder) as your executable.
If you use a sub-folder, your application must call ALSManager.SetLibrariesSubFolder(OnlyTheNameOfTheSubfolder) before calling ALSManager.LoadLibraries.


## Under Linux
> The libraries must be named 'libopenal.so' and 'libsndfile.so' and copied in the same folder (or in a sub-folder) as your executable. If you use a sub-folder, your application must call ALSManager.SetLibrariesSubFolder(OnlyTheNameOfTheSubfolder) before calling ALSManager.LoadLibraries.

## Under MacOS
The libraries must be named 'libopenal.dylib' and 'libsndfile.dylib'.
- If your application don't use a bundle:
> put a copy of the libraries in the same folder (or in a sub-folder) as your executable and in your Lazarus->Project options->Application->**uncheck** 'use Application Bundle for running and debugging'.
- If your application use a bundle:
> put a copy of the libraries in the Resources folder of the bundle (or sub-folder and in your Lazarus->Project options->Application->**check** 'use Application Bundle for running and debugging'.

**In all platforms, if the libraries are located in a sub-folder of your executable (or a sub-folder in /Resources in a MacOS bundle), your application must call ALSManager.SetLibrariesSubFolder(OnlyTheNameOfTheSubfolder) before calling ALSManager.LoadLibraries.

# Thanks
Thanks to Christopher Robinson, the author and maintainer of OpenAL-Soft, for its help.  
Thanks to the LibSndFile team.
(https://github.com/libsndfile/libsndfile)  

Thanks to Fred van Stappen, the author of United OpenLib of Sound (UOS) (https://github.com/fredvs/uos) who wrote pascal binding for LibSndFile and PortAudio. This inspired me to write pascal binding for OpenAL-Soft and LibSndFile used by ALSound.


