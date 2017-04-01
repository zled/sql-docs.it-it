---
title: "Gestire un servizio Oracle CDC | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "createSrv"
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Gestire un servizio Oracle CDC
  È possibile utilizzare CDC Service Configuration Console per gestire un servizio CDC specifico.  
  
 **Per selezionare il servizio CDC che si desidera utilizzare**  
  
1.  Dal riquadro sinistro di CDC Service Configuration Console, espandere **Local CDC Services**.  
  
2.  Selezionare il servizio CDC che si desidera utilizzare.  
  
     È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC da utilizzare e selezionare l'azione desiderata. Vedere [What can you do with a CDC Service](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
 **OPPURE**  
  
1.  Selezionare **Local CDC Services** nel riquadro sinistro in CDC Service Configuration Console.  
  
2.  Dalla sezione centrale di CDC Service Configuration Console selezionare il servizio che si desidera utilizzare.  
  
     È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC da utilizzare e selezionare l'azione desiderata. Vedere [What can you do with a CDC Service](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
##  <a name="BKMK_WhatcandowithCDCService"></a> Attività che è possibile eseguire con un servizio CDC  
 Quando si utilizza un servizio CDC è possibile eseguire le azioni seguenti:  
  
### Eliminare il servizio  
 Dal riquadro **Actions** sul lato destro di CDC Service Configuration Console, fare clic su **Delete** per eliminare il servizio.  
  
 È anche possibile fare clic con il pulsante destro del mouse sul servizio CDC da eliminare e scegliere **Elimina**.  
  
 **Nota**: se il servizio è in esecuzione al momento dell'eliminazione, il servizio viene arrestato prima di essere eliminato.  
  
 Per eliminare la definizione del servizio Windows di Oracle CDC, è necessario aggiornare l'accesso al database MSXDBCDC nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associata. Quando si fa clic su OK per eliminare il servizio, viene effettuato un tentativo di eliminare la registrazione del servizio Oracle CDC nel database MSXDBCDC. Se non è possibile eliminare la registrazione del servizio Oracle CDC tramite il programma perché non sono disponibili le autorizzazioni appropriate, viene richiesto all'utente di immettere un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con autorizzazioni di aggiornamento per il database MSXDBCDC.  
  
 Per informazioni sui dati da immettere nella finestra di dialogo Connect to SQL Server, vedere [Connection to SQL Server for Delete](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md).  
  
### Modificare le proprietà del servizio CDC  
 Dal riquadro **Actions** sul lato destro di CDC Service Configuration Console, fare clic su **Properties**.  
  
 È anche possibile fare clic con il pulsante destro del mouse sul servizio CDC in cui si desidera modificare le proprietà e scegliere **Proprietà**.  
  
## Vedere anche  
 [Procedura di gestione di un servizio CDC locale](../../integration-services/change-data-capture/how-to-manage-a-local-cdc-service.md)  
  
  