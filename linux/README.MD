Reverse Suite for Linux
=============

```bash
# ./rsuite.sh -h
  _____                                 _____       _ _       
 |  __ \                               / ____|     (_) |      
 | |__) |_____   _____ _ __ ___  ___  | (___  _   _ _| |_ ___ 
 |  _  // _ \ \ / / _ \ '__/ __|/ _ \  \___ \| | | | | __/ _ \ 
 | | \ \  __/\ V /  __/ |  \__ \  __/  ____) | |_| | | ||  __/
 |_|  \_\___| \_/ \___|_|  |___/\___| |_____/ \__,_|_|\__\___|
                                                                                                                            
./rsuite.sh <options>, where <options> are:

     -h                        what you are looking at
     -d <file.apk>,            disassemble the apk (convert to smali)
     -l,                       shows the name of the applications already disassembled
     -b <application_name>,    build the provided application as an apk (use with -o)
     -n,                       optimize images during build
     -x <file.apk>,            decompile the apk, and run luyten to verify the source code
     -o <file.apk>,            the name of apk that gets written (use with -b)
```
Disassemble the apk:
```bash
# ./rsuite.sh -d test.apk 
                                                                                                                            
Provide a name to save this app: test 
I: Using Apktool 2.2.4 on test.apk
I: Loading resource table...
I: Decoding AndroidManifest.xml with resources...
I: Loading resource table from file: /root/.local/share/apktool/framework/1.apk
I: Regular manifest package...
I: Decoding file-resources...
I: Decoding values */* XMLs...
I: Baksmaling classes.dex...
I: Copying assets and libs...
I: Copying unknown files...
I: Copying original files...

Extracted files can be found here: "/root/tools/git_tools/reverse-suite/output/test"
```
List all the disassembled apps:
```bash
root@attacker:~/tools/git_tools/reverse-suite/linux# ./rsuite.sh -l
                                                                                                                            
The applications you've extracted are: 
  test

To build one of the apps use: ./rsuite.sh -b test -o newfile.apk
```
Build an app:
```bash
root@attacker:~/tools/git_tools/reverse-suite/linux# ./rsuite.sh -b test -o new_apk_tampered.apk
                                                         
Building the app
I: Using Apktool 2.2.4
I: Checking whether sources has changed...
I: Smaling smali folder into classes.dex...
I: Checking whether resources has changed...
I: Building resources...
I: Copying libs... (/lib)
I: Building apk file...
I: Copying unknown files/dir...
Running alignment tool for Android application files
Signing the app

All done. You can now install the app: new_apk_tampered.apk
```


**Version of used tools:**

 - [**apktool** - v2.2.4](https://github.com/iBotPeaches/Apktool)
 - [**dex2jar** - 2.1-SNAPSHOT](https://github.com/pxb1988/dex2jar)
 - [**jd-gui** -  1.4.0](https://github.com/java-decompiler/jd-gui)
 - [**luyten** - 0.5.3](https://github.com/deathmarine/Luyten)
