---
title: Le impostazioni di migrazione di dati (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91f7f558-025d-4f4d-ac2c-aa095e7d1ace
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9e92081e6dea57616636e2b404bce3a950ca8ea4
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="data-migration-settings-oracletosql"></a>Impostazioni di migrazione di dati (OracleToSQL)
  
## <a name="data-migration-settings"></a>Impostazioni di migrazione di dati  
**Le impostazioni di migrazione di dati** consente all'utente di scrivere query personalizzate per la migrazione dei dati.  
  
-   Questa scheda è disponibile quando **opzioni di migrazione di dati estesi** è impostato su **Mostra** e viene nascosto quando l'impostazione è impostata su **nascondere** nelle impostazioni del progetto. Per ulteriori informazioni sulle impostazioni di progetto di migrazione, vedere [le impostazioni del progetto (migrazione)](http://msdn.microsoft.com/en-us/fcd6b988-633b-4b2b-9f36-6368b5e86b60) .  
  
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
[La migrazione dei dati di Oracle a SQL Server](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13)  
  

