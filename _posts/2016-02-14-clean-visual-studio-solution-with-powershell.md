---
title: Clean Visual Studio solution with PowerShell
layout: post
date: 2016-02-14 11:37:24 +0100
tags: [visual studio, powershell]
---
Sometimes when I work in Visual Studio, I need to remove all unnecessary files and folders from a solution. But unfortunately there are no build-in feature to do this. The closest option is the "Clean solution", but as you may know, this only cleans the content in the `bin` folder.

To overcome this issue, I use this script to find and remove files and folders.

```powershell
$include = @("*.suo", "*.user", "*.userosscache", "*.sln.docstates", ".vs", "bin", "obj", "build")
$exclude = @()

$items = Get-ChildItem . -Recurse -Force -Include $include -Exclude $exclude

foreach ($item in $items) {
    Remove-Item $item.FullName -Force -Recurse -ErrorAction SilentlyContinue
    Write-Host "Deleted " $item.FullName
}
```

The script will find everything matching the `$include` variable. If there is anything you need to keep, place it in the `$exclude` variable.

To use the script, copy the above content and create a `.ps1` file. Then place the file in the same directory as your `.sln` file, and run it.
