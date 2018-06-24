---
title: Selezionare righe non corrispondenti a un valore (Visual Database Tools) | Microsoft Docs
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
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c0bfc7ef077a3e968ec418430a5b4213c4ef552b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056084"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Selezione di righe non corrispondenti a un valore (Visual Database Tools)
  Per individuare le righe che non corrispondono a un valore, utilizzare l'operatore NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Per individuare le righe che non corrispondono a un valore  
  
1.  Se non è ancora stato fatto, aggiungere nel [riquadro Criteri](visual-database-tools.md)le colonne o le espressioni da usare nella condizione di ricerca.  
  
2.  Individuare la riga contenente la colonna di dati o l'espressione da includere nella ricerca, quindi immettere l'operatore NOT seguito da un valore di ricerca nella colonna **Filtro** della griglia.  
  
 Per trovare, ad esempio, tutte le righe in una tabella `products` in cui i valori nella colonna del codice del prodotto iniziano con un carattere diverso da "A", immettere una condizione di ricerca analoga alla seguente:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Vedere anche  
 [La ricerca di regole per l'immissione di valori &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [Specifica dei criteri di ricerca &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  