# Overview

Here you'll find an updated version of Roku SceneGraph's xsd, because the [published one](https://devtools.web.roku.com/schema/RokuSceneGraph.xsd] is out of date

## This project should not even exist: Please ask Roku to update their XSD

It's a shame they don't keep it up to date as it means those of us working hard to make developer tools can't serve you as well as we'd like. 

Email them and let them know that this is a priority for you: this repo should not be necessary [developer@roku.com](mailto:developer@roku.com)

# Suggested use

Here's one unobtrusive workaround I've figured out, which works for me:

 - Fork this repo (so you can submit pull requests for any fixes you make), and clone to your machine 
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
      "systemId": "/Users/PATH_TO_THIS_REPO_CLONE/RokuSceneGraph.xsd",
      "pattern": "**/*.xml"
    },
  ],

```

note - you might want a more constrained pattern (perhaps only pointing at your components path), to prevent you applying xsd's erroneously.
    

# Making your own changes
 In your own fork, create a branch where you'll add your custom types for extends until we add that to the [vscode brightscript language plugin](https://github.com/TwitchBronBron/vscode-brightscript-language/)

For example, edit the code in your branch for extends attribute:

```
<xs:attribute name="extends" use="required">
<xs:annotation>
<xs:documentation>&lt;b...............
</xs:annotation>
<xs:simpleType>
    <xs:restriction base="xs:string">
        <xs:enumeration value="Node"/>
        <xs:enumeration value="Task"/>
        <xs:enumeration value="ScrollingLabel"/>

        <xs:enumeration value="CustomComponent1"/>
        <xs:enumeration value="CustomComponent2"/>
        <xs:enumeration value="CustomComponentEtc"/>
                        
```

You can make other changes too; but you'll want to keep them separate from any pr's you'll be submitting here, so the best course of action is your own fork, and cherry pick in problems with the xsd when you see it.

# Submitting prs

Please contribute! If you get a red squiggly in your ide with valid xml sytnax, please edit this xsd and submit a pr.

# Thanks

To Roku (though not for having an out of date xsd) and the great community over at the [Roku developer slack](http://tiny.cc/nrdf0y) who are always spurring each other on to make the Roku world a better place.

