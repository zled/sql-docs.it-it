---
title: Specifica il tipo di dati e il tipo di contenuto (esercitazione di base di Data Mining) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8ea7d719e4341ded35a874c1bdc6c9c9ea0892f9
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313209"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>Impostazione del tipo di dati e contenuto (Esercitazione di base sul data mining)
  Ora che sono state selezionate le colonne da utilizzare per la compilazione della struttura e il training dei modelli, apportare le modifiche necessarie ai tipi di dati e di contenuto predefiniti impostati dalla procedura guidata.  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>Esaminare e modificare il tipo di contenuto e di dati per ogni colonna  
  
1.  Nel **di specificare le colonne tipo di contenuto e dati** fare clic su **rileva** per eseguire un algoritmo che determina i dati predefiniti e i tipi di contenuto per ogni colonna.  
  
2.  Esaminare le voci nel **tipo di contenuto** e **tipo di dati** colonne e modificarle se necessario, per assicurarsi che le impostazioni siano gli stessi di quelli elencati nella tabella seguente.  
  
     In genere, la procedura guidata rileva i numeri e assegna un tipo di dati numerico adatto, ma esistono diversi scenari in cui è invece necessario gestire un numero come testo. Ad esempio, il **GeographyKey** deve essere gestito come testo, perché è corretto eseguire operazioni matematiche su questo identificatore.  
  
    |colonna|Tipo di contenuto|Tipo di dati|  
    |------------|------------------|---------------|  
    |**Riga indirizzo 1**|**Discreti**|**Text**|  
    |**Riga indirizzo 2**|**Discreti**|**Text**|  
    |**Età**|**Continua**|**Long**|  
    |**Bike Buyer**|**Discreti**|**Long**|  
    |**Commute Distance**|**Discreti**|**Text**|  
    |**CustomerKey**|**Key**|**Long**|  
    |**DateLastPurchase**|**Continua**|**Data**|  
    |**Email Address**|**Discreti**|**Text**|  
    |**English Education**|**Discreti**|**Text**|  
    |**English Occupation**|**Discreti**|**Text**|  
    |**FirstName**|**Discreti**|**Text**|  
    |**Gender**|**Discreti**|**Text**|  
    |**Geography Key**|**Discreti**|**Text**|  
    |**House Owner Flag**|**Discreti**|**Text**|  
    |**Last Name**|**Discreti**|**Text**|  
    |**Marital Status**|**Discreti**|**Text**|  
    |**Number Cars Owned**|**Discreti**|**Long**|  
    |**Number Children At Home**|**Discreti**|**Long**|  
    |**Region**|**Discreti**|**Text**|  
    |**Total Children**|**Discreti**|**Long**|  
    |**Yearly Income**|**Continua**|**Double**|  
  
3.  Scegliere **Avanti**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Specifica un Set di dati di Testing per la struttura &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Attività precedente della lezione  
 [Creazione di una struttura modello di Data Mining Targeted Mailing &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [I tipi di contenuto &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [Tipi di dati &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  