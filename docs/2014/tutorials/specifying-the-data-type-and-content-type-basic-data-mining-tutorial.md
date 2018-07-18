---
title: Specifica il tipo di dati e il tipo di contenuto (esercitazione di base di Data Mining) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 578d47783f22e857bb2fb84949e9d22dd6ad0e85
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174953"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>Impostazione del tipo di dati e contenuto (Esercitazione di base sul data mining)
  Ora che sono state selezionate le colonne da utilizzare per la compilazione della struttura e il training dei modelli, apportare le modifiche necessarie ai tipi di dati e di contenuto predefiniti impostati dalla procedura guidata.  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>Esaminare e modificare il tipo di contenuto e di dati per ogni colonna  
  
1.  Nel **contenuto e tipo di dati specificare colonne** pagina, fare clic su **rileva** per eseguire un algoritmo che determina i dati predefiniti e i tipi di contenuto per ogni colonna.  
  
2.  Esaminare le voci nel **tipo di contenuto** e **tipo di dati** colonne e modificarli se necessario, per assicurarsi che le impostazioni siano identici a quelli elencati nella tabella seguente.  
  
     In genere, la procedura guidata rileva i numeri e assegna un tipo di dati numerico adatto, ma esistono diversi scenari in cui è invece necessario gestire un numero come testo. Ad esempio, il **GeographyKey** deve essere gestita come testo, perché non è corretto eseguire operazioni matematiche su questo identificatore.  
  
    |colonna|Tipo di contenuto|Tipo di dati|  
    |------------|------------------|---------------|  
    |**Riga indirizzo 1**|**Discreta**|**Text**|  
    |**Riga indirizzo 2**|**Discreta**|**Text**|  
    |**Età**|**Continua**|**Long**|  
    |**Bike Buyer**|**Discreta**|**Long**|  
    |**Commute Distance**|**Discreta**|**Text**|  
    |**CustomerKey**|**Key**|**Long**|  
    |**DateLastPurchase**|**Continua**|**Data**|  
    |**Email Address**|**Discreta**|**Text**|  
    |**English Education**|**Discreta**|**Text**|  
    |**English Occupation**|**Discreta**|**Text**|  
    |**firstName**|**Discreta**|**Text**|  
    |**Gender**|**Discreta**|**Text**|  
    |**Geography Key**|**Discreta**|**Text**|  
    |**House Owner Flag**|**Discreta**|**Text**|  
    |**Last Name**|**Discreta**|**Text**|  
    |**Marital Status**|**Discreta**|**Text**|  
    |**Number Cars Owned**|**Discreta**|**Long**|  
    |**Number Children At Home**|**Discreta**|**Long**|  
    |**Region**|**Discreta**|**Text**|  
    |**Total Children**|**Discreta**|**Long**|  
    |**Yearly Income**|**Continua**|**Double**|  
  
3.  Scegliere **Avanti**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Specifica un Set di dati di Testing per la struttura &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Attività precedente della lezione  
 [Creazione di una struttura modello di Data Mining Targeted Mailing &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [I tipi di contenuto &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [Tipi di dati &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  
