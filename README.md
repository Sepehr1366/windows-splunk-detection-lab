# Windows Splunk Detection Lab

A hands-on detection engineering lab focused on collecting Windows process telemetry with Sysmon, ingesting the data into Splunk, and investigating suspicious PowerShell activity.

## Overview

This lab demonstrates a basic Windows security monitoring and detection workflow:

1. Configure a Windows endpoint with Sysmon.
2. Verify that Splunk and Sysmon are running.
3. Generate Windows process activity.
4. Ingest the telemetry into Splunk.
5. Identify Windows process creation events.
6. Investigate suspicious PowerShell execution.
7. Use Splunk Search Processing Language (SPL) to isolate relevant events.

The goal is to demonstrate the practical workflow of moving from **endpoint telemetry → SIEM ingestion → investigation → detection**.

---

## Lab Environment

| Component | Environment |
|---|---|
| Operating System | Windows 11 Pro |
| SIEM | Splunk Enterprise |
| Endpoint Telemetry | Sysmon |
| Query Language | Splunk SPL |
| Architecture | Windows endpoint → Splunk |
----
## 1. Verify Windows Environment

The Windows operating system was verified using PowerShell:

```powershell
Get-CimInstance Win32_OperatingSystem |
    Select-Object Caption, Version
````
## 2. Verify Splunk and Sysmon Services

The Splunk and Sysmon services were checked to confirm that both
components were running correctly:

```powershell
Get-Service | Where-Object {$_.Name -match "Splunk|Sysmon"}
````
##3. Verify Sysmon Telemetry

Recent Sysmon operational events were queried to confirm that Windows
endpoint telemetry was being generated:
```powershell
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" -MaxEvents 5 |
    Select-Object TimeCreated, Id, ProviderName
