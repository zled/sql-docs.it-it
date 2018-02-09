---
title: Restrizioni del modello di programmazione dell'integrazione CLR | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d282b317a5ea31fe8170a847f5b425bcd1af4fd
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="clr-integration-programming-model-restrictions"></a>Restrizioni relative al modello di programmazione dell'integrazione con CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Quando si compila una stored procedure gestita o un altro oggetto di database gestito, esistono alcuni controlli di codice eseguiti da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che devono essere considerati. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]esegue controlli sull'assembly del codice gestito quando viene innanzitutto registrata nel database, utilizzando il **CREATE ASSEMBLY** istruzione e anche in fase di esecuzione. Il controllo del codice gestito viene effettuato anche in fase di esecuzione in quanto è possibile che in un assembly siano presenti percorsi di codice mai raggiunti in questa fase.  Tale controllo offre quindi la flessibilità necessaria per registrare soprattutto assembly di terze parti, in modo da evitare che un assembly venga bloccato in presenza di codice considerato poco sicuro, progettato per essere eseguito in un ambiente client, ma mai nel CLR hosted. Il codice gestito deve soddisfare i requisiti dipendono se l'assembly viene registrato come **provvisoria**, **EXTERNAL_ACCESS**, o **UNSAFE**, **SAFE** il più rigoroso e sono elencati di seguito.  
  
 Oltre alle restrizioni inserite negli assembly del codice gestito, vengono concesse anche delle autorizzazioni di sicurezza da accesso di codice. Common Language Runtime (CLR) supporta un modello di sicurezza definito sicurezza dall'accesso di codice per il codice gestito che prevede che le autorizzazioni vengano concesse agli assembly in base all'identità del codice. **SICURO**, **EXTERNAL_ACCESS**, e **UNSAFE** assembly autorizzazioni diverse autorità di certificazione. Per ulteriori informazioni, vedere [sicurezza dall'accesso di codice CLR Integration](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Controlli CREATE ASSEMBLY  
 Quando il **CREATE ASSEMBLY** viene eseguita l'istruzione, vengono eseguiti i controlli seguenti per ogni livello di sicurezza.  Se un controllo non riesce, **CREATE ASSEMBLY** avrà esito negativo con un messaggio di errore.  
  
### <a name="global-any-security-level"></a>Globale (qualsiasi livello di sicurezza)  
 Tutti gli assembly a cui si fa riferimento devono soddisfare uno o più dei criteri seguenti:  
  
-   L'assembly è già registrato nel database.  
  
-   L'assembly è uno degli assembly supportati. Per ulteriori informazioni, vedere [librerie di .NET Framework supportata](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
-   Si utilizza **CREATE ASSEMBLY FROM * * *\<posizione >,* e tutti gli assembly di riferimento e le relative dipendenze sono disponibili in  *\<percorso >*.  
  
-   Si utilizza **CREATE ASSEMBLY FROM * * *\<byte... >,* e tutti i riferimenti vengono specificati tramite spazio separati byte.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Tutti **EXTERNAL_ACCESS** assembly devono soddisfare i criteri seguenti:  
  
-   I campi statici non vengono utilizzati per archiviare informazioni. Sono consentiti campi statici di sola lettura.  
  
-   Il test di PEVerify viene superato. Lo strumento PEVerify (peverify.exe) che verifica che il codice MSIL e i metadati associati soddisfino i requisiti di indipendenza dai tipi, viene fornito insieme a .NET Framework SDK.  
  
-   La sincronizzazione, ad esempio con il **SynchronizationAttribute** classe, non viene utilizzata.  
  
-   I metodi del finalizzatore non vengono utilizzati.  
  
 Gli attributi personalizzati seguenti non sono consentiti negli **EXTERNAL_ACCESS** assembly:  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   Tutti **EXTERNAL_ACCESS** vengono verificate le condizioni dell'assembly.  
  
## <a name="runtime-checks"></a>Controlli runtime  
 In fase di esecuzione l'assembly del codice viene esaminato per verificare la presenza delle condizioni riportate di seguito. Se ne viene riscontrata una, non verrà consentita l'esecuzione del codice gestito e sarà generata un'eccezione.  
  
### <a name="unsafe"></a>UNSAFE  
 Caricamento di un assembly, in modo esplicito chiamando il **System.Reflection.Assembly.Load()** metodo da una matrice di byte o in modo implicito tramite l'utilizzo di **Emit** dello spazio dei nomi, non è consentito.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Tutti **UNSAFE** condizioni vengono verificate.  
  
 Tutti i tipi e i metodi annotati con i valori dell'attributo di protezione host riportati di seguito dell'elenco supportato di assembly non sono consentiti.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Per ulteriori informazioni su attributi di protezione host e un elenco di tipi non consentiti e membri nell'assembly supportati, vedere [attributi di protezione Host e programmazione CLR Integration](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Tutti **EXTERNAL_ACCESS** condizioni vengono verificate.  
  
## <a name="see-also"></a>Vedere anche  
 [Librerie .NET Framework supportate](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [Sicurezza di accesso di codice dell'integrazione CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Attributi di protezione host e programmazione dell'integrazione con CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Creazione di un Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
