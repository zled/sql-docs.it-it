---
title: "Propriet&#224; pubblicazione, Partizioni dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.datapartitions.f1"
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Propriet&#224; pubblicazione, Partizioni dati
  Il **partizioni di dati** pagina della **Proprietà pubblicazione** la finestra di dialogo consente di definire partizioni di dati per le pubblicazioni di tipo merge che utilizzano filtri con parametri. Dopo aver definito le partizioni è possibile generare gli snapshot per queste partizioni, specificando set di dati iniziali diversi per Sottoscrittori diversi in base alle proprietà della connessione, ovvero nome dell'account di accesso e/o nome del computer, dei Sottoscrittori. È inoltre possibile consentire ai Sottoscrittori di richiedere il recapito e la generazione di snapshot nel caso in cui questi non dispongano di uno snapshot per la propria partizione al momento della prima sincronizzazione. Per altre informazioni, vedere [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## Opzioni  
 **Aggiungi**  
 Fare clic su **Aggiungi** per definire una partizione. Nel **Aggiungi partizione dati** finestra di dialogo specificare i valori per **HOST_NAME ()** e/o **SUSER_SNAME ()**, e definire una pianificazione per aggiornare gli snapshot.  
  
 **Modifica**  
 Selezionare una partizione esistente nella griglia e fare clic su **Modifica** di modificare la partizione.  
  
 **Delete**  
 Selezionare una partizione esistente nella griglia e fare clic su **eliminare** per eliminare la partizione.  
  
 **Genera gli snapshot selezionati adesso**  
 Selezionare una o più partizioni nella griglia e fare clic su **Genera gli snapshot selezionati adesso** per generare snapshot per tali partizioni.  
  
 **Elimina gli snapshot esistenti**  
 Selezionare una o più partizioni nella griglia e fare clic su **pulire gli snapshot esistenti** per eliminare gli snapshot per tali partizioni.  
  
 **Definisci automaticamente una partizione e genera uno snapshot, se necessario, quando un nuovo Sottoscrittore cerca di eseguire la sincronizzazione**  
 Selezionare questa opzione se si desidera consentire ai Sottoscrittori di richiedere la generazione e l'applicazione di snapshot. I Sottoscrittori potrebbero richiedere questa opzione nel caso in cui non dispongano di uno snapshot per la propria partizione al momento della prima sincronizzazione.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Snapshot per pubblicazioni di tipo merge con filtri con parametri](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  