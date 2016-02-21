#Reading and Writing XLSX on Android 5
Reading and Writing XLSX and XLS on Android 5 with Apache POI

It was quite a challenging task to use Apache POI on android with Dalvik VM. It is much easier to use Apache POI on Android 5+ with ART VM and Build Tools 21+

Please refer to https://github.com/andruhon/AndroidReadXLSX if you need to read XLSX on Android 4 with Dalvik VM.

#Contents
I've repacked poi-ooxml to contain all dependencies in order to read and write XLSX (XLS as well, obviously)
All javax classes from the STAX library and calls to them are renamed to aavax, to avoid --core-library warning and conflicts.

* poi-3.12-android-a.jar //Repacked POI with all dependencies
* poi-ooxml-schemas-3.12-20150511-a.jar //original schemas jar

Copy these two jars into your project's libs directory and use gradle config similar to build.gradle from this repo.

It will work if you use all original files from https://poi.apache.org/download.html, however you need to re-pack xmlbeans-2.6.0.jar because for some reason it contains duplicates and Android does not like it. See below for contents of jar and details of javax -> aavax hack.

#Configuration
Please find gradle app configuration with comments in the build.gradle, the crucial thing is enabling multi-dex.

#Auto-downloading dependencies
This might also be achieved by adding 'org.apache.poi:poi-ooxml:3.12' into dependencies, but it is not very straightforward because it is required to add some routine to re-pack xmlbeans and disable preDex. It will work. however the build process will be very slow, so it is easier just to prepare jars once and put them into libs directory (as described above)

#Contents of poi-3.12 jar
* poi-3.12-20150511.jar  
* poi-ooxml-3.12-20150511.jar  
* stax-1.2.0.jar  
* stax-api-1.0.1.jar  
* *xmlbeans-2.6.0.jar* //this one contained duplicates, Android does not like it

#javax -> aavax hack
the following classes and calls to them were renamed (as HEX strings + renaming namespace dir javax to aavax):
* javax/xml/namespace -> aavax/xml/namespace
* javax.xml.namespace -> aavax.xml.namespace
* javax/xml/stream -> aavax/xml/stream
* javax.xml.stream -> aavax.xml.stream
* javax/xml/XMLConstants -> aavax/xml/XMLConstant
* javax.xml.XMLConstants -> aavax.xml.XMLConstants

Please note that you'd better not replace all javax to aavax, because there might be calls other classes from javax package which are available in android.



#Usage example
Usage example is coming soon
