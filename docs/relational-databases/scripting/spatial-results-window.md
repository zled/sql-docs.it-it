---
title: Finestra Risultati spaziali | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b99298f74c35b95175fd0fe5cb41eb14095477b1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spatial-results-window"></a>Finestra Risultati spaziali
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
 [Visualizzazione di dati spaziali in Esplora oggetti](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Editor di query del motore di database &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Editor di query e di testo &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
