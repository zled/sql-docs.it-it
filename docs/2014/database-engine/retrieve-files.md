---
title: Recuperare file | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1b53eb99abc77e809bd7aaac30f8f218cd4ee03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063402"
---
# <a name="retrieve-files"></a>Recupero di file
  Dopo aver aperto un progetto incluso nel controllo del codice sorgente, è possibile utilizzare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per recuperare le copie locali dei file di progetto dall'archivio del controllo del codice sorgente e salvarle nella directory locale in cui si trova il progetto.  
  
 È possibile utilizzare il controllo del codice sorgente integrato per recuperare i file nei modi seguenti:  
  
-   **Leggi ultima versione (ricorsivo)** comando  
  
     Consente di recuperare l'ultima versione archiviata dei file selezionati. Se viene selezionata una soluzione o un progetto, questo comando consente di recuperare l'ultima versione di tutti i file della soluzione o del progetto.  
  
-   **Ottenere** comando  
  
     Consente di visualizzare il **ottenere** della finestra di dialogo che è possibile utilizzare per recuperare la versione più recente di un file selezionato o per recuperare un subset dei file di soluzione o progetto selezionato.  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a>Per recuperare l'ultima versione di tutti i file in un progetto  
  
1.  In Esplora soluzioni selezionare il progetto desiderato.  
  
2.  Nel **File** dal menu **controllo del codice sorgente**, quindi fare clic su **Leggi ultima versione (ricorsivo)**.  
  
 Le versioni più recenti dei file nel progetto verranno recuperate nel percorso del progetto sul disco locale.  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a>Per recuperare solo alcuni file in un progetto  
  
1.  In Esplora soluzioni selezionare l'elemento che si desidera recuperare.  
  
2.  Nel **File** dal menu **controllo del codice sorgente**, quindi fare clic su **ottenere**.  
  
3.  Nel **ottenere** finestra di dialogo, fare clic su **OK**. In alternativa, se in Esplora soluzioni è stato selezionato un progetto o una soluzione, deselezionare le caselle di controllo accanto agli elementi che non si desidera recuperare.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo &#40;controllo del codice sorgente&#41;](../../2014/database-engine/get-dialog-box-source-control.md)   
 [Impostare e recuperare le informazioni sulla versione](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Visualizzare cronologia progetti](../../2014/database-engine/view-project-history.md)   
 [Visualizzare lo stato di File](../../2014/database-engine/view-file-status.md)  
  
  