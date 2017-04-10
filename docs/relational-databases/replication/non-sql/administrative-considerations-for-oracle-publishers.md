---
title: "Considerazioni amministrative per i server di pubblicazione Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione Oracle [replica di SQL Server], considerazioni amministrative"
  - "amministrazione della replica, pubblicazione Oracle"
ms.assetid: cfd81fb5-419b-4a1b-97c4-be7c9d4ee289
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Considerazioni amministrative per i server di pubblicazione Oracle
  Dopo la configurazione di un server di pubblicazione Oracle e l'implementazione dei meccanismi di rilevamento delle modifiche della replica, gli amministratori del sistema di database Oracle possono utilizzare utilità di database Oracle standard ed eseguire attività tipiche di amministrazione dei sistemi. È tuttavia opportuno considerare gli effetti sui dati pubblicati di determinate attività amministrative.  
  
 Ad eccezione dell'eliminazione o della modifica di una colonna pubblicata per la replica oppure dell'eliminazione o della modifica di oggetti di replica, queste considerazioni non sono applicabili alle pubblicazioni snapshot.  
  
## Importazione e caricamento di dati  
 I trigger vengono utilizzati nel rilevamento delle modifiche per le pubblicazioni transazionali in Oracle. Le modifiche apportate alle tabelle pubblicate possono essere replicate nei Sottoscrittori soltanto in caso di attivazione di trigger di replica al momento di un aggiornamento, un inserimento o un'eliminazione. Le utilità Oracle SQL*Loader e Oracle Import dispongono di opzioni che influiscono sull'attivazione di trigger in caso di inserimento di righe nelle tabelle replicate con queste utilità.  
  
### Oracle Import  
 Con Oracle Import, è possibile impostare l'opzione **ignorare** su 'y' o ' N' (il valore predefinito è ' N' '). Se **ignorare** è impostato su ' N' ', la tabella viene eliminata e ricreata durante l'importazione. In questo modo, vengono rimossi i trigger di replica e viene disabilitata la replica. Se **ignorare** è impostato su 'y' importazione tenterà di caricare le righe nella tabella esistente, che viene attivato il trigger di replica. Pertanto, assicurarsi **ignorare** è impostato su 'y' durante l'importazione in una tabella replicata con lo strumento di importazione.  
  
### SQL*Loader  
 Con SQL\*caricatore, è possibile impostare l'opzione **diretta** su 'true' o 'false' (il valore predefinito è 'false'). Se **diretta** è impostato su 'false', le righe vengono inserite mediante istruzioni INSERT convenzionali, che attivano trigger di replica. Se **diretta** è impostato su 'true', il caricamento viene ottimizzato e non vengono attivati i trigger. Pertanto, assicurarsi **diretta** è impostato su 'false' durante il caricamento in una tabella replicata con SQL * strumento caricatore.  
  
## Modifiche a oggetti pubblicati  
 Le azioni seguenti non richiedono speciali considerazioni:  
  
-   Ricompilazione di indici su tabelle pubblicate.  
  
-   Aggiunta di trigger dell'utente a una tabella pubblicata.  
  
 L'azione seguente richiede l'arresto di tutte le attività sulle tabelle pubblicate:  
  
-   Spostamento di una tabella pubblicata.  
  
 Le azioni seguenti richiedono l'eliminazione della pubblicazione, l'esecuzione dell'operazione e infine la ricreazione della pubblicazione:  
  
-   Troncamento di una tabella pubblicata.  
  
-   Ridenominazione di una tabella pubblicata.  
  
-   Aggiunta di una colonna a una tabella pubblicata.  
  
-   Eliminazione o modifica di una colonna pubblicata per la replica.  
  
-   Esecuzione di operazioni non registrate.  
  
## Eliminazione o modifica di oggetti di replica  
 In caso di eliminazione o modifica di qualsiasi trigger, sequenza, stored procedure o tabella di rilevamento a livello di server di pubblicazione, è necessario eliminare e riconfigurare il server di pubblicazione. Per un elenco parziale di questi oggetti, vedere [gli oggetti creati nel server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md).  
  
 Per informazioni sull'eliminazione e la riconfigurazione del server di pubblicazione, vedere la sezione "Modifiche che richiedono la riconfigurazione del server di pubblicazione" nell'argomento [risoluzione dei problemi di server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).  
  
## Vedere anche  
 [Configurazione di un server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Considerazioni e limitazioni relative alla progettazione dei server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md)   
 [Panoramica della pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  