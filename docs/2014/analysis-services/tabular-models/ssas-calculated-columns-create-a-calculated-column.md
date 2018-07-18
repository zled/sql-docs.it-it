---
title: Creare una colonna calcolata (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.as.daxref.CreataCalculatedColumn.f1
ms.assetid: 59440510-2d76-41dc-9b55-edc15259f9da
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b88ac967733abd8cb8c29089435552039f1c55d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224131"
---
# <a name="create-a-calculated-column-ssas-tabular"></a>Creare una colonna calcolata (SSAS tabulare)
  Le colonne calcolate consentono di aggiungere nuovi dati al modello. Invece di incollare o importare i valori nella colonna, viene creata una formula DAX che consente di definire i valori a livello di riga della colonna. I valori in ogni riga di una colonna calcolata vengono calcolati e popolati quando si crea una formula valida e si fa clic su INVIO. La colonna calcolata può essere aggiunta a un'applicazione di analisi o di creazione di report come qualsiasi altra colonna di dati. In questo argomento viene descritto come creare una nuova colonna calcolata tramite la barra della formula DAX in Progettazione modelli.  
  
#### <a name="to-create-a-new-calculated-column"></a>Per creare una nuova colonna calcolata  
  
1.  In Vista dati di Progettazione modelli selezionare la tabella a cui si desidera aggiungere una colonna calcolata, fare clic sul menu **Colonna** , quindi scegliere **Aggiungi colonna**.  
  
     L'opzione**Aggiungi colonna** viene evidenziata nella colonna vuota più a destra e il cursore si sposta nella barra della formula.  
  
     Per creare una nuova colonna tra due colonne esistenti, fare clic con il pulsante destro del mouse su una colonna esistente e quindi scegliere **Inserisci colonna**.  
  
2.  Nella barra della formula effettuare una delle operazioni seguenti:  
  
    -   Digitare un segno di uguale seguito da una formula.  
  
    -   Digitare un segno di uguale, seguito da una funzione DAX e dagli argomenti e dai parametri come richiesto dalla funzione.  
  
    -   Fare clic sul pulsante della funzione (**fx**) e quindi nella finestra di dialogo **Inserisci funzione** selezionare una categoria e una funzione e fare clic su **OK**. Nella barra della formula digitare gli argomenti e i parametri restanti come richiesto dalla funzione.  
  
3.  Premere INVIO per accettare la formula.  
  
     L'intera colonna viene popolata con la formula e viene calcolato un valore per ogni riga.  
  
> [!TIP]  
>  È possibile utilizzare Completamento automatico formule DAX in una formula esistente con funzioni nidificate. Il testo immediatamente prima del punto di inserimento viene utilizzato per visualizzare i valori nell'elenco a discesa mentre tutto il testo dopo tale punto rimane invariato.  
  
## <a name="see-also"></a>Vedere anche  
 [Le colonne calcolate &#40;tabulare di SSAS&#41;](ssas-calculated-columns.md)   
 [Le misure &#40;tabulare di SSAS&#41;](measures-ssas-tabular.md)  
  
  
