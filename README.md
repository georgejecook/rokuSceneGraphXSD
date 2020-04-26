# Overview

~~Here you'll find an updated version of Roku SceneGraph's xsd, because the [published one](https://devtools.web.roku.com/schema/RokuSceneGraph.xsd] is out of date~~

## ~~This project should not even exist: Please ask Roku to update their XSD~~

~~It's a shame they don't keep it up to date as it means those of us working hard to make developer tools can't serve you as well as we'd like. ~~
~~

This repo existed to work around there being no official XSD for scenegraph. 2 things have changed.

1. Roku now support an official xsd. Thanks roku!
2. Sam Heavner made a wonderful npm module that can generate custom xsds for you. 


# Suggested use

 - Install redhat xml [plugin](https://developers.redhat.com/blog/2018/12/04/xml-language-server-vscode-extension/) (if you haven't already)
 - make sure you have java home set, in your settings. e.g. in settings.json, you should have:

```
  "java.home": "/Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk/Contents/Home/",
  (or similar)
```
 	
 - In your roku xml component files, do not have _any_ xsi or xsd declarations, becuase you'll get the roku out of date one's (minus any of your edits). So remove these lines from your components:

```  
xsi:noNamespaceSchemaLocation="https://devtools.web.roku.com/schema/RokuSceneGraph.xsd"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
```

 - you now want to configure the xml extension to apply your xsd to your components
   - in your vscode settings add the following: 

```
  "xml.fileAssociations": [
    {
      "systemId": "/Users/PATH_TO_YOUR_XSD",
      "pattern": "**/*.xml"
    },
  ],

```

Instructions for generating your xsd are to be found here:

https://github.com/slheavner/scenegraph-schema
