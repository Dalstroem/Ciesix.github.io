---
title: XML namespace definition mapping
layout: post
#date: 0000-01-01 00:00:00 +0000
tags: [c#, xaml, xml]
---
A few days ago, I discovered a pretty neat feature when I was using XML namespaces in a XAML file. I have properly done this a few thousand times before. But one thing that have always annoyed me, is setups like this:

```
xmlns:converter="clr-namespace:Application.Converter"
xmlns:sharedControls="clr-namespace:SharedLibrary.Controls"
xmlns:sharedConverter="clr-namespace:SharedLibrary.Converter"
```

Having multiple XML namespaces (aliases) for basically the same thing, is a real pain and messy. Of cause you could just move all classes to the shared library for better control, but this is also bad if there are application specific classes involved, and in the end nothing is fixed.

While I was looking for a solution, I found the [XmlnsDefinitionAttribute](https://msdn.microsoft.com/en-us/library/system.windows.markup.xmlnsdefinitionattribute(v=vs.110).aspx) class. With it, it allowes you to map multiple namespaces to a single (or multiple) XAML identifier, that you then can use in you XAML files.

## Attribute usage

The XmlnsDefinition attribute has one constructor that takes to string parameters:

- `xmlNamespace` The XAML namespace identifier.
- `clrNamespace` A string that references a CLR namespace name.

_How to use the XmlnsDefinition attribute?_

```
[assembly: XmlnsDefinition("http://dalstroem.com", "SharedLibrary.Controls")]
[assembly: XmlnsDefinition("http://dalstroem.com", "SharedLibrary.Converter")]
```

## Limitations

Because of the way a project is build, the XAML identifier cannot be used in the local assembly. You can only use identifiers from another assemblies, because XAML files must be parsed before the assembly is build.
