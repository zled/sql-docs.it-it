---
title: Posizioni alternative della cartella snapshot | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d22d572ba74036509ee9ed4ce37a56d2b6b87d97
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="alternate-snapshot-folder-locations"></a>Posizioni alternative della cartella snapshot
  Le posizioni alternative della cartella snapshot consentono di archiviare i file di snapshot in una posizione aggiuntiva o diversa da quella predefinita, in genere inclusa nel database di distribuzione. Una posizione alternativa può essere un altro server, un'unità di rete oppure un supporto rimovibile, ad esempio un CD-ROM o un disco rimovibile.  
  
 Le posizioni alternative della cartella snapshot vengono archiviate come proprietà della pubblicazione. Dato che la posizione alternativa della cartella snapshot è una proprietà della pubblicazione, l'agente di distribuzione e l'agente di merge sono in grado di individuare la cartella snapshot corretta durante il processo di sincronizzazione.  
  
 Se si desidera specificare una posizione alternativa della cartella snapshot o comprimere i file di snapshot senza creare immediatamente lo snapshot iniziale, è possibile impostare le proprietà della pubblicazione relative alla posizione dello snapshot e quindi eseguire l'agente snapshot per tale pubblicazione. Se tuttavia si modifica la posizione alternativa dopo avere creato lo snapshot iniziale, è possibile che gli snapshot generati per la pubblicazione non vengano ricollocati nella nuova posizione alternativa. In questo caso, a seconda delle impostazioni di pubblicazione, l'agente di merge o l'agente di distribuzione potrebbero non essere in grado di trovare i file di snapshot nella nuova posizione alternativa.  
  
> [!NOTE]  
>  Evitare di specificare una posizione alternativa che corrisponde alla posizione predefinita della cartella snapshot utilizzando la finestra di dialogo **Proprietà pubblicazione** o [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md).  
  
> [!CAUTION]  
>  Non utilizzare contemporaneamente sia WebSync sia percorsi alternativi della cartella snapshot.  
  
 **Per specificare posizioni alternative della cartella snapshot**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Specificare un percorso alternativo per la cartella snapshot &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   Programmazione [!INCLUDE[tsql](../../includes/tsql-md.md)] della replica: [Configurare le proprietà dello snapshot &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Inizializzare una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Opzioni per gli snapshot](../../relational-databases/replication/snapshot-options.md)  
  
  
