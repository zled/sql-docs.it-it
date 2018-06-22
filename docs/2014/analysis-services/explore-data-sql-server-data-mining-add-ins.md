---
title: Esplorare i dati (SQL Server Data Mining Add-ins) | Documenti Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c648fba4cf47f117eb5dd04b76b5d7f0cb4f17c0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066610"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a>Esplorazione dati (componenti aggiuntivi Data mining di SQL Server)
  ![Creazione guidata dati di Esplora](media/dmc-explore.gif "procedura guidata esplorazione dati")  
  
 Il **Esplora dati** procedura guidata consente di conoscere il tipo e la quantità di dati della tabella dati. La procedura guidata consente di creare un grafico della distribuzione e dei valori delle colonne selezionate, una alla volta. È quindi possibile provare a modificare il modo in cui i dati vengono raggruppati o copiare il grafico del contenuto in una cartella di lavoro di Excel per esaminarlo.  
  
 Se nei dati sono contenuti dati numerici continui, è possibile passare tra queste due viste:  
  
-   **Grafico a linee.** Questo grafico a linee riporta i valori dei dati sull'asse X e il numero di case sull'asse Y.  
  
-   **Grafico a barre.** Questo grafico a barre raggruppa i valori in base al numero di case per ogni valore.  
  
 Quando tramite la procedura guidata vengono trovati gruppi nei dati, si utilizza la distribuzione effettiva dei valori dei dati. Pertanto, il grafico a barre non visualizza i valori numerici in base a indicatori numerici tipici dell'asse costituiti da numeri interi, ad esempio 10 o 100. Gli intervalli visualizzati nel grafico a barre possono invece essere simili al seguente: 43521-55603 (per la colonna Income).  
  
 Se si desidera raggruppare i dati in altri intervalli, è necessario eseguire questa operazione in Excel prima di analizzare i dati. In alternativa, è possibile modificare le etichette dati utilizzando il [Modifica etichette](relabel-sql-server-data-mining-add-ins.md) procedura guidata.  
  
## <a name="using-the-explore-data-wizard"></a>Utilizzo della procedura guidata Esplorazione dati  
  
1.  Nel **Data Mining** sulla barra multifunzione, fare clic su **Esplora dati**.  
  
2.  Nel **selezionare l'origine** finestra di dialogo, selezionare la tabella o l'intervallo di celle che contiene i dati.  
  
3.  Nel **Seleziona colonna** finestra di dialogo scegliere la colonna da analizzare dai dati di esempio visualizzati nel riquadro.  
  
4.  Nel **Esplora dati** finestra di dialogo, scegliere i tipi di grafico per visualizzare la distribuzione dei dati.  
  
5.  È possibile aggiungere nuove colonne ai dati, cambiare il modo in cui i dati sono segmentati o copiare il grafico in Excel.  
  
### <a name="requirements"></a>Requisiti  
 Usare la **Esplora dati** procedura guidata, i dati devono essere in una tabella di dati di Excel.   
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo della preparazione per il Data Mining](checklist-of-preparation-for-data-mining.md)  
  
  