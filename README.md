#Reading and Writing XLSX on Android 5
Reading and Writing XLSX and XLS on Android 5 with Apache POI

It was quite a challenging task to use Apache POI on android with Dalvik VM. It is much easier to use Apache POI on Android 5+ with ART VM and Build Tools 21+

Please refer to https://github.com/andruhon/AndroidReadXLSX if you need to read XLSX on Android 4 with Dalvik VM.

#Contents
I've repacked poi-ooxml to contain all dependencies in order to read and write XLSX (XLS as well, obviously)

poi-3.12-android.jar :  
* poi-3.12-20150511.jar  
* poi-ooxml-3.12-20150511.jar  
* stax-1.2.0.jar  
* stax-api-1.0.1.jar  
* *xmlbeans-2.6.0.jar* //this one contained duplicates, Android does not like it

poi-ooxml-schemas-3.12-20150511.jar //original schemas jar

Copy these two jars into your project's libs directory and use gradle config similar to bild.gradle from this repo.

It will work if you use all original files from https://poi.apache.org/download.html, however you need to re-pack xmlbeans-2.6.0.jar because for some reason it contains duplicates and Android does not like it.

#Configuration
Please find gradle app configuration with comments in the build.gradle, two crucial things are enabling multi-dex and compiling with --core-library option.

#Usage example
Usage example is coming soon
