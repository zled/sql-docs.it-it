---
title: Creazione di un Assembly | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
caps.latest.revision: 27
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3b22443461b5bb11d4e4ca1933d4f1d1f931fda9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="creating-an-assembly"></a>Creazione di un assembly
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Gli oggetti di database gestiti, ad esempio le stored procedure o i trigger, vengono compilati e quindi distribuiti in unità denominate assembly. Gli assembly DLL gestiti devono essere registrati in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prima di poter utilizzare le funzionalità fornite dall'assembly. Per registrare l'assembly in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], utilizzare l'istruzione CREATE ASSEMBLY. In questo argomento viene descritto come registrare un assembly in un database tramite l'istruzione CREATE ASSEMBLY e specificare le impostazioni di sicurezza per l'assembly.  
  
## <a name="the-create-assembly-statement"></a>Istruzione CREATE ASSEMBLY  
 L'istruzione CREATE ASSEMBLY viene utilizzata per creare un assembly in un database. Esempio:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 La clausola FROM specifica il percorso dell'assembly da creare. Questo percorso può essere un percorso UNC (Universal Naming Convention) o un percorso di file fisico locale rispetto al computer.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non consente la registrazione di versioni diverse di un assembly con lo stesso nome, lingua e chiave pubblica.  
  
 È possibile creare assembly che fanno riferimento ad altri assembly. Quando si crea un assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crea anche gli assembly cui fa riferimento l'assembly di livello radice, se non sono già stati creati nel database.  
  
 Agli utenti del database o ai ruoli utente vengono concesse autorizzazioni per creare, e pertanto possedere, assembly in un database. Per creare assembly, l'utente o il ruolo del database deve disporre dell'autorizzazione CREATE ASSEMBLY.  
  
 Un assembly può fare riferimento ad altri assembly solo nei casi seguenti:  
  
-   L'assembly chiamato o cui si fa riferimento è di proprietà dello stesso utente o ruolo.  
  
-   L'assembly chiamato o cui si fa riferimento è stato creato nello stesso database.  
  
## <a name="specifying-security-when-creating-assemblies"></a>Configurazione della sicurezza durante la creazione di assembly  
 Durante la creazione di un assembly in un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, è possibile specificare uno dei tre diversi livelli di sicurezza in cui è possibile eseguire il codice: **provvisoria**, **EXTERNAL_ACCESS**, o **UNSAFE** . Quando il **CREATE ASSEMBLY** viene eseguita l'istruzione, vengono effettuati alcuni controlli sull'assembly del codice che potrebbe causare l'assembly a non riuscire registrare il server. Per ulteriori informazioni, vedere l'esempio di rappresentazione in [CodePlex](http://msftengprodsamples.codeplex.com/).  
  
 **SICURO** è il set di autorizzazioni predefinito e funziona per la maggior parte degli scenari. Per specificare un determinato livello di sicurezza, è necessario modificare la sintassi dell'istruzione CREATE ASSEMBLY come indicato di seguito:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 È anche possibile creare un assembly con il **provvisoria** autorizzazione impostata omettendo semplicemente la terza riga del codice precedente:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Quando viene eseguito codice in un assembly di **provvisoria** autorizzazione impostata, è possibile eseguire solo calcoli e accesso ai dati all'interno del server tramite il provider gestito in-process.  
  
### <a name="creating-externalaccess-and-unsafe-assemblies"></a>Creazione di assembly EXTERNAL_ACCESS e UNSAFE  
 **EXTERNAL_ACCESS** per gli scenari in cui il codice deve accedere a risorse esterne al server, ad esempio file, rete, del Registro di sistema e le variabili di ambiente. Ogni volta che il server accede a una risorsa esterna, rappresenta il contesto di sicurezza dell'utente che chiama il codice gestito.  
  
 **UNSAFE** autorizzazione per il codice è per i casi in cui un assembly non è effettivamente protetto o richiede accesso aggiuntivo a risorse limitate, ad esempio il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] API Win32.  
  
 Per creare un **EXTERNAL_ACCESS** o **UNSAFE** assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], deve essere soddisfatta una delle due condizioni seguenti:  
  
1.  L'assembly è firmato con nome sicuro o dispone di firma Authenticode con un certificato. Questo nome sicuro (o certificato) viene creato all'interno [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come asimmetrica chiave (o certificato), e ha un account di accesso corrispondente con **EXTERNAL ACCESS ASSEMBLY** autorizzazioni (per assembly di accesso esterno) o  **ASSEMBLY UNSAFE** autorizzazioni (per assembly unsafe).  
  
2.  Il proprietario del database (DBO) dispone **EXTERNAL ACCESS ASSEMBLY** (per **accesso esterno** assembly) o **ASSEMBLY UNSAFE** (per **UNSAFE** autorizzazione assembly) e il database ha il [proprietà di Database TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md) impostato su **ON**.  
  
 Le due condizioni elencate in precedenza vengono verificate in fase di caricamento dell'assembly (fase che include l'esecuzione). Per caricare l'assembly, è necessario che si verifichi almeno una delle due condizioni.  
  
 È consigliabile che il [proprietà di Database TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md) in un database di non essere impostato su **ON** solo per l'esecuzione di common language runtime (CLR) di codice nel processo server. È invece consigliabile creare una chiave asimmetrica dal file di assembly nel database master. Quindi è necessario creare un account di accesso mappato a questa chiave asimmetrica, e l'account di accesso devono essere concesse **EXTERNAL ACCESS ASSEMBLY** o **ASSEMBLY UNSAFE** autorizzazione.  
  
 Nell'esempio [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzioni consentono di eseguire i passaggi necessari per creare una chiave asimmetrica, eseguire il mapping di un account di accesso a questa chiave e quindi concedere **EXTERNAL_ACCESS** dell'autorizzazione per l'account di accesso. Prima di eseguire l'istruzione CREATE ASSEMBLY, è necessario eseguire le istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] seguenti.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  È necessario creare un nuovo account di accesso da associare alla chiave asimmetrica. Questo account di accesso viene utilizzato solo per concedere le autorizzazioni e non è necessario che sia associato a un utente o utilizzato nell'applicazione.  
  
 Per creare un **accesso esterno** assembly, è necessario disporre di **accesso esterno** autorizzazione. Questa autorizzazione viene specificata durante la creazione dell'assembly:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Nell'esempio [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzioni consentono di eseguire i passaggi necessari per creare una chiave asimmetrica, eseguire il mapping di un account di accesso a questa chiave e quindi concedere **UNSAFE** dell'autorizzazione per l'account di accesso. Prima di eseguire l'istruzione CREATE ASSEMBLY, è necessario eseguire le istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] seguenti.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Per specificare che un assembly viene caricato con **UNSAFE** autorizzazione, specificare il **UNSAFE** set di autorizzazioni durante il caricamento dell'assembly nel server:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Per ulteriori informazioni sulle autorizzazioni per ognuna delle impostazioni, vedere [sicurezza dell'integrazione con CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione degli assembly di integrazione con CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Modifica di un Assembly](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [Eliminazione di un Assembly](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [Sicurezza di accesso di codice dell'integrazione CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Proprietà di database TRUSTWORTHY](../../../relational-databases/security/trustworthy-database-property.md)   
 [Chiamanti consentendo parzialmente attendibili](http://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
  
  
