---
title: "Configurazione di data factory per la modalità provvisoria o senza restrizioni | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataFactory configuration in RDS [ADO]
ms.assetid: 8ff24805-dc7a-42ae-b600-5bad0e3f51b8
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5ca6d71ee4d714cabb482b09f686e7616618c18
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="configuring-datafactory-for-safe-or-unrestricted-modes"></a>Configurazione di data factory per la modalità provvisoria o senza restrizioni
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Per impostazione predefinita, ADO viene installato con una "safe" [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) configurazione. La modalità provvisoria per i componenti Server di servizi desktop remoto indica che si verifica quanto segue:  
  
1.  Gestore è obbligatorio con il RDSServer (imposto dall'impostazione di una chiave del Registro di sistema).  
  
2.  Il gestore predefinito, MSDFMAP. Handler, viene contrassegnata come gestore predefinito, presente nell'elenco di gestori sicuri e registrati.  
  
3.  MSDFMAP file viene installato nella directory di Windows. È necessario configurare il file in base alle esigenze, prima di usare servizi desktop remoto in modalità a tre livelli.  
  
 Facoltativamente, è possibile configurare un'autorizzazione **DataFactory** installazione. **DataFactory** può essere utilizzato direttamente senza il gestore personalizzato. Sarà quindi possibile utilizzare un gestore personalizzato modificando le stringhe di connessione, ma non è necessaria. Per ulteriori informazioni sulle implicazioni dell'utilizzo di **RDSServer** , vedere [protezione delle applicazioni di servizi desktop remoto](../../../ado/guide/remote-data-service/securing-rds-applications.md).  
  
 Il file di registro di sistema handsafe. reg è stato specificato per impostare le voci di registro del gestore per una configurazione sicura. Per eseguire in modalità provvisoria, eseguire handsafe.  
  
 Dopo aver eseguito handsafe. reg, è necessario arrestare e riavviare il servizio pubblicazione sul Web nel server Web, digitare i comandi seguenti in una finestra del prompt dei comandi: "NET STOP W3SVC" e "NET START W3SVC".  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



