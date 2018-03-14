---
title: "Proprietà pubblicazione, Partizioni dati | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.datapartitions.f1
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c3934697f01070c587aa1e20670bb42e34e9500
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="publication-properties-data-partitions"></a>Proprietà pubblicazione, Partizioni dati
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La pagina **Partizioni dati** della finestra di dialogo **Proprietà pubblicazione** consente di definire le partizioni di dati per pubblicazioni di tipo merge che utilizzano filtri con parametri. Dopo aver definito le partizioni è possibile generare gli snapshot per queste partizioni, specificando set di dati iniziali diversi per Sottoscrittori diversi in base alle proprietà della connessione, ovvero nome dell'account di accesso e/o nome del computer, dei Sottoscrittori. È inoltre possibile consentire ai Sottoscrittori di richiedere il recapito e la generazione di snapshot nel caso in cui questi non dispongano di uno snapshot per la propria partizione al momento della prima sincronizzazione. Per altre informazioni, vedere [Creazione di uno snapshot per una pubblicazione di tipo merge con filtri con parametri](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## <a name="options"></a>Opzioni  
 **Aggiungi**  
 Fare clic su **Aggiungi** per definire una partizione. Nella finestra di dialogo **Aggiungi partizione dati** specificare i valori per **HOST_NAME()** e/o **SUSER_SNAME()**e definire una pianificazione per l'aggiornamento degli snapshot.  
  
 **Modifica**  
 Selezionare una partizione esistente nella griglia e fare clic su **Modifica** per modificarla.  
  
 **Elimina**  
 Selezionare una partizione esistente nella griglia e fare clic su **Elimina** per eliminarla.  
  
 **Genera gli snapshot selezionati adesso**  
 Selezionare una o più partizioni nella griglia e fare clic su **Genera gli snapshot selezionati adesso** per generare gli snapshot per tali partizioni.  
  
 **Elimina gli snapshot esistenti**  
 Selezionare una o più partizioni nella griglia e fare clic su **Elimina gli snapshot esistenti** per eliminare gli snapshot per tali partizioni.  
  
 **Definisci automaticamente una partizione e genera uno snapshot, se necessario, quando un nuovo Sottoscrittore cerca di eseguire la sincronizzazione**  
 Selezionare questa opzione se si desidera consentire ai Sottoscrittori di richiedere la generazione e l'applicazione di snapshot. I Sottoscrittori potrebbero richiedere questa opzione nel caso in cui non dispongano di uno snapshot per la propria partizione al momento della prima sincronizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzare e modificare le proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Snapshot per pubblicazioni di tipo merge con filtri con parametri](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
