---
title: Restrizioni relative al modello di programmazione dell'integrazione CLR | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 039afe6cbe5892d2422eec3c92a4d2bb942d5de0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062674"
---
# <a name="clr-integration-programming-model-restrictions"></a>Restrizioni relative al modello di programmazione dell'integrazione con CLR
  Quando si compila una stored procedure gestita o un altro oggetto di database gestito, vi sono determinati controlli del codice eseguiti da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esegue i controlli sull'assembly del codice gestito quando viene innanzitutto registrata nel database, utilizzando il `CREATE ASSEMBLY` istruzione e anche in fase di esecuzione. Il controllo del codice gestito viene effettuato anche in fase di esecuzione in quanto è possibile che in un assembly siano presenti percorsi di codice mai raggiunti in questa fase.  Tale controllo offre quindi la flessibilità necessaria per registrare soprattutto assembly di terze parti, in modo da evitare che un assembly venga bloccato in presenza di codice considerato poco sicuro, progettato per essere eseguito in un ambiente client, ma mai nel CLR hosted. Il codice gestito deve soddisfare i requisiti dipendono indica se l'assembly viene registrato come `SAFE`, `EXTERNAL_ACCESS`, o `UNSAFE`, `SAFE` in corso il più restrittivo e sono elencate di seguito.  
  
 Oltre alle restrizioni inserite negli assembly del codice gestito, vengono concesse anche delle autorizzazioni di sicurezza da accesso di codice. Common Language Runtime (CLR) supporta un modello di sicurezza definito sicurezza dall'accesso di codice per il codice gestito che prevede che le autorizzazioni vengano concesse agli assembly in base all'identità del codice. Gli assembly `SAFE`, `EXTERNAL_ACCESS` e `UNSAFE` presentano autorizzazioni di protezione dall'accesso di codice diverse. Per altre informazioni, vedere [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).  
  
## <a name="create-assembly-checks"></a>Controlli CREATE ASSEMBLY  
 Durante l'esecuzione dell'istruzione `CREATE ASSEMBLY`, per ogni livello di sicurezza vengono eseguiti i controlli seguenti.  Se un controllo non riesce, non è possibile completare l'esecuzione di `CREATE ASSEMBLY` e viene visualizzato un messaggio di errore.  
  
### <a name="global-any-security-level"></a>Globale (qualsiasi livello di sicurezza)  
 Tutti gli assembly a cui si fa riferimento devono soddisfare uno o più dei criteri seguenti:  
  
-   L'assembly è già registrato nel database.  
  
-   L'assembly è uno degli assembly supportati. Per altre informazioni, vedere [librerie di .NET Framework supportata](supported-net-framework-libraries.md).  
  
-   Si utilizza `CREATE ASSEMBLY FROM`  *\<posizione >,* e tutti gli assembly di riferimento e le relative dipendenze sono disponibili nelle  *\<percorso >*.  
  
-   Si utilizza `CREATE ASSEMBLY FROM`  *\<byte... >,* e tutti i riferimenti vengono specificati tramite spazio separati byte.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Tutti gli assembly `EXTERNAL_ACCESS` devono soddisfare i criteri seguenti:  
  
-   I campi statici non vengono utilizzati per archiviare informazioni. Sono consentiti campi statici di sola lettura.  
  
-   Il test di PEVerify viene superato. Lo strumento PEVerify (peverify.exe) che verifica che il codice MSIL e i metadati associati soddisfino i requisiti di indipendenza dai tipi, viene fornito insieme a .NET Framework SDK.  
  
-   La sincronizzazione, ad esempio con la classe `SynchronizationAttribute`, non viene utilizzata.  
  
-   I metodi del finalizzatore non vengono utilizzati.  
  
 Gli attributi personalizzati seguenti non sono consentiti negli assembly `EXTERNAL_ACCESS`:  
  
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
  
-   Tutte le condizioni dell'assembly `EXTERNAL_ACCESS` vengono controllate.  
  
## <a name="runtime-checks"></a>Controlli runtime  
 In fase di esecuzione l'assembly del codice viene esaminato per verificare la presenza delle condizioni riportate di seguito. Se ne viene riscontrata una, non verrà consentita l'esecuzione del codice gestito e sarà generata un'eccezione.  
  
### <a name="unsafe"></a>UNSAFE  
 Il caricamento di un assembly, in modo esplicito mediante la chiamata del metodo `System.Reflection.Assembly.Load()` da una matrice di byte o in modo implicito attraverso l'utilizzo dello spazio dei nomi `Reflection.Emit`, non è consentito.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Tutte le condizioni di `UNSAFE` vengono controllate.  
  
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
  
 Per ulteriori informazioni su attributi di protezione host e un elenco di tipi non consentiti e membri nell'assembly supportati, vedere [attributi di protezione Host e programmazione CLR Integration](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
### <a name="safe"></a>SAFE  
 Tutte le condizioni di `EXTERNAL_ACCESS` vengono controllate.  
  
## <a name="see-also"></a>Vedere anche  
 [Librerie .NET Framework supportate](supported-net-framework-libraries.md)   
 [Sicurezza di accesso di codice dell'integrazione CLR](../security/clr-integration-code-access-security.md)   
 [Attributi di protezione host e programmazione dell'integrazione con CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Creazione di un assembly](../assemblies/creating-an-assembly.md)  
  
  