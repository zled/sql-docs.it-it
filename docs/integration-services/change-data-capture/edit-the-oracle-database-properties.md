---
title: "Modificare le proprietà del Database Oracle | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- oraProp
ms.assetid: 58dc99f1-ee6b-4508-bb66-2bc589611ff7
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c310a25fe5098cd5edc845c3a29d024182f6361c
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="edit-the-oracle-database-properties"></a>Modificare le proprietà del database Oracle
  Utilizzare la scheda Oracle nell'editor delle proprietà per modificare la descrizione fornita nella pagina Create CDC database della New Instance Wizard e le informazioni di connessione al database di log mining Oracle.  
  
 Di seguito vengono illustrate le informazioni nella scheda **Oracle** .  
  
 **Nome**  
 Nome dell'istanza di CDC immesso nella pagina Create CDC Database della New Instance Wizard. Questo campo è di sola lettura, pertanto non è possibile modificare queste informazioni.  
  
 **Description**  
 È possibile modificare la descrizione della nuova istanza o aggiungerne una se non è stato fatto al momento della creazione dell'istanza di CDC.  
  
 **Oracle Connect String**  
 Stringa di connessione Oracle al computer contenente il database Oracle in uso. Questo campo è di sola lettura, pertanto non è possibile modificare queste informazioni. In seguito ad alcune modifiche alla stringa di connessione, infatti, l'istanza di Oracle CDC può puntare a un altro database Oracle, danneggiando lo stato dell'istanza archiviato nella tabella **cdc.xdbcdc_config** . Qualora fossero necessarie modifiche di piccola entità, è possibile modificare la stringa di connessione direttamente nella tabella di configurazione tramite SQL Server Management Studio.  
  
 **Oracle Log Mining Authentication**  
 Per immettere le credenziali di autenticazione per il database Oracle che contiene il log miner, selezionare una delle opzioni disponibili in **Authentication**:  
  
-   **Windows Authentication**: selezionare questa opzione per utilizzare le credenziali del dominio Windows correnti. È possibile utilizzare questa opzione solo se il database Oracle è configurato per l'utilizzo dell'autenticazione di Windows.  
  
-   **Oracle Authentication**: se si seleziona questa opzione, è necessario digitare il **nome utente** e la **password** dell'utente nel database Oracle a cui si effettua la connessione.  
  
 È possibile visualizzare le proprietà del database Oracle nel visualizzatore. Quando si utilizza il visualizzatore le informazioni sono in sola lettura. Nel visualizzatore è inoltre incluso un elenco delle colonne acquisite nella tabella. Per informazioni su come accedere al visualizzatore, vedere [How to Manage a CDC Instance](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Come gestire un servizio CDC da CDC Designer Console](../../integration-services/change-data-capture/how-to-manage-a-cdc-service-from-the-cdc-designer-console.md)   
 [Connettersi a un Database di origine Oracle](../../integration-services/change-data-capture/connect-to-an-oracle-source-database.md)   
 [Connettersi a Oracle](../../integration-services/change-data-capture/connect-to-oracle.md)  
  
  
