---
title: XML namespace definition mapping
layout: post
#date: 0000-01-01 00:00:00 +0000
tags: [c#, xaml, xml]
---
A few days ago I discovered a pretty neat feature, when I was using XML namespaces in a XAML file. I have properly done this a few thousand times before. But one thing that have always annoyed me, is setups like this:

```
xmlns:converter="clr-namespace:Application.Converter"
xmlns:sharedConverter="clr-namespace:SharedLibrary.Converter"
```

Having multiple XML namespaces (aliases) for basically the same thing, is a real pain and messy. Of cause you could just move all converters to the shared library, but this is also bad if there are application specific classes involved.

If you add the following code-snippet in the `AssemblyInfo.cs` file of the shared library, you can map multiple namespaces into a single XML namespace that you can use in your XAML files.

```csharp
[assembly: XmlnsDefinition("http://dalstroem.com", "SharedLibrary")]
[assembly: XmlnsDefinition("http://dalstroem.com", "SharedLibrary.Controls")]
[assembly: XmlnsDefinition("http://dalstroem.com", "SharedLibrary.Converter")]
```
