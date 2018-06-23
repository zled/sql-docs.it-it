---
title: Recuperare informazioni sul Set di risultati (ODBC) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae6d8f1c5640ee0dc8f63b54a2117057b8f334e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067165"
---
# <a name="retrieve-result-set-information-odbc"></a>Recuperare informazioni sul set di risultati (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>Per recuperare informazioni su un set di risultati  
  
1.  Chiamare [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) per ottenere il numero di colonne nel set di risultati.  
  
2.  Per ogni colonna del set di risultati, effettuare le operazioni seguenti:  
  
    -   Chiamare [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) per ottenere informazioni sulla colonna dei risultati.  
  
     e  
  
    -   Chiamare [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) per ottenere informazioni del descrittore specifiche sulla colonna dei risultati.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure di risultati per l'elaborazione &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Determinazione delle caratteristiche di un Set di risultati &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  