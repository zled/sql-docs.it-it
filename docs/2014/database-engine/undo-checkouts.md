---
title: Annullamento di estrazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 273f7c1ccb5a9e55864df27939ff39e7f04787d5
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43811547"
---
# <a name="undo-checkouts"></a>Annullare estrazioni
  È possibile usare la **Annulla estrazione** comando per annullare un'estrazione esistente. che risulta particolarmente utile quando è necessario eseguire il rollback delle modifiche dopo avere modificato e salvato un file.  
  
 A seconda delle opzioni impostate **opzioni avanzate Annulla estrazione** finestra di dialogo, l'ambiente Studio lascia la copia dell'elemento di lavoro sul disco locale o lo sostituisce con la versione più recente di controllo del codice sorgente. Se l'elemento è stato modificato all'esterno del contesto del sistema di controllo del codice sorgente, è possibile che la versione recuperata non sia quella più recente.  
  
### <a name="to-undo-a-checkout"></a>Per annullare un'estrazione  
  
1.  In Esplora soluzioni selezionare il progetto desiderato.  
  
2.  Nel **File** dal menu **controllo del codice sorgente**, quindi fare clic su **Annulla estrazione**.  
  
3.  Nel **Annulla estrazione** finestra di dialogo, selezionare le opzioni appropriate e quindi fare clic sui **Annulla estrazione** pulsante.  
  
     **Colonne**  
     Consente di specificare le colonne da visualizzare e il relativo ordine.  
  
     **Visualizzazione semplice**  
     Consente di visualizzare gli elementi come elenchi semplici sotto la relativa connessione del controllo del codice sorgente.  
  
     **Nome**  
     Consente di visualizzare i nomi degli elementi per i quali annullare l'estrazione. Accanto agli elementi viene visualizzata la casella di controllo selezionata. Se non si desidera annullare l'estrazione di un elemento, deselezionare la casella di controllo corrispondente.  
  
     **Opzioni**  
     Consente di visualizzare le opzioni di annullamento dell'estrazione specifiche del plug-in del controllo del codice sorgente quando si fa clic sulla freccia a destra del pulsante.  
  
     **Sort**  
     Consente di eseguire l'ordinamento delle colonne visualizzate.  
  
     **Visualizzazione struttura ad albero**  
     Consente di visualizzare la gerarchie di cartelle e di elementi per gli elementi di cui si sta annullando l'estrazione.  
  
     **Annulla estrazione**  
     Consente di annullare l'estrazione, eliminando le eventuali modifiche apportate al file estratto.  
  
## <a name="see-also"></a>Vedere anche  
 [Estrarre i file](../../2014/database-engine/check-out-files.md)   
 [Gestione delle estrazioni](../../2014/database-engine/manage-checkouts.md)  
  
  
