---
title: Impostare le opzioni di risoluzione dei conflitti per l'aggiornamento in coda (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b688ce4bb2798336481af48c864a8387fa9c904c
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37348623"
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>Impostazione delle opzioni di risoluzione dei conflitti per l'aggiornamento in coda (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Per impostare le opzioni di risoluzione dei conflitti per le pubblicazioni che supportano sottoscrizioni ad aggiornamento in coda, usare la pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Per impostare le opzioni di risoluzione dei conflitti per l'aggiornamento in coda  
  
1.  Nella pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** selezionare uno dei valori seguenti per l'opzione **Criteri di risoluzione dei conflitti**:  
  
    -   **Mantieni la modifica del server di pubblicazione**  
  
    -   **Mantieni la modifica del Sottoscrittore**  
  
    -   **Reinizializza la sottoscrizione**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
