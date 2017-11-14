---
title: Utilizzo di dati multidimensionali | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multidimensional data [ADO]
ms.assetid: 84387746-aa3e-44fd-ad6c-a8214a6966dc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e14c59fd0620129486408d33339e80624743f02
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="working-with-multidimensional-data"></a>Utilizzo di dati multidimensionali
Oggetto *set di celle* è il risultato di una query sui dati multidimensionali. È costituito da una raccolta di assi, in genere non più di quattro assi e in genere solo due o tre. Un *asse* è una raccolta di membri di uno o più dimensioni, che viene utilizzata per individuare o filtrare valori specifici in un cubo.  
  
 Oggetto *posizione* è un punto di un asse. Per un asse è costituito da una singola dimensione, queste posizioni sono un subset dei membri della dimensione. Se un asse è costituito da più di una dimensione, quindi ogni posizione è un'entità composta, che ha  *n*  parti dove  *n*  è il numero di dimensioni orientati lungo l'asse. Ogni parte della posizione è un membro da una dimensione che lo costituiscono.  
  
 Ad esempio, se le dimensioni di geografia e prodotto da un cubo contenente i dati di vendita sono orientate lungo l'asse x di un set di celle, una posizione lungo l'asse può contenere i membri "USA" e "Computer". In questo esempio, determinare una posizione lungo l'asse x richiede che i membri di ogni dimensione sono orientati lungo l'asse.  
  
 Oggetto *cella* è un oggetto posizionato in corrispondenza dell'intersezione delle coordinate dell'asse. Ogni cella dispone di più parti di informazioni a esso associati, inclusi i dati stessi, una stringa formattata (visualizzabile forma dei dati delle celle) e il valore ordinale della cella. (Ogni cella è un valore ordinale univoco nel set di celle. Il valore ordinale della prima cella nel set di celle è zero, mentre la cella più a sinistra nella seconda riga di un set di celle con otto colonne avrebbe un valore ordinale pari a otto.)  
  
 Ad esempio, un cubo include le seguenti sei dimensioni (si noti che questo schema cubo differisce leggermente dall'esempio riportato [Panoramica di schemi e dati multidimensionali](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)):  
  
-   Venditore  
  
-   Geography (gerarchia naturale): continenti, paesi, stati e così via  
  
-   Trimestri, Giorni di trimestri, mesi,  
  
-   Years  
  
-   Le misure: VenditePreviste Sales, valori,  
  
-   Products  
  
 Il set di celle seguente rappresenta le vendite per 1991 per tutti i prodotti:  
  
> [!NOTE]
>  Nell'esempio i valori delle celle possono essere visualizzati come coppie ordinate di numeri ordinali di posizione dell'asse in cui la prima cifra rappresenta la posizione dell'asse x e la seconda cifra la posizione dell'asse y.  
  
 Come indicato di seguito sono riportate le caratteristiche di questo set di celle:  
  
-   Le dimensioni dell'asse: trimestri, venditore, Geography  
  
-   Filtrare le dimensioni: misure, gli anni, i prodotti  
  
-   Due assi: colonna (x o asse 0) e riga (y, o asse 1)  
  
-   asse x: due dimensioni nidificate, venditore e Geography  
  
-   asse y: dimensione trimestri  
  
 L'asse x include due dimensioni nidificate: venditore e Geography. Da geografia, vengono selezionati quattro membri: Seattle, Boston, USA meridionale e Giappone. Vengono selezionati due membri da venditore: otto posizioni Nash. Ciò produce un totale di otto posizioni su questo asse (4 * 8 = 2).  
  
 Ogni coordinata è rappresentato come una posizione con due membri, uno dalla dimensione di agente e un altro dalla dimensione dell'area geografica:  
  
```  
(Valentine, Seattle), (Valentine, Boston), (Valentine, USA_North),  
(Valentine, Japan), (Nash, Seattle), (Nash, Boston), (Nash, USA_North),  
(Nash, Japan)  
```  
  
 L'asse y contiene solo una dimensione, che contiene le otto posizioni seguenti:  
  
```  
Jan, Feb, Mar, Qtr2, Qtr3, Oct, Nov, Dec  
```  
  
 Set di celle, celle, assi e le posizioni sono tutti rappresentate in ADO MD tramite gli oggetti corrispondenti: [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md), [cella](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [asse](../../../ado/reference/ado-md-api/axis-object-ado-md.md), e [posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Modello a oggetti ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (multidimensionale) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Panoramica di schemi e dati multidimensionali](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmazione con ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Uso di ADO con ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)

