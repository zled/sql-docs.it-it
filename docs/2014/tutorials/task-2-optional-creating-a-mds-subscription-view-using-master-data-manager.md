---
title: 'Attività 2 (facoltativa): Creazione di viste sottoscrizioni MDS tramite Gestione dati Master | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 09c2402b9168ac99a201afa8e0ebda971614ee4a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097594"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>Attività 2 (facoltativa): Creazione di viste sottoscrizioni MDS tramite Gestione dati master
  In questa attività si crea una vista sottoscrizioni per esporre il **Supplier** entità nel **Suppliers** modello ad altre applicazioni. Questa vista non viene utilizzata nella versione corrente dell'esercitazione.  
  
1.  Passare alla pagina principale del **gestione dati Master** ([http://localhost/MDS](http://localhost/MDS)), fare clic su **SQL Server 2012 Master Data Services** nella parte superiore.  
  
2.  Fare clic su **Gestione integrazione**.  
  
3.  Fare clic su **creare visualizzazioni** nella barra dei menu.  
  
     ![Aggiungere un nuovo pulsante di visualizzazione di abbonamento](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "aggiungere un nuovo pulsante di visualizzazione di sottoscrizione")  
  
4.  Fare clic su **+ (segno più)** icona sulla barra degli strumenti per creare una vista sottoscrizioni.  
  
5.  Nel **Crea vista sottoscrizioni** riquadro, digitare **Suppliers** per **nome vista sottoscrizioni**.  
  
6.  Selezionare **Suppliers** per **modello**.  
  
7.  Selezionare **VERSION_1** per **versione**.  
  
8.  Selezionare **Supplier** per **entità**.  
  
9. Selezionare **i membri foglia** per **formato**.  
  
     ![Pulsante Salva vista sottoscrizione](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "pulsante Salva vista sottoscrizione")  
  
10. Fare clic su **salvare** sulla barra degli strumenti per salvare la vista sottoscrizioni. Questa azione consente di creare una vista in SQL Server denominata **Suppliers**. Per verificarla, utilizzare SQL Server Management Studio (SSMS).  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 3 &#40;facoltativo&#41;: verifica delle viste sottoscrizioni](task-3-optional-reviewing-the-subscription-views.md)  
  
  
