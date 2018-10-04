---
title: 'Attività 16: Verifica con gestione dati Master | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b0f8c608384e3840f0c154233e90a79d4319bbad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203191"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Attività 16: Verifica con Gestione dati master
  In questa attività viene verificato lo stato del processo batch inviato dal pacchetto SSIS e viene controllato che i dati siano stati caricati nel server MDS tramite Gestione dati master.  
  
1.  Avvio veloce **gestione dati Master** ([http://localhost/MDS](http://localhost/MDS)). Se è già aperto, fare clic su **Microsoft SQL Server Master Data Services** nella parte superiore per passare alle **homepage**.  
  
2.  Fare clic su **Gestione integrazione**.  
  
3.  Si noti che è presente un batch con denominato **EIMBatch** che è stato inviato nell'elenco. Fare clic su **Import Data** nella barra dei menu se non viene visualizzata la schermata seguente.  
  
     ![Batch EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "Batch EIM")  
  
4.  Tornare alla home page, fare clic su **SQL Server 2012 Master Data Services** nella parte superiore.  
  
5.  Assicurarsi che **Suppliers** modello selezionato per **Model** e **VERSION_1** sia selezionato per **versione**e fare clic su  **Esplora**.  
  
6.  È possibile visualizzare il pacchetto di dati SSIS importato in MDS. I dati devono essere puliti e non sono duplicati **codice** valori (Nota: **SupplierID** colonna in Excel corrisponde a **codice** attributo dell'entità Supplier in MDS).  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 17: Verifica del progetto DQS Cleansing creato dal pacchetto SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
