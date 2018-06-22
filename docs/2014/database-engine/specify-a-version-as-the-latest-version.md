---
title: Specificare una versione come ultima versione | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 598fc6f2d90220f85cef590600d8fcf397384f28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062447"
---
# <a name="specify-a-version-as-the-latest-version"></a>Specifica di una versione come ultima versione
  Quando un file viene archiviato nel controllo del codice sorgente, l'ultima versione diventa quella archiviata. Gli utenti che la estraggono o la recuperano ricevono copie locali dell'elemento archiviato più di recente.  
  
 In alcune situazioni, tuttavia, potrebbe essere necessario designare come ultima una versione precedente di un elemento. Ad esempio, si estrae, si modifica e quindi si archivia il file. In un secondo momento si decide di rimuovere le modifiche. Dal momento che il file è stato archiviato, non è possibile annullare l'estrazione originale. In questo caso è possibile impostare la versione estratta originariamente come ultima versione dell'elemento.  
  
 Per impostare l'ultima versione:  
  
-   **Bloccare una versione**. Quando si blocca una versione del file, le versioni più recenti di quella bloccata non vengono eliminate. È inoltre possibile sbloccare un file bloccato in precedenza. In questo caso, l'ultima versione del file sarà quella archiviata più di recente. Non è tuttavia possibile estrarre un file bloccato.  
  
-   **Eseguire il rollback a una versione specificata**. Quando viene eseguito il ripristino di una versione, tutte le versioni più recenti di quella ripristinata verranno eliminate dal controllo del codice sorgente. È possibile quindi estrarre l'ultima versione rimanente.  
  
### <a name="to-pin-a-version"></a>Per bloccare una versione  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] aprire la soluzione.  
  
2.  In Esplora soluzioni selezionare il file che si desidera specificare come ultima versione.  
  
3.  Nel **File** dal menu **controllo del codice sorgente** e fare clic su **ViewHistory**.  
  
4.  Nel **storico** \<file > finestra di dialogo, selezionare la versione che si desidera specificare come ultima e fare clic su **Pin**.  
  
     Accanto alla versione selezionata viene visualizzato un simbolo di blocco per indicare che si tratta della versione corrente del file. Se in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] è caricata una versione diversa, viene chiesto di ricaricare il file.  
  
### <a name="to-roll-back-to-a-version"></a>Per ripristinare una versione  
  
1.  In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] aprire la soluzione.  
  
2.  In Esplora soluzioni selezionare l'elemento che si desidera specificare come ultima versione.  
  
3.  Nel **File** dal menu **controllo del codice sorgente** e fare clic su **cronologia**.  
  
4.  Nel **Opzioni cronologia** finestra di dialogo, fare clic su **OK** per visualizzare il **cronologia di File** finestra di dialogo.  
  
5.  Nel **cronologia** , selezionare la versione che si desidera specificare come ultima versione, quindi scegliere **Rollback**.  
  
     Verrà visualizzato un messaggio che informa che tutte le versioni successive a quella selezionata verranno eliminate.  
  
6.  Fare clic su **Sì** per eseguire il rollback alla versione selezionata.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle archiviazioni](../../2014/database-engine/manage-checkins.md)   
 [Archiviazione di file](../../2014/database-engine/check-in-files.md)  
  
  