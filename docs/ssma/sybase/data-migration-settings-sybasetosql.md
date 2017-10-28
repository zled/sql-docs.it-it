---
title: Le impostazioni di migrazione di dati (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0873c644809c32ecbffa5fbea00bdf71176e9ad2
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="data-migration-settings-sybasetosql"></a>Impostazioni di migrazione di dati (SybaseToSQL)
  
## <a name="data-migration-settings"></a>Impostazioni di migrazione di dati  
**Le impostazioni di migrazione di dati** consente all'utente di scrivere query personalizzate per la migrazione dei dati.  
  
-   Questa scheda è disponibile quando **opzioni di migrazione di dati estesi** è impostato su **Mostra** e viene nascosto quando l'impostazione è impostata su **nascondere** nelle impostazioni del progetto. Per ulteriori informazioni sulle impostazioni di progetto di migrazione, vedere [le impostazioni del progetto (migrazione)](http://msdn.microsoft.com/en-us/82f8857f-7ab1-4738-ab6e-b1e95ea94924) .  
  
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
[Migrazione dei dati Sybase a SQL Server o SQL Azure](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811)  
  

