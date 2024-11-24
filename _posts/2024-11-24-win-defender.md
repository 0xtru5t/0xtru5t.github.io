---
title: "Explore Defender"
date: 2024-11-24 00:00 +0500
categories: [Windows Defender]
tags: [Windows]
---

## Story Behind
While researching Windows Defender, I discovered an interesting command that allows checking AV exclusion paths with low-privileged access which led me to develop a tool for scanning excluded folders and uncovering some interesting behaviors.

## Key Findings

### 1. Persistent Exclusion Paths
- Excluded folder paths remain in Defender's exclusion list even after folder deletion
- Creating a new folder with the same path inherits the exclusion status

### 2. File-Level Exclusions
- Deleted files that were previously excluded maintain their path exclusion
- New files created with the exact same name and path inherit the exclusion
- Example: If `Enum Exclusion.exe` was previously excluded and deleted, placing a new `Enum Exclusion.exe` in the same location bypasses detection

![File Exclusion Example](/assets/images/1.jpg)
![Detection Example](/assets/images/2.jpg)

### 3. File Overwrite Behavior
- Files in excluded paths can be overwritten while maintaining exclusion status
- Requires appropriate file system privileges

![Overwrite Example](/assets/images/3.jpg)

## Tool
For detailed exploration of excluded paths, check out the scanning tool: [win-defender-scan](https://github.com/0x-trust/win-defender-scan)