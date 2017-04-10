---
title: "Regole business (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regole business [Master Data Services], informazioni sulle regole business"
  - "regole business [Master Data Services]"
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
caps.latest.revision: 16
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 16
---
# Regole business (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] una regola business è una regola utilizzata per garantire la qualità e l'accuratezza dei dati master. È possibile utilizzare una regola business per aggiornare automaticamente i dati, inviare posta elettronica o per avviare un processo aziendale o un flusso di lavoro.  
  
 Per visualizzare esempi di regole di business, vedere [esempi di regole di Business & #40; Master Data Services & #41;](../master-data-services/business-rule-examples-master-data-services.md).  
  
## Creare e pubblicare regole business  
 Regole di business sono **If/Then/Else** istruzioni create in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Se un valore di attributo soddisfa una condizione specificata, viene eseguita una determinata azione. In caso contrario, viene eseguita un'azione Else. Tra le possibili azioni è inclusa l'impostazione di un valore predefinito o la modifica di un valore. Queste azioni possono essere combinate con l'invio di una notifica tramite posta elettronica.  
  
 Le regole business possono essere basate su valori di attributo specifici, ad esempio eseguire un'azione se Color=Blue, o quando i valori di attributo vengono modificati, ad esempio eseguire un'azione se l'attributo Color viene modificato. Per ulteriori informazioni sul rilevamento modifiche non specifiche, vedere [Change Tracking & #40; Master Data Services & #41;](../master-data-services/change-tracking-master-data-services.md).  
  
 Per utilizzare regole business, è necessario prima crearle e pubblicarle, quindi applicare le regole pubblicate ai dati. È possibile applicare regole a subset di dati o a tutti i dati di una versione convalidando la versione. Il commit di una versione non può essere eseguito finché tutti gli attributi non hanno superato la convalida tramite regole business.  
  
 Se un utente tenta di aggiungere un valore di attributo che non ha superato la convalida tramite una regola business, tale valore può comunque essere salvato. È possibile controllare e correggere i problemi di convalida visualizzati in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Quando si crea un pacchetto di distribuzione di modelli, se si desidera includere regole business è necessario includere i dati della versione contenuta nel pacchetto.  
  
 Se si crea una regola business che utilizza il **o** operatore, è necessario creare una regola separata per ogni istruzione condizionale che può essere valutata indipendentemente. È quindi possibile escludere regole in base alle esigenze, offrendo maggiore flessibilità e una più facile risoluzione dei problemi.  
  
## Come vengono applicate le regole business  
 È possibile impostare l'ordine di priorità per l'esecuzione delle regole spostando le regole business verso l'alto e verso il basso. Tuttavia, prima che la priorità venga presa in considerazione, le regole business vengono applicate in base al tipo di azioni che la regola esegue. L'ordine è il seguente:  
  
1.  **Valore predefinito**  
  
2.  **Modifica valore**  
  
3.  **Convalida**  
  
4.  **Azione esterna**  
  
5.  **Script dell'azione definito dall'utente**  
  
 In questi gruppi, le azioni vengono applicate con ordine di priorità crescente, dalla più bassa alla più elevata. Ad esempio, potrebbero essere quattro regole separate **Default Value** Azioni. Il **Default Value** azione che si verifica per primo dipende dall'ordine di priorità specificato nell'interfaccia utente web.  
  
 Altre note importanti sull'applicazione delle regole:  
  
-   Se una regola business è esclusa o non è pubblicata con lo stato **Active**, la regola è comunque disponibile ma non viene inclusa quando vengono applicate le regole di business.  
  
-   Le regole business si applicano ai valori di attributo per tutti i membri foglia oppure per quelli consolidati, non entrambi.  
  
-   Regole di business possono essere applicate a qualsiasi versione di un modello **aprire** o **bloccato**.  
  
-   Le modifiche apportate ai dati, quando le regole business vengono applicate, non vengono registrate come transazioni.  
  
-   Una regola business non può contenere più di un **Avvia flusso di lavoro** azione.  
  
## Impostazioni sistema  
 In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] sono disponibili due impostazioni che influiscono sulle regole business. È possibile regolare tali impostazioni in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] o direttamente nella tabella Impostazioni sistema. Per ulteriori informazioni, vedere [le impostazioni di sistema & #40; Master Data Services & #41;](../master-data-services/system-settings-master-data-services.md).  
  
## Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare e pubblicare una nuova regola business.|[Creare e pubblicare una regola Business & #40; Master Data Services & #41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|Aggiungere più condizioni a una regola business.|[Aggiungere più condizioni a una regola Business & #40; Master Data Services & #41;](../master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|Creare una regola business affinché gli attributi dispongano di valori.|[Richiedere valori di attributo & #40; Master Data Services & #41;](../master-data-services/require-attribute-values-master-data-services.md)|  
|Creare una regola business per eseguire un'azione basata su modifiche dei valori di attributo.|[Inizializzare azioni basate su modifiche dei valori attributo & #40; Master Data Services & #41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|Creare una regola business per eseguire uno script definito dall'utente come condizione|[Estensione delle regole business & #40; Master Data Services & #41;](../master-data-services/business-rules-extension-master-data-services.md)|  
|Creare una regola business per eseguire uno script definito dall'utente come azione|[Estensione delle regole business & #40; Master Data Services & #41;](../master-data-services/business-rules-extension-master-data-services.md)|  
|Modificare il nome di una regola business esistente.|[Modificare il nome di una regola Business & #40; Master Data Services & #41;](../master-data-services/change-a-business-rule-name-master-data-services.md)|  
|Configurare [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] per inviare notifiche quando vengono applicate le regole business.|[Configurare le regole Business per l'invio di notifiche & #40; Master Data Services & #41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|Applicare le regole business a membri specifici.|[Convalidare membri specifici rispetto alle regole Business & #40; Master Data Services & #41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Escludere una regola business in modo che non venga utilizzata.|[Escludere una regola Business & #40; Master Data Services & #41;](../master-data-services/exclude-a-business-rule-master-data-services.md)|  
|Eliminare una regola business esistente.|[Elimina una regola Business & #40; Master Data Services & #41;](../master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## Contenuto correlato  
  
-   [Panoramica di master Data Services e 40 #; MDS & #41;](../master-data-services/master-data-services-overview-mds.md)  
  
-   [Versioni & #40; Master Data Services & #41;](../master-data-services/versions-master-data-services.md)  
  
-   [Convalida & #40; Master Data Services & #41;](../master-data-services/validation-master-data-services.md)  
  
-   [Rilevamento delle modifiche & #40; Master Data Services & #41;](../master-data-services/change-tracking-master-data-services.md)  
  
  