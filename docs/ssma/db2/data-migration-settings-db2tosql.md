---
title: Le impostazioni di migrazione di dati (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 573e673e-a194-4cb2-9aba-aaac6e1a225c
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f21954dbad8a99ef79b1ece15fb82ea037e99572
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="data-migration-settings-db2tosql"></a>Impostazioni di migrazione di dati (DB2ToSQL)
  
## <a name="data-migration-settings"></a>Impostazioni di migrazione di dati  
**Le impostazioni di migrazione di dati** consente all'utente di scrivere query personalizzate per la migrazione dei dati.  
  
-   Questa scheda è disponibile quando **opzioni di migrazione di dati estesi** è impostato su **Mostra** e viene nascosto quando l'impostazione è impostata su **nascondere** nelle impostazioni del progetto. Per ulteriori informazioni sulle impostazioni di progetto di migrazione, vedere [le impostazioni del progetto (migrazione)](http://msdn.microsoft.com/en-us/48aaa8e6-a9cb-487d-9ba5-fc3f1c4786ae) .  
  
-   L'analisi delle istruzioni SQL personalizzata verrà implementato in **le impostazioni di migrazione di dati** scheda del nodo di tabella.  
  
-   Di seguito sono le due caselle di controllo disponibili nel **le impostazioni di migrazione di dati** dei quali.:  
  
    1.  Troncare la tabella di SQL Server  
  
    2.  Selezionare utilizzo personalizzato  
  
1.  **Troncare la tabella di SQL Server:**  
     Questa opzione consente all'utente di avere una visione chiara dei dati migrati nel database di destinazione.  
  
    -   Per impostazione predefinita, questa casella di testo è selezionata.  
  
    -   Se questa casella di testo è deselezionata, verranno aggiunti i dati che viene eseguita la migrazione per i dati esistenti nel database di destinazione.  
  
2.  **Selezionare utilizzo personalizzato:**  
     Questa opzione consente all'utente di modificare il **selezionare** istruzione presente (**selezionare** istruzione consente agli utenti di selezionare i dati da visualizzare nel database di destinazione).  
  
    1.  Per impostazione predefinita, questa casella di testo è deselezionata.  
  
    2.  Se questa casella di testo è selezionata, quindi consente agli utenti di modificare il **selezionare** istruzione presente.  
  
Esistono due pulsanti presenti dei quali.:  
  
-   **Applica:** fare clic su **applica** per applicare le impostazioni che sono state modificate.  
  
-   **Annulla:** fare clic su **Annulla** per ripristinare le impostazioni presente prima di apportare le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei dati DB2 a SQL Server](http://msdn.microsoft.com/en-us/86cbd39f-6dac-409a-9ce1-7dd54403f84b)  
  
