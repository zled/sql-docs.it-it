---
title: Programmazione dell'integrazione con CLR e attributi di protezione host | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4caf403fe2fee4b43031efd387a170aae3de1353
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Attributi di protezione host e programmazione dell'integrazione con CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Common language runtime (CLR) fornisce un meccanismo per annotare gestito application programming interface (API) che fanno parte di .NET Framework con determinati attributi che possono interessare un host di CLR, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Di seguito sono riportati alcuni esempi di attributi di protezione host:  
  
-   **SharedState**, che indica se l'API espone la possibilità di creare o gestire lo stato (ad esempio campi classe statici) di condiviso.  
  
-   **Sincronizzazione**, che indica se l'API espone la possibilità di eseguire la sincronizzazione tra thread.  
  
-   **ExternalProcessMgmt**, che indica se l'API espone un modo per controllare il processo host.  
  
 Sulla base di tali attributi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specifica un elenco di attributi di protezione host non consentiti nell'ambiente host attraverso la sicurezza da accesso di codice. I requisiti di autorità di certificazione vengono specificati da uno dei tre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di autorizzazioni: **provvisoria**, **EXTERNAL_ACCESS**, o **UNSAFE**. Uno dei tre livelli di sicurezza viene specificato quando l'assembly viene registrato nel server, utilizzando il **CREATE ASSEMBLY** istruzione. L'esecuzione di codice all'interno di **provvisoria** o **EXTERNAL_ACCESS** set di autorizzazioni necessario evitare alcuni tipi o membri che hanno il **System.Security.Permissions.HostProtectionAttribute** attributo applicato. Per ulteriori informazioni, vedere [creazione di un Assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) e [restrizioni del modello di programmazione integrazione CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 Il **HostProtectionAttribute** non è un'autorizzazione di sicurezza come costruisce un modo per migliorare l'affidabilità, in quanto identifica il codice specifico, tipi o metodi, che l'host possono essere disattivati. L'utilizzo del **HostProtectionAttribute** applica un modello di programmazione che consente di proteggere la stabilità dell'host.  
  
## <a name="host-protection-attributes"></a>Attributi di protezione host  
 Gli attributi di protezione host identificano i tipi o i membri non inclusi nel modello di programmazione host e rappresentano i livelli di pericolo per l'affidabilità, riportati di seguito in ordine crescente di gravità:  
  
-   Sono altrimenti innocui.  
  
-   Possono determinare la destabilizzazione del codice utente gestito dal server.  
  
-   Possono determinare la destabilizzazione del processo del server stesso.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]non consente l'utilizzo di un tipo o membro che dispone di un **HostProtectionAttribute** che specifica un **System.Security.Permissions.HostProtectionResource** enumerazione con un valore di  **ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**,  **SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **sincronizzazione**, o **dell'interfaccia utente**. In questo modo si impedisce agli assembly di chiamare membri che attivano la condivisione dello stato, eseguono la sincronizzazione, possono determinare una perdita di risorse al termine del processo o compromettere l'integrità del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Tipi e membri non consentiti  
 Gli argomenti seguenti identificano i tipi e membri i cui **HostProtectionResource** valori non sono consentiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Gli elenchi presenti in questi argomenti sono stati generati dagli assembly supportati.  Per ulteriori informazioni, vedere [librerie di .NET Framework supportata](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Tipi e membri non consentiti in Microsoft.VisualBasic.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Vengono elencati i tipi e i membri di Microsoft.VisualBasic.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
 [Tipi e membri non consentiti in mscorlib.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)  
 Elenca i tipi e i membri in mscorlib.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
 [Tipi e membri non consentiti in System.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)  
 Elenca i tipi e i membri in System.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
 [Tipi e membri non consentiti in System.Data.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)  
 Elenca i tipi e i membri in System.Data.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
 [Tipi e membri non consentiti in System.Core.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
 Elenca i tipi e i membri in System.Core.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza di accesso di codice dell'integrazione CLR](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Restrizioni del modello di programmazione integrazione CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Creazione di un assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
