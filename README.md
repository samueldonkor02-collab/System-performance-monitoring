# System-performance-monitoring
This section covers using Task Manager to get a full picture of what's actually running on a Windows 11 machine, separating the handful of visible apps from the much larger set of background processes most users never look at.

# Running Process Review (Task Manager Baseline Check)

`Windows 11` `Task Manager` `Processes` `Background Services` `Baselining`

## Overview
This section covers using Task Manager to get a full picture of what's actually running on a Windows 11 machine, separating the handful of visible apps from the much larger set of background processes most users never look at.

## Objective
Get comfortable reading Task Manager's process list beyond just "what's open," and start building a sense of what a normal baseline looks like so unfamiliar or suspicious processes are easier to spot later.

## Environment
* Machine: Windows 11 desktop
* Tool used: Task Manager (Processes tab)
* System load at time of review: 12% CPU, 48% Memory, 3% Disk, 0% Network

## What I Did

### Checking the Apps Section
Task Manager separated things into Apps (3) and Background processes (75). The Apps section only listed Google Chrome, Task Manager itself, and Windows Explorer, which lined up with what was visibly open and in use at the time.

### Scrolling Through Background Processes
The background list was a lot longer than expected at 75 entries, dominated by vendor-specific services tied to the hardware on the machine, things like AMD Crash Defender Service, several ASUS-branded services (Optimization, Switch, ScreenXpert, Software Manager), and Windows security components like Antimalware Service Executable. Almost all of them sat at 0% CPU and under a few MB of memory each.

### Reading Resource Usage Per Process
Sorted mentally by what stood out: Google Chrome was using by far the most memory at 1,840.8 MB across its processes, which made sense given 19 sub-processes were grouped under it. Everything else, especially the background services, used a trivial amount of memory and CPU individually, but the sheer number of them adds up.

### Thinking Through the Baseline
None of the 75 background processes looked out of place, they all traced back to known vendors (AMD, ASUS, Microsoft) rather than anything unrecognized. The exercise was less about finding something wrong and more about establishing what "normal" looks like on this specific machine, so a future unfamiliar process name or an unexpected spike in CPU/Disk/Network would actually stand out.

## What's in This Section

```
screenshots/
01 task manager processes view.png (Task Manager Processes tab, showing Apps and 75 Background processes with resource usage)
```

## Skills I Picked Up
Reading Task Manager's process breakdown (Apps vs. Background processes) rather than just glancing at CPU percentage.
Recognizing vendor-tied background services (AMD, ASUS) as expected noise rather than a threat.
Establishing a resource usage baseline (CPU/Memory/Disk/Network) as a reference point for spotting anomalies later.

## How This Applies in the Real World
Knowing what a clean baseline looks like is a foundational skill for spotting malware or unwanted persistence, since a lot of malicious processes try to blend in with legitimate-looking names or hide inside a long list of background services. Analysts use tools like Task Manager, Process Explorer, or EDR agents to do exactly this kind of triage, comparing what's currently running against a known-good baseline.

## Limitations
This was a surface-level GUI review, not a deep process audit. It didn't verify digital signatures, check process file paths, or cross-reference PIDs against parent processes, all of which would be part of a more thorough investigation.

## References
Task Manager Overview: https://support.microsoft.com/windows/task-manager
Windows Process and Thread Documentation: https://learn.microsoft.com/windows/win32/procthread/processes-and-threads
