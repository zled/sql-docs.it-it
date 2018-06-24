---
title: 'Attività 16: Verifica con gestione dati Master | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 36220f21f3e2e28d75ff546857fd87b1e71436f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065023"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Attività 16: Verifica con Gestione dati master
  In questa attività viene verificato lo stato del processo batch inviato dal pacchetto SSIS e viene controllato che i dati siano stati caricati nel server MDS tramite Gestione dati master.  
  
1.  Avviare **gestione dati Master** ([http://localhost/MDS](http://localhost/MDS)). Se è già aperto, fare clic su **Microsoft SQL Server Master Data Services** nella parte superiore per passare al **home page di**.  
  
2.  Fare clic su **Gestione integrazione**.  
  
3.  Si noti che vi sia un batch con denominato **EIMBatch** che è stato inviato nell'elenco. Fare clic su **l'importazione dei dati** nella barra dei menu se non viene visualizzata la schermata seguente.  
  
     ![Batch EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "Batch EIM")  
  
4.  Tornare alla home page, fare clic su **SQL Server 2012 Master Data Services** nella parte superiore.  
  
5.  Assicurarsi che **Suppliers** modello è selezionato per **modello** e **VERSION_1** sia selezionata per **versione**, fare clic su  **Esplora**.  
  
6.  È possibile visualizzare il pacchetto di dati SSIS importato in MDS. I dati devono essere puliti e non includere duplicati **codice** valori (Nota: **SupplierID** colonna in Excel corrisponde a **codice** attributo dell'entità Supplier in MDS).  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 17: Verifica del progetto DQS Cleansing creato dal pacchetto SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  