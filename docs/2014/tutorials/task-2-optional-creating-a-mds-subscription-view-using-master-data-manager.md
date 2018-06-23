---
title: 'Attività 2 (facoltativa): Creazione di viste sottoscrizioni MDS tramite Gestione dati Master | Documenti Microsoft'
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
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4883d4f5c7bef05de9625c2fcb7bac235c0306e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170027"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Attività 2 (facoltativa): Creazione di viste sottoscrizioni MDS tramite Gestione dati master
  In questa attività, si crea una vista sottoscrizioni per esporre il **fornitore** entità nel **Suppliers** modello ad altre applicazioni. Questa vista non viene utilizzata nella versione corrente dell'esercitazione.  
  
1.  Passare alla pagina principale del **gestione dati Master** ([http://localhost/MDS](http://localhost/MDS)) facendo clic su **SQL Server 2012 Master Data Services** nella parte superiore.  
  
2.  Fare clic su **Gestione integrazione**.  
  
3.  Fare clic su **creare viste** nella barra dei menu.  
  
     ![Pulsante Aggiungi nuova sottoscrizione vista](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "aggiungere un nuovo pulsante Vista sottoscrizione")  
  
4.  Fare clic su **+ (più)** icona sulla barra degli strumenti per creare una vista sottoscrizioni.  
  
5.  Nel **Crea vista sottoscrizioni** riquadro, digitare **Suppliers** per **nome vista sottoscrizioni**.  
  
6.  Selezionare **Suppliers** per **modello**.  
  
7.  Selezionare **VERSION_1** per **versione**.  
  
8.  Selezionare **fornitore** per **entità**.  
  
9. Selezionare **i membri foglia** per **formato**.  
  
     ![Pulsante Salva vista sottoscrizione](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "pulsante Salva vista sottoscrizione")  
  
10. Fare clic su **salvare** sulla barra degli strumenti per salvare la vista sottoscrizioni. Questa azione viene creata una vista in SQL Server denominata **Suppliers**. Per verificarla, utilizzare SQL Server Management Studio (SSMS).  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 3 &#40;facoltativo&#41;: verifica delle viste sottoscrizioni](task-3-optional-reviewing-the-subscription-views.md)  
  
  