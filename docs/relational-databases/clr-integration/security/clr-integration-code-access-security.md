---
title: Sicurezza dall'accesso di codice CLR Integration | Documenti Microsoft
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
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b93a1955adb6f38eebd8de86599e1861a80ff75b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="clr-integration-code-access-security"></a>Sicurezza da accesso di codice dell'integrazione con CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Common Language Runtime (CLR) supporta un modello di sicurezza definito sicurezza dall'accesso di codice per il codice gestito che prevede che le autorizzazioni vengano concesse agli assembly in base all'identità del codice. Per ulteriori informazioni, vedere la sezione relativa alla sicurezza da accesso di codice in .NET Framework SDK (Software Development Kit).  
  
 I criteri di sicurezza che determinano le autorizzazioni concesse agli assembly vengono definiti in tre punti diversi:  
  
-   Criteri del computer: criteri attivi per tutto il codice gestito in esecuzione sul computer nel quale viene installato [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Criteri utente: criteri attivi per il codice gestito ospitato da un processo. Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], i criteri utente sono specifici dell'account di Windows su cui è in esecuzione il servizio di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Criteri host: criteri impostati dall'host di CLR (in questo caso, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]), attivi per il codice gestito in esecuzione su quell'host.  
  
 Il meccanismo di sicurezza da accesso di codice supportato da CLR si basa sul presupposto che il runtime possa ospitare codice completamente o parzialmente attendibile. Le risorse che sono protette dalla sicurezza di accesso di codice CLR in genere vengono eseguito il wrapping da interfacce di programmazione di applicazione gestita che richiedono l'autorizzazione corrispondente prima di consentire l'accesso alla risorsa. La richiesta di autorizzazione viene soddisfatta solo se tutti i chiamanti a livello di assembly nello stack di chiamate dispongono dell'autorizzazione corrispondente per la risorsa.  
  
 Il set di autorizzazioni della sicurezza dell'accesso di codice concesse al codice gestito durante l'esecuzione all'interno di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rappresenta l'intersezione del set di autorizzazioni concesse dai tre livelli di criteri sopra descritti. Anche se [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] concede un set di autorizzazioni a un assembly caricato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il set di autorizzazioni effettivo concesso al codice utente potrebbe essere limitato ulteriormente dai criteri utente e a livello di computer.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Set di autorizzazioni a livello di criteri host di SQL Server  
 Il set di autorizzazioni della sicurezza da accesso di codice concesso agli assembly al livello di criteri host di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è determinato dal set di autorizzazioni specificato durante la creazione dell'assembly. Sono disponibili tre set di autorizzazioni: **provvisoria**, **EXTERNAL_ACCESS** e **UNSAFE** (specificati mediante il **PERMISSION_SET** opzione di [ CREAZIONE di ASSEMBLY &#40; Transact-SQL &#41; ](../../../t-sql/statements/create-assembly-transact-sql.md)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] offre un livello di criteri di sicurezza a livello di host per CLR quando ospita tale ambiente. Questo criterio è un ulteriore livello di criteri di sotto di due livelli di criteri che sono sempre attivi. e viene impostato per ogni dominio applicazione creato da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Non è indicato per il dominio applicazione predefinito che sarebbe attivo quando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crea un'istanza di CLR.  
  
 I criteri a livello host di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono una combinazione dei criteri fissi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per gli assembly di sistema e dei criteri specificati dall'utente per gli assembly utente.  
  
 I criteri fissi per gli assembly CLR e gli assembly di sistema di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] concedono loro l'attendibilità totale.  
  
 La parte dei criteri host di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificata dall'utente è basata su uno dei tre bucket di autorizzazione specificati per ogni assembly dal relativo proprietario. Per ulteriori informazioni sulle autorizzazioni di sicurezza elencate in basso, vedere .NET Framework SDK.  
  
### <a name="safe"></a>SAFE  
 È consentito solo il calcolo interno e l'accesso locale ai dati. **SICURO** è il set di autorizzazioni più restrittivo. Il codice eseguito da un assembly con **provvisoria** autorizzazioni non è possibile accedere alle risorse di sistema esterne, ad esempio file, rete, le variabili di ambiente o il Registro di sistema.  
  
 **SICURO** gli assembly hanno le autorizzazioni e dei valori seguenti:  
  
|Autorizzazione|Valori/Descrizione|  
|----------------|-----------------------------|  
|**SecurityPermission**|**Esecuzione:** dell'autorizzazione per eseguire il codice gestito.|  
|**SqlClientPermission**|**Connessione di contesto = true**, **connessione contesto = yes**: solo la connessione di contesto può essere utilizzata e la stringa di connessione può specificare solo un valore di "connessione di contesto = true" o "connessione di contesto = yes".<br /><br /> **AllowBlankPassword = false:** password vuote non sono consentite.|  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Gli assembly EXTERNAL_ACCESS dispongono delle stesse autorizzazioni come **provvisoria** assembly, con la possibilità aggiuntiva di accedere alle risorse di sistema esterne, ad esempio file, reti, variabili di ambiente e il Registro di sistema.  
  
 **EXTERNAL_ACCESS** assembly dispongono anche delle autorizzazioni e dei valori seguenti:  
  
|Autorizzazione|Valori/Descrizione|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**Unrestricted:** sono consentite le transazioni distribuite.|  
|**DNSPermission**|**Unrestricted:** dell'autorizzazione per richiedere informazioni da server dei nomi di dominio.|  
|**EnvironmentPermission**|**Unrestricted:** completo è consentito l'accesso alle variabili di ambiente utente e di sistema.|  
|**EventLogPermission**|**Amministrare:** sono consentite le azioni seguenti: creazione di un'origine evento, leggere i log esistenti, l'eliminazione di origini evento o log, rispondere alle immissioni, cancellare un log eventi, l'attesa di eventi e l'accesso a una raccolta di tutti i registri eventi.|  
|**FileIOPermission**|**Unrestricted:** accesso completo al file e cartelle è consentito.|  
|**KeyContainerPermission**|**Unrestricted:** completo è consentito l'accesso ai contenitori di chiavi.|  
|**NetworkInformationPermission**|**L'accesso:** è consentito un ping.|  
|**RegistryPermission**|Concede diritti di lettura per **HKEY_CLASSES_ROOT**, **HKEY_LOCAL_MACHINE**, **HKEY_CURRENT_USER**, **HKEY_CURRENT_CONFIG**e  **HKEY_USERS.**|  
|**SecurityPermission**|**Asserzione:** capacità di asserire che tutti i chiamanti del codice dispongono dell'autorizzazione necessaria per l'operazione.<br /><br /> **ControlPrincipal:** possibilità di modificare l'oggetto principal.<br /><br /> **Esecuzione:** dell'autorizzazione per eseguire il codice gestito.<br /><br /> **SerializationFormatter:** possibilità di fornire servizi di serializzazione.|  
|**SmtpPermission**|**L'accesso:** sono consentite le connessioni in uscita porta 25 dell'host SMTP.|  
|**SocketPermission**|**Connettersi:** sono consentite le connessioni in uscita (tutte le porte, tutti i protocolli) su un indirizzo di trasporto.|  
|**SqlClientPermission**|**Unrestricted:** completo è consentito l'accesso all'origine dati.|  
|**StorePermission**|**Unrestricted:** accesso completo al certificato x. 509 è consentito archivi.|  
|**WebPermission**|**Connettersi:** sono consentite le connessioni in uscita a risorse web.|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE concede agli assembly libero accesso a risorse interne ed esterne a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Codice eseguito all'interno un **UNSAFE** assembly può anche chiamare codice non gestito.  
  
 **UNSAFE** gli assembly **FullTrust**.  
  
> [!IMPORTANT]  
>  **SICURO** è l'impostazione di autorizzazioni consigliata per gli assembly che eseguono attività di gestione di calcolo e di dati senza accedere alle risorse esterne [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **EXTERNAL_ACCESS** è consigliata per gli assembly che accedono a risorse esterne [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **EXTERNAL_ACCESS** gli assembly per impostazione predefinita vengono eseguiti come il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account del servizio. È possibile che **EXTERNAL_ACCESS** codice per rappresentare in modo esplicito di contesto di sicurezza di autenticazione di Windows del chiamante. Poiché il valore predefinito è l'esecuzione come il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account del servizio, dell'autorizzazione per eseguire **EXTERNAL_ACCESS** devono essere specificate solo agli account attendibili per l'esecuzione come account del servizio di accesso. Da una prospettiva di sicurezza, **EXTERNAL_ACCESS** e **UNSAFE** gli assembly sono identici. Tuttavia, **EXTERNAL_ACCESS** assembly forniscono vari protezioni di affidabilità e l'affidabilità che non sono in **UNSAFE** assembly. Specifica di **UNSAFE** consente al codice nell'assembly di eseguire operazioni non valide per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] spazio di processo e pertanto compromettere l'affidabilità e la scalabilità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per ulteriori informazioni sulla creazione di assembly CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [la gestione di assembly di integrazione CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Accesso a risorse esterne  
 Se un tipo definito dall'utente (UDT), stored procedure o altro tipo di assembly del costrutto è registrato con il **provvisoria** set di autorizzazioni, quindi l'esecuzione nel costrutto di codice gestito è in grado di accedere alle risorse esterne. Tuttavia, se il valore di **EXTERNAL_ACCESS** o **UNSAFE** set di autorizzazioni e codice gestito tenta di accedere alle risorse esterne, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applica le regole seguenti:  
  
|Se in|Risultato|  
|--------|----------|  
|Il contesto di esecuzione corrisponde a un account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|I tentativi di accesso a risorse esterne vengono negati e viene generata un'eccezione di sicurezza.|  
|Il contesto di esecuzione corrisponde a un account di accesso di Windows e rappresenta il chiamante originale.|L'accesso alla risorsa esterna viene effettuato nel contesto di sicurezza dell'account di servizio di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Il chiamante non è il chiamante originale.|L'accesso viene negato e viene generata un'eccezione di sicurezza.|  
|Il contesto di esecuzione corrisponde a un account di accesso di Windows e rappresenta il chiamante originale, mentre il chiamante è stato rappresentato.|L'accesso verrà effettuato nel contesto di sicurezza del chiamante e non in quello dell'account del servizio.|  
  
## <a name="permission-set-summary"></a>Riepilogo dei set di autorizzazioni  
 Il grafico seguente sono riepilogate le restrizioni e autorizzazioni di **provvisoria**, **EXTERNAL_ACCESS**, e **UNSAFE** set di autorizzazioni.  
  
|||||  
|-|-|-|-|  
||**SAFE**|**EXTERNAL_ACCESS**|**UNSAFE**|  
|**Autorizzazioni di sicurezza di accesso di codice**|Sola esecuzione|Esecuzione più accesso a risorse esterne|Senza restrizioni (incluso P/Invoke)|  
|**Restrizioni del modello di programmazione**|Sì|Sì|Nessuna restrizione|  
|**Requisito di verificabilità**|Sì|Sì|no|  
|**Accesso ai dati locali**|Sì|Sì|Sì|  
|**Possibilità di chiamare codice nativo**|no|No|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza dell'integrazione con CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Attributi di protezione host e programmazione dell'integrazione con CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Restrizioni del modello di programmazione integrazione CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Ambiente CLR](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
