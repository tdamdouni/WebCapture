# Compress files using 7-zip

_Captured: 2016-07-05 at 14:53 from [net-informations.com](http://net-informations.com/q/mis/7zip.html)_

7-Zip is an open source software. It is a file archive compression utility that can be used on any computer. The 7-Zip utility can be used from a command line interface, graphical user interface, or with a window-based shell integration. By default, 7-Zip creates 7z format archives with a .7z file extension. Besides operating on the 7z format, it supports many other popular archive formats and can seamlessly work on them. The main features of 7z format are it has high compression ratio and it supporting files with sizes up to 16000000000 GB. Moreover 7zip is distributed under LGPL license as a free software to use.

#### How to download 7-Zip ?

You can freely download 7-zip.exe file from http://www.7-zip.org

**[Click here to download 7-Zip.exe**](http://www.7-zip.org/)

After download 7-zip.exe you have to double click the file and install it. After installed the 7-zip.exe you can find it on windows C:\Program Files\7-Zip with the name 7z.exe

#### How to run 7-zip ?

For study purpose, you don't need to change environment paths, copy the 7-Zip folder to your user directory. Open a Command Prompt window from Start->All Programs->Accessories->Command Prompt. Change the command prompt directory to your 7-Zip folder.

### Usage:

7za [..] <archive_name> [<file_names>..] [<@listfiles..>]

#### How to compress (zip) files using 7-zip ?
    
    
    7z a -t7z files.7z *.txt -r
    

![how to compress a file](http://net-informations.com/q/mis/img/zip.png)

Above command compress all *.txt files from current folder and its subfolders to archive files.7z. The output filename (compressed filename) is files.7z

#### How to zip a folder ?
    
    
    7z a testzip.zip test

Above command compress the folder test and the output filename (compressed filename) is testzip.zip.

#### How to extract files ?
    
    
    7z e testzip.zip
    

Above command extracts all files from testzip.zip to the current directory.
    
    
    7z e testzip.zip -od:\ext
    

Above command extract all files from testzip.zip to the directory d:\ext
    
    
    7z e testzip.zip -od:\ext  *.dll -r
    

Above command extract all *.dll files from testzip.zip to the directory d:\ext

**Note:** 7-Zip will always prompt you if there is a file it needs to overwrite to extract the new file. Possible Query Answers:
    
    
     (Y)es / (N)o / (A)lways / (S)kip all / A(u)to rename all / (Q)uit 

#### How to list (view) all files from an archive ?
    
    
    7z l testzip.zip
    

Above command will display all files from testzip.zip

#### How to delete a file from an archive ?
    
    
    7z d testzip.zip *.dll -r
    

Above command will delete all .dll files from the archive testzip.zip

#### How to update files in an archive ?
    
    
    7z u testzip.zip *.dll
    

Above command update the testzip.zip file by adding all *.dll files to testzip.zip

### Switches:
    
    
    -y - Stops prompting. Automatically answers "Yes" to all questions.
    -ms=on - Enable solid mode. All files are compressed as one (unable to update, and olny for 7z format). Default behaviour.
    -ms=off - Disable solid mode.
    -o - Output. (7z x archive.zip -oC:Doc)
    -p - Password. (7za a pw.7z *.txt -pSECRET)
    -mhe - Encrypts headers. File names are not visible until decryption.
    -ssc - Specify case-sensitive (Windows default: insensitive, Linux default: sensitive).
    -ssw - Compress locked files.
    -sw - Specify working directory.
    -so - Redirect output to standard stream.
    

### m - Method. Specifies the compression method
    
    
    Switch -mx0: Don't compress at all. This is called "copy mode."
    Switch -mx1: Low compression. This is called "fastest" mode.
    Switch -mx3: Fast compression mode. Will automatically set various parameters.
    Switch -mx5: Same as above, but "normal."
    Switch -mx7: This means "maximum" compression.
    Switch -mx9: This means "ultra" compression. You probably want to use this.
    

### t - Type. Specifies archive type that you want to create
    
    
    Switch: -t7z Format: 7Z
    Switch: -tgzip Format: GZIP
    Switch: -tzip Format: ZIP
    Switch: -tbzip2 Format: BZIP2
    Switch: -ttar Format: TAR
    Switch: -tiso Format: ISO
    Switch: -tudf Format: UDF
    

#### Create and extract a password-protected file

The following commands create password-protected file uisng 7zip
    
    
    7z a arc.zip * -p
    

Then system ask to enter password:
    
    
    7z	: CommandName
    a	: Add to archive
    arc.zip	: Destination file name
    *	: Add all files from current directory to zip file
    -p	: Specify the password
    

The following commands extract a password-protected file uisng 7zip
    
    
    7z x arc.zip
    

Then the system ask the password, when you supply correct password it will extract the zip file

#### Create separate zip files for each directory/folder

You may know how to archieve multiple files to one zip file, but do you know how to zip multiple folders or files and create individual zip files for each of them automatically ? The following 7zip commandline shows how create seperate zip file for each folder you select.
    
    
    for /D %d in (*.*) do C:\7-Zip\7z a -tzip "%d.zip" "%d"
    

## 7-zip GUI (Graphical User Interface)

After successfully installed 7-zip, you can use 7-zip GUI (Graphical User Interface) to compress file(s).

#### How to zip (Compress) file(s) using 7-zip GUI ?

Right click on selected file(s) or folder(s), then you get the pop-up menu, select "7-zip" and then select "Add to Archive" menu.

Then you get the next window and you can set your file name and preferred path from that screen.

And then Click OK button. The files now compressed and saved to your prefered folder.

#### How to Quick Compression ?

Right click on selected file(s), then you get the pop-up menu, select "7-zip" and then select "Add to yourfilename.7z" menu.

#### How to extract 7-zip files ?

It is very easy to extract 7-zip file(s). Right click on the compressed file then select "7-zip" and then select "Extract Here" option. It will then extract all file(s) in the current directory.

"Extract Files" option will let you to select prefered folder and extract the files to that folder.

"Extract to yourfilename\" option will automatically create a folder and named your filename and then extract the whole files to that folder.

**NEXT.....**[How to Use Robocopy](http://net-informations.com/q/mis/robocopy.html)
