---
title: Selezionare righe non corrispondenti a un valore (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9bf7180c6e3e8f27c49b0f7d662a1b3f42c126fd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38030766"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>Selezione di righe non corrispondenti a un valore (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Per individuare le righe che non corrispondono a un valore, utilizzare l'operatore NOT.  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>Per individuare le righe che non corrispondono a un valore  
  
1.  Se non è ancora stato fatto, aggiungere nel [riquadro Criteri](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)le colonne o le espressioni da usare nella condizione di ricerca.  
  
2.  Individuare la riga contenente la colonna di dati o l'espressione da includere nella ricerca, quindi immettere l'operatore NOT seguito da un valore di ricerca nella colonna **Filtro** della griglia.  
  
Per trovare, ad esempio, tutte le righe in una tabella `products` in cui i valori nella colonna del codice del prodotto iniziano con un carattere diverso da "A", immettere una condizione di ricerca analoga alla seguente:  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>Vedere anche  
[Regole per l'immissione di valori di ricerca (Visual Database Tools)](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Specificare i criteri di ricerca (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
