---
title: "Selezione di un sistema di risoluzione | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sistema di risoluzione di conflitti predefinito"
  - "articoli [replica di SQL Server], risoluzione dei conflitti"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Selezione di un sistema di risoluzione
  Quando si sceglie un sistema di risoluzione, considerare l'importanza della risoluzione dei conflitti nell'applicazione e se è possibile utilizzare il sistema di risoluzione dei conflitti predefinito basato sulle priorità oppure se è necessario utilizzare un sistema di risoluzione dell'articolo.  
  
 Se i dati sono suddivisi in partizioni che non vengono modificate da più utenti e la topologia di replica è relativamente semplice, ovvero costituita da un server di pubblicazione e pochi Sottoscrittori, i conflitti dovrebbero essere pochi o inesistenti. In questi ambienti non è in genere necessario implementare una strategia di risoluzione dei conflitti complessa. È consigliabile adottare una strategia basata sulle impostazioni predefinite per la risoluzione dei conflitti e che preveda l'utilizzo di sottoscrizioni client e di criteri di priorità della prima modifica. Se la topologia è più complessa, ad esempio se prevede l'utilizzo di Sottoscrittori di ripubblicazione, potrebbero risultare più appropriate le sottoscrizioni server con priorità specifiche.  
  
 È consigliabile adottare un sistema di risoluzione dell'articolo se l'azienda richiede una soluzione più efficace rispetto al sistema di risoluzione predefinito. Se si decide di utilizzare un sistema di risoluzione dell'articolo, è consigliabile utilizzare un gestore della logica di business. Per ulteriori informazioni, vedere [eseguire logica di Business durante la sincronizzazione di tipo Merge](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 Infine, la scelta tra l'utilizzo di un sistema di risoluzione predefinito e un sistema di risoluzione dell'articolo dovrebbe basarsi sui dati e sulle necessità dell'applicazione per quanto riguarda la logica di business. Si supponga, ad esempio, che gli utenti addetti all'immissione dei dati sulla valutazione dei clienti in un set di tabelle non partizionate in diversi Sottoscrittori abbiano qualifiche diverse, ad esempio responsabili di filiale, responsabili di settore, personale addetto alle vendite, e che la qualifica lavorativa determini la priorità da assegnare ai dati. In questo caso è possibile compilare un sistema di risoluzione dell'articolo in cui vengano utilizzati i dati relativi alle qualifiche professionali dell'articolo per stabilire l'elemento che prevale in caso di conflitto.  
  
 Nella tabella seguente vengono descritti i fattori che è necessario prendere in considerazione quando si implementa una strategia di risoluzione dei conflitti, se si prevede che i conflitti si verifichino con una certa frequenza.  
  
|Problema relativo alla risoluzione dei conflitti|Consiglio|  
|-------------------------------|--------------------|  
|Categorie diverse di utenti richiedono valori di priorità diversi.|Utilizzare il sistema di risoluzione predefinito e creare sottoscrizioni server con diversi valori di priorità.<br /><br /> Oppure<br /><br /> Utilizzare un sistema di risoluzione dell'articolo in grado di riconoscere una colonna con valori di autorità nell'articolo per semplificare la risoluzione del conflitto.|  
|Si desidera impostare la priorità della prima modifica eseguita.|Utilizzare il sistema di risoluzione predefinito e creare sottoscrizioni client.|  
|Le modifiche apportate alla stessa riga di dati da più utenti sono accettabili a condizione che non vengano apportate modifiche in conflitto nella stessa colonna.|Utilizzare il sistema di risoluzione predefinito o un sistema di risoluzione dell'articolo con il rilevamento a livello di colonna.|  
|Contrassegnare come conflitto più modifiche a un valore di una riga.|Utilizzare il sistema di risoluzione predefinito o un sistema di risoluzione dell'articolo con il rilevamento a livello di riga.|  
|Contrassegnare come conflitto più modifiche a un valore in un record logico.|Utilizzare il sistema di risoluzione predefinito con il rilevamento a livello di record logico. La funzionalità di record logici non supporta i sistemi di risoluzione personalizzati né i gestori della logica di business.|  
|I dati risultanti dal conflitto devono essere diversi dai dati originali del conflitto.|Utilizzare un sistema di risoluzione dell'articolo che consenta di calcolare nuovi valori.|  
  
## Vedere anche  
 [Rilevamento e risoluzione dei conflitti nei record logici](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md)   
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Ripubblicazione dei dati](../../../relational-databases/replication/republish-data.md)  
  
  