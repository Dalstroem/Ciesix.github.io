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

This is where the `XmlnsDefinition` attribute comes in.

```csharp
public XmlnsDefinitionAttribute(string xmlNamespace, string clrNamespace)
```

The `xmlNamespace` is the namespace identifier used in the XAML file, and `clrNamespace` is a reference to a CLR namespace name.

If you add the following code-snippet to the `AssemblyInfo.cs` file of the shared library, you can map multiple namespaces into a single XML namespace that you can use in your XAML files.

```csharp
[assembly: XmlnsDefinition("http://dalstroem.com", "SharedLibrary")]
[assembly: XmlnsDefinition("http://dalstroem.com", "SharedLibrary.Controls")]
[assembly: XmlnsDefinition("http://dalstroem.com", "SharedLibrary.Converter")]
```

In the example above, my XAML identifier is "http://dalstroem.com" and when it is used in a XAML file like this:

```
xmlns:core="http://dalstroem.com"
```
