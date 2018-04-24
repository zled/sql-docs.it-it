---
title: Sottoscrivere e verificare criteri Nome Finance | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c6a473677fef460ad5d000c87872255d6b9d9ae8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="lesson-2-2---subscribe-to-and-check-the-finance-name-policy"></a>Lezione 2-2: Sottoscrivere e verificare criteri Nome Finance
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questa attività verrà configurato il database Finance per la sottoscrizione della categoria di criteri Finance. Verranno quindi verificati i criteri Nome Finance.  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a>Per sottoscrivere la categoria di criteri Finance  
  
1.  In Esplora oggetti, espandere **Database**, fare clic con il pulsante destro del mouse su **Finance**, scegliere **Criteri**e fare clic su **Categorie**.  
  
2.  Selezionare la casella di controllo **Sottoscritto** per la categoria **Finance** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a>Per verificare l'applicazione dei criteri Nome Finance  
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]aprire una finestra di query. Eseguire le istruzioni seguenti che consentono di creare una tabella che viola i criteri **Nome Finance** . La tabella viola i criteri perché il nome della tabella non inizia con le lettere **fintbl**.  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
    Si noti che i criteri impediscono la creazione della tabella e restituiscono un messaggio informativo indicante il nome dei criteri.  
  
2.  Per specificare un nome valido, modificare il codice nel modo indicato di seguito ed eseguire nuovamente l'istruzione.  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
    Questa modifica consente la creazione della tabella.  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a>Per applicare i criteri all'intero server  
  
1.  Solo il database Finance sottoscrive attualmente la categoria di criteri Finance. In molti casi è più facile applicare la categoria di criteri all'intero server. In Esplora oggetti espandere **Gestione**, fare clic con il pulsante destro del mouse su **Gestione criteri**e scegliere **Gestione categorie**.  
  
2.  Nella finestra di dialogo **Gestione categorie di criteri** individuare la categoria Finance e selezionare la casella di controllo **Imponi sottoscrizioni di database** per la categoria.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] La categoria Finance si applica ora a tutti i database, ma la condizione creata in precedenza limita i criteri Nome Finance al database Finance. In questo esempio viene illustrato come utilizzare combinazioni complesse di condizioni per i criteri in modalità valide per molti server.  
  
## <a name="summary"></a>Riepilogo  
In questa esercitazione è stato illustrato come creare condizioni, criteri e gruppi di criteri della gestione basata su criteri e come applicare filtri e verificare la conformità delle destinazioni della gestione basata su criteri.  
  
## <a name="next"></a>Avanti  
L'esercitazione è completata. Per tornare all'inizio, selezionare [Esercitazione: Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/tutorial-administering-servers-by-using-policy-based-management.md).  
  
Per un elenco delle esercitazioni, vedere [Esercitazioni di SQL Server 2016](../../sql-server/tutorials-for-sql-server-2016.md).  
  
## <a name="see-also"></a>Vedere anche  
[Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
  
