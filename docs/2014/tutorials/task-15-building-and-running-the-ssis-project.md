---
title: 'Attività 15: Compilazione ed esecuzione del progetto SSIS | Documenti Microsoft'
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
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a63fcf03591626d5b4c1351d5ce868ef7a9fb65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067503"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>Attività 15: Compilazione ed esecuzione del progetto SSIS
  In questa attività viene compilato ed eseguito il progetto SSIS. Se si dispone della versione a 64 bit di Excel 2010 installato nel computer, è necessario impostare il valore di **Run64BitRuntime** alla **False** per l'origine Excel da utilizzare.  
  
1.  Nel **Esplora soluzioni** finestra, fare clic su **progetto** dal menu, fare clic su **proprietà CleanseAndCurateSuppliers**.  
  
2.  Nel **delle proprietà** finestra di dialogo espandere **le proprietà di configurazione** a sinistra e fare clic su **debug**.  
  
3.  Impostare **Run64BitRuntime** alla **False**.  
  
     ![Proprietà progetto CleanseAndCurateSuppliers](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "proprietà progetto CleanseAndCurateSuppliers")  
  
4.  Fare clic su **OK** per chiudere la **proprietà** finestra di dialogo.  
  
5.  Fare clic su **compilare** nella barra dei menu e fare clic su **compila CleanseAndCurateSuppliers**. Assicurarsi che non siano presenti errori di compilazione.  
  
6.  Fare clic su **Debug** nella barra dei menu e fare clic su **Avvia debug**.  
  
7.  Esaminare i messaggi nel **lo stato di avanzamento** finestra e verificare il pacchetto eseguito e completato correttamente.  
  
     ![I risultati dalla finestra di stato](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "risultante dalla finestra di stato")  
  
     ![Stato finale dalla finestra di stato](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "stato finale dalla finestra di stato")  
  
8.  Fare clic su **Debug** nella barra dei menu e fare clic su **arresta debug** per arrestare la sessione di debug. Se il pacchetto ha esito negativo, è necessario abilitare i visualizzatori dati e verificare il flusso dei dati tra i componenti.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 16: Verifica con gestione dati Master](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  