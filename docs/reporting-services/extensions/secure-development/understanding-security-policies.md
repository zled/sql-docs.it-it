---
title: Informazioni sui criteri di sicurezza | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services], security policies
- Execution permission set
- custom assemblies [Reporting Services], security
- permission sets [Reporting Services]
- expressions [Reporting Services], security
- evidence [Reporting Services]
- FullTrust permission set
- security policies [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: a9bf043a-139a-4929-9a58-244815323df0
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 4c8fa977e2b9cdd596e3029be4954daea7fe239d
ms.contentlocale: it-it
ms.lasthandoff: 08/12/2017

---
# <a name="understanding-security-policies"></a>Informazioni sui criteri di sicurezza
  Qualsiasi codice eseguito da un server di report deve far parte di criteri di sicurezza dall'accesso di codice specifici. Tali criteri di sicurezza sono costituiti da gruppi di codice che eseguono il mapping dell'evidenza a un insieme di set di autorizzazioni denominati. I gruppi di codice sono spesso associati a un set di autorizzazioni denominato che specifica le autorizzazioni consentite per il codice appartenente al gruppo specifico. In fase di esecuzione l'evidenza viene usata da un host trusted o dal caricatore per determinare i gruppi di codice cui il codice appartiene e, di conseguenza, le autorizzazioni per concedere il codice. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]rispetti questa architettura di criteri di sicurezza come definito dal [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime (CLR). Nelle sezioni seguenti vengono descritti i diversi tipi di codice in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e le regole dei criteri associate.  
  
## <a name="report-server-assemblies"></a>Assembly del server di report  
 Gli assembly del server di report contengono codice incluso nel prodotto [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] viene scritto usando assembly del codice gestito. Tutti questi assembly hanno un nome sicuro, ossia sono firmati digitalmente. I gruppi di codice per questi assembly vengono definiti utilizzando il **StrongNameMembershipCondition**, che fornisce evidenza basata sulle informazioni sulla chiave pubbliche con nome sicuro dell'assembly. Il gruppo di codice viene concesso il **FullTrust** set di autorizzazioni.  
  
## <a name="report-server-extensions-rendering-data-delivery-and-security"></a>Estensioni del server di report (rendering, dati, recapito e sicurezza)  
 Le estensioni del server di report sono estensioni per dati personalizzati, per il recapito, per il rendering e di sicurezza create dall'utente o da terze parti per estendere le funzionalità di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. È necessario concedere **FullTrust** a queste estensioni o assembly di codice nei file di configurazione dei criteri è associato il [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] componente si estende. Le estensioni fornite come parte di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] vengono firmati con la chiave pubblica del server di report e ricevere la **FullTrust** set di autorizzazioni.  
  
> [!IMPORTANT]  
>  È necessario modificare il [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] file di configurazione di criteri per consentire **FullTrust** per tutte le estensioni di terze parti. Se non si aggiunge un gruppo di codice con **FullTrust** per le estensioni personalizzate, non possono essere utilizzate dal server di report.  
  
 Per ulteriori informazioni sui file di configurazione dei criteri in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vedere [tramite Reporting Services Security Policy Files](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).  
  
## <a name="expressions-used-in-reports"></a>Espressioni usate nei report  
 Le espressioni di report sono espressioni di codice inline o metodi definiti dall'utente contenuti all'interno di **codice** elemento di un file di report definition language. Un gruppo di codice che è già configurata nei file di criteri che concede a tali espressioni il **esecuzione** autorizzazione impostata per impostazione predefinita. Il gruppo di codice è analogo al seguente:  
  
```  
<CodeGroup  
   class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="Execution"  
   Name="Report_Expressions_Default_Permissions"  
   Description="This code group grants default permissions for code in report expressions and Code element. ">  
    <IMembershipCondition  
       class="StrongNameMembershipCondition"  
       version="1"  
       PublicKeyBlob="002400..."  
    />  
</CodeGroup>  
```  
  
 **Esecuzione** autorizzazioni consente di eseguire codice (esecuzione), ma non per usare risorse protette. Tutte le espressioni presenti all'interno di un report vengono compilate in un assembly (denominato assembly "delle espressioni") archiviato come parte del report compilato. Quando il report viene eseguito, il server di report carica l'assembly delle espressioni ed effettua chiamate in tale assembly per eseguire le espressioni. Gli assembly delle espressioni vengono firmati con una chiave specifica usata per definire il gruppo di codice per tutte le espressioni.  
  
 Le espressioni del report fanno riferimento a raccolte di modelli a oggetti del report (campi, parametri e così via) ed eseguono semplici attività, ad esempio operazioni aritmetiche e di stringa. Richiede solo il codice che esegue queste semplici operazioni **esecuzione** autorizzazione. Per impostazione predefinita, i metodi definiti dall'utente nel **codice** elemento e qualsiasi assembly personalizzati vengono concesse **esecuzione** autorizzazione in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Di conseguenza, per la maggior parte delle espressioni, non è necessario modificare alcun file di criteri di sicurezza per la configurazione corrente. Per concedere autorizzazioni aggiuntive agli assembly delle espressioni, è necessario che un amministratore modifichi i file di configurazione dei criteri del server di report e di Progettazione report e il gruppo di codice delle espressioni del report. Poiché è un'impostazione globale, la modifica di autorizzazioni predefinite per le espressioni influisce su tutti i report. Per tale ragione, è consigliabile posizionare tutto il codice per cui è necessario usare sicurezza aggiuntiva in un assembly personalizzato. Le autorizzazioni necessarie verranno concesse solo a tale assembly.  
  
> [!IMPORTANT]  
>  Affinché sia possibile usarlo nei report, il codice che effettua chiamate ad assembly esterni oppure a risorse protette deve essere incorporato in un assembly personalizzato. In questo modo è possibile esercitare maggiore controllo sulle autorizzazioni richieste e asserite dal codice. Non è necessario effettuare chiamate per proteggere metodi all'interno di **codice** elemento. In questo modo è necessario concedere **FullTrust** all'host di espressione di report e concede l'accesso di tutto il codice personalizzato completo a CLR.  
  
> [!CAUTION]  
>  Non concedere **FullTrust** al gruppo di codice per un host di espressione di report. In caso contrario, a tutte le espressioni del report viene consentito di effettuare chiamate di sistema protette.  
  
## <a name="custom-assemblies-referenced-in-reports"></a>Assembly personalizzati cui si fa riferimento nei report  
 Alcune espressioni del report possono chiamare assembly del codice di terze parti, denominati assembly personalizzati in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Il server di report che tali assembly per avere almeno **esecuzione** autorizzazione nei file di configurazione dei criteri. Per impostazione predefinita, i criteri di file forniti con [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] concedere **esecuzione** dell'autorizzazione per tutti gli assembly a partire dall'area "My Computer". È possibile concedere autorizzazioni aggiuntive agli assembly personalizzati in base alle proprie esigenze.  
  
 In alcuni casi, potrebbe essere necessario eseguire un'operazione che richiede autorizzazioni per il codice specifiche in un'espressione del report. Se si verifica questa situazione, in genere un'espressione del report deve effettuare una chiamata a un metodo della libreria CLR protetto, ad esempio un metodo che esegue l'accesso ai file oppure al Registro di sistema. Nella documentazione di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] vengono descritte le autorizzazioni per il codice necessarie per effettuare la chiamata protetta. Al codice che esegue quest'ultima operazione è necessario concedere tali autorizzazioni di sicurezza specifiche. Se si effettua la chiamata da un'espressione di report o **codice** elemento, l'assembly delle espressioni debba essere concesse le autorizzazioni appropriate. Una volta concesse alle espressioni, tuttavia, le autorizzazioni specifiche vengono concesse a tutto il codice eseguito in tutte le espressioni di qualsiasi report. L'esecuzione della chiamata da un assembly personalizzato cui sono state concesse le autorizzazioni specifiche è molto più sicura a livello di sicurezza.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza dall'accesso di codice in Reporting Services](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)   
 [Proteggere Development &#40; Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  
