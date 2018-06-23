---
title: Finestra Risultati spaziali | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5a98d82babedc2f60804a1948cd510d59e78b9fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170539"
---
# <a name="spatial-results-window"></a>Finestra Risultati spaziali
  La finestra **Risultati spaziali** fornisce strumenti di mapping visivo per la visualizzazione di dati spaziali. Per visualizzare i risultati spaziali, è necessario che i risultati delle query contengano una colonna spaziale con dati geometrici o geografici.  
  
> [!NOTE]  
>  La finestra **Risultati spaziali** è disponibile solo se i risultati vengono restituiti in una griglia nella finestra **Risultati** . Se si richiede invece la restituzione dei risultati come testo, tale finestra non sarà disponibile.  
  
## <a name="options"></a>Opzioni  
 **Selezionare la colonna spaziale**  
 Consente di specificare la colonna che si desidera visualizzare tra le colonne spaziali nei risultati delle query. È possibile selezionare solo una colonna alla volta.  
  
 **Selezionare la colonna etichetta**  
 Consente di specificare la colonna non spaziale tra le colonne restituite nei risultati delle query per etichettare i dati spaziali. È possibile selezionare solo una colonna alla volta.  
  
 Questa opzione non è disponibile quando in una query vengono restituite solo istanze di punti.  
  
 **Selezionare la proiezione**  
 Consente di visualizzare i dati geografici in quattro tipi di proiezione, ovvero Equirectangular, Mercator, Robinson e Bonne.  
  
 Questa opzione non è disponibile per i dati geometrici.  
  
 **Zoom**  
 Consente di regolare la visualizzazione del mapping in una scala esponenziale.  
  
 **Mostra linee griglia**  
 Consente di attivare o disattivare le linee della griglia delle coordinate.  
  
 Per le forme poligonali, l'etichetta viene visualizzata solo se la forma è grande abbastanza da contenere il testo dell'etichetta. Per visualizzare le etichette di forme di piccole dimensioni, regolare lo zoom.  
  
> [!NOTE]  
>  Non è possibile etichettare le istanze di punti.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di dati spaziali in Esplora oggetti](view-spatial-data-in-object-explorer.md)   
 [Dati spaziali &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)   
 [Editor di query del motore di database &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Editor di query e di testo &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  