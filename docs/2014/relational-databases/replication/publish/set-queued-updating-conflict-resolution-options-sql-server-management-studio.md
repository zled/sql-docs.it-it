---
title: Impostare le opzioni di risoluzione dei conflitti per l'aggiornamento in coda (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bf77195076c4467babaa85c19202449b567367ef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37262427"
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>Impostazione delle opzioni di risoluzione dei conflitti per l'aggiornamento in coda (SQL Server Management Studio)
  Per impostare le opzioni di risoluzione dei conflitti per le pubblicazioni che supportano sottoscrizioni ad aggiornamento in coda, usare la pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Per impostare le opzioni di risoluzione dei conflitti per l'aggiornamento in coda  
  
1.  Nella pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** selezionare uno dei valori seguenti per l'opzione **Criteri di risoluzione dei conflitti**:  
  
    -   **Mantieni la modifica del server di pubblicazione**  
  
    -   **Mantieni la modifica del Sottoscrittore**  
  
    -   **Reinizializza la sottoscrizione**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali](enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
