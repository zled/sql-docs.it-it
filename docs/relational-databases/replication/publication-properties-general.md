---
title: "Propriet&#224; pubblicazione, Generale | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.general.f1"
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Propriet&#224; pubblicazione, Generale
  Il **Generale** pagina della **Proprietà pubblicazione** la finestra di dialogo contiene le informazioni di base per la pubblicazione, inclusi nome, descrizione e i criteri di scadenza della sottoscrizione.  
  
## Opzioni  
 **Nome**  
 Nome del database della pubblicazione (informazione di sola lettura).  
  
 **Database**  
 Nome del database di pubblicazione (informazione di sola lettura).  
  
 **Descrizione**  
 Descrizione della pubblicazione.  
  
 **Tipo**  
 Tipo di pubblicazione (informazione di sola lettura).  
  
 **Scadenza sottoscrizione**  
 Selezionare una delle opzioni per la scadenza della sottoscrizione: **le sottoscrizioni non scadono mai** o **le sottoscrizioni scadono**, con un periodo di tempo esplicito (**intervallo**).  
  
 Per pubblicazioni snapshot e transazionali, [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di accettare il valore predefinito di **le sottoscrizioni non scadono mai**.  
  
 Replica di tipo merge [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di accettare il valore predefinito di **le sottoscrizioni scadono** e impostare come valore più basso possibile per **intervallo**. Più è alto il valore del periodo di tempo di scadenza, maggiore è la quantità di metadati archiviati, con conseguenti possibili effetti negativi sulle prestazioni. Raggiungere un equilibrio tra la necessità di disconnettere i Sottoscrittori o semplicemente di non consentire ai Sottoscrittori di eseguire la sincronizzazione per un periodo di tempo esteso e i potenziali problemi di prestazioni derivanti dall'archiviazione e dall'elaborazione di grandi quantità di metadati.  
  
 Per altre informazioni, vedere [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Livello di compatibilità**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. solo per le pubblicazioni di tipo merge. Consente di selezionare la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] minima richiesta per i Sottoscrittori che eseguono la sincronizzazione con la pubblicazione. Il livello di compatibilità viene determinato da una serie di regole associate.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  