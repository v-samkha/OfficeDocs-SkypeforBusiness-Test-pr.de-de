﻿---
title: Remove-CsEnhancedEmergencyServiceDisclaimer
TOCTitle: Remove-CsEnhancedEmergencyServiceDisclaimer
ms:assetid: 30a5aa8c-04b8-4c1f-92b3-88c86bf69a52
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg425810(v=OCS.15)
ms:contentKeyID: 49293582
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsEnhancedEmergencyServiceDisclaimer

 

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Removes the disclaimer text that is used globally to prompt for location information for an Enhanced 9-1-1 (E9-1-1) implementation. Dieses Cmdlet wurde in Lync Server 2010 eingeführt.

## Syntax

    Remove-CsEnhancedEmergencyServiceDisclaimer -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Examples

## EXAMPLE 1

This command removes the text of the enhanced emergency service disclaimer. Note that this does not remove the global disclaimer; it still exists. It simply sets the Body property to an empty string.

    Remove-CsEnhancedEmergencyServiceDisclaimer -Identity global

## Detailed Description

In order for an Enterprise Voice implementation to provide E9-1-1 service, locations must be mapped to ports, subnets, switches, and wireless access points to identify the caller’s location. When the caller is connecting from outside one of these mapped points, he must enter his location manually for it to be received by emergency services. This cmdlet removes the text string that will be displayed to users who choose not to enter their location information. This message will be displayed only if the LocationRequired property of the user’s location policy is set to Disclaimer. (You can retrieve location policy settings by calling the **Get-CsLocationPolicy** cmdlet.) After calling this cmdlet, a blank message will be displayed to users in this case.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsEnhancedEmergencyServiceDisclaimer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsEnhancedEmergencyServiceDisclaimer"}

## Parameter


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>This value is required and must be set to Global.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Fordert Sie vor der Ausführung des Befehls zum Bestätigen auf.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Beschreibt die Auswirkungen einer Ausführung des Befehls, ohne den Befehl tatsächlich auszuführen.</p></td>
</tr>
</tbody>
</table>


## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer object. Accepts pipelined input of an enhanced emergency service disclaimer object.

## Return Types

This cmdlet does not return a value or an object. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer.

## Siehe auch

#### Weitere Ressourcen

[Set-CsEnhancedEmergencyServiceDisclaimer](set-csenhancedemergencyservicedisclaimer.md)  
[Get-CsEnhancedEmergencyServiceDisclaimer](get-csenhancedemergencyservicedisclaimer.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)
