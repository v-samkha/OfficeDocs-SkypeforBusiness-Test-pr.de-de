﻿---
title: Cmdlets, in denen der Parameter "Tenant" verwendet wird
TOCTitle: Cmdlets, in denen der Parameter "Tenant" verwendet wird
ms:assetid: e7fe7c12-fbe0-49c1-9e8c-eef6958f27d0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn362850(v=OCS.15)
ms:contentKeyID: 56269350
ms.date: 06/01/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets, in denen der Parameter \"Tenant\" verwendet wird

 

_**Letztes Änderungsdatum des Themas:** 2015-06-22_

Wenn Sie Ihre Einstellungen für öffentliche Anbieter ändern, müssen Sie immer eine Mandantenidentität bereitstellen, und zwar selbst dann, wenn Sie nur einen einzigen Mandanten haben. Beispielsweise wird mit dem folgenden Befehl Windows Live als der einzige öffentliche Anbieter festgelegt, über den Ihre Benutzer kommunizieren dürfen:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

Glücklicherweise müssen Sie die Mandanten-ID (hier beispielsweise bf19b7db-6960-41e5-a139-2aa373474354) nicht jedes Mal eingeben, wenn Sie eines dieser Cmdlets ausführen. Stattdessen können Sie die Mandanten-ID abrufen, indem Sie das Cmdlet [Get-CsTenant](get-cstenant.md) ausführen, die Mandanten-ID in einer Variablen speichern und dann diese Variable verwenden, wenn Sie eines der anderen Cmdlets aufrufen. Zum Beispiel:

    $x = (Get-CsTenant).TenantId
    Set-CsTenantPublicProvider -Tenant $x -Provider "WindowsLive"

Alternativ können Sie dies in einem einzigen Befehl ausführen, indem Sie die Mandanten-ID abrufen und diesen Wert dann an das Cmdlet **Set-CsTenantPublicProvider** weiterleiten:

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Set-CsTenantPublicProvider -Tenant $_.TenantId -Provider "WindowsLive"}

Sie müssen die Mandanten-ID nicht angeben, wenn Sie das Cmdlet **Get-CsTenant** aufrufen. Der folgende Befehl gibt Informationen zu Ihrem Mandanten zurück:

    Get-CsTenant

Für die folgenden Cmdlets kann eine Mandantenidentität angegeben werden. Der Parameter ist in diesen Fällen aber optional und muss nicht angegeben werden, wenn das jeweilige Cmdlet aufgerufen wird. Stattdessen gibt Windows PowerShell die Mandanten-ID für Sie anhand des Skype for Business Online-Mandanten eine, mit dem Sie aktuell verbunden sind:

  - [Get-CsTenant](get-cstenant.md)

  - [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

  - [Set-CsTenantHybridConfiguration](set-cstenanthybridconfiguration.md)

  - [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)

  - [Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)

  - [Get-CsTenantLicensingConfiguration](get-cstenantlicensingconfiguration.md)

Beispielsweise kann das Cmdlet **Get-CsTenantFederationConfiguration** mit diesem Befehl aufgerufen werden:

    Get-CsTenantFederationConfiguration

Obwohl der Parameter **Tenant** nicht erforderlich ist, können Sie ihn in einem Aufruf von **Get-CsTenantFederationConfiguration** angeben:

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

## Siehe auch

#### Konzepte

[Identitäten, Bereiche und Mandanten](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Die Lync Online-Cmdlets](the-skype-for-business-online-cmdlets.md)

