# Windows Splunk Detection Lab

## Overview

A hands-on cybersecurity detection engineering lab focused on Windows process creation and PowerShell activity using Splunk.

## Objectives

- Ingest Windows security telemetry into Splunk
- Search and analyze Windows Event ID 4688
- Detect suspicious PowerShell execution
- Write SPL detection queries
- Investigate process, parent process, user, and host activity
- Build a foundation for security alerting and threat hunting

## Tools

- Splunk Enterprise
- Windows
- PowerShell
- Windows Event ID 4688
- Sysmon / Windows process telemetry
- SPL (Search Processing Language)

## Detection Scenario

The lab investigates suspicious PowerShell execution using:

- PowerShell
- `-NoProfile`
- `-EncodedCommand`
- Process creation telemetry
- Parent process information

## Investigation Example

The lab identified a PowerShell process executed from:

`C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

The observed command line contained an encoded PowerShell command.

## Status

Project 2 — Detection Engineering Lab

Work in progress.
