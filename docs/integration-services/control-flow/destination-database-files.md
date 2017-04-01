---
title: "File di database di destinazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferdatabasetask.destdbfiles.f1"
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# File di database di destinazione
  Utilizzare la finestra di dialogo **File di database di destinazione** per visualizzare o modificare i percorsi e i nomi dei file di database nel server di destinazione oppure per specificare un percorso di file di rete per l'attività Trasferisci database. Per altre informazioni su questa attività, vedere [Attività Trasferisci database](../../integration-services/control-flow/transfer-database-task.md).  
  
 Per inserire automaticamente i percorsi e i nomi dei file di database del server di origine in questa finestra di dialogo, specificare innanzitutto le proprietà **SourceConnection**, **SourceDatabaseName**e **SourceDatabaseFiles** nella pagina **Database** della finestra di dialogo **Editor attività Trasferisci database** .  
  
## Opzioni  
 **File di destinazione**  
 Nomi dei file di database trasferiti nel server di destinazione.  
  
 Immettere il nome del file o fare clic sul nome del file per modificarlo.  
  
 **Cartella di destinazione**  
 Cartella del server di destinazione in cui verranno trasferiti i file di database.  
  
 Immettere il percorso della cartella, fare clic su tale percorso per modificarlo oppure fare clic su Sfoglia per individuare la cartella del server di destinazione in cui trasferire i file di database.  
  
 **Condivisione file di rete**  
 Cartella di condivisione dei file di rete del server di destinazione in cui verranno trasferiti i file di database. Utilizzare **Condivisione file di rete** quando si trasferisce un database in modalità offline specificando **DatabaseOffline** per **Metodo** nella pagina **Database** della finestra di dialogo **Editor attività Trasferisci database** .  
  
 Immettere il percorso di condivisione dei file di rete o fare clic su Sfoglia per individuarlo.  
  
 Durante il trasferimento di un database in modalità offline, prima di essere trasferiti nella posizione **Cartella di destinazione** , i file di database vengono copiati nella cartella **Condivisione file di rete** .  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Trasferisci database &#40;pagina Generale&#41;](../../integration-services/control-flow/transfer-database-task-editor-general-page.md)   
 [Editor attività Trasferisci database &#40;pagina Database&#41;](../../integration-services/control-flow/transfer-database-task-editor-databases-page.md)  
  
  