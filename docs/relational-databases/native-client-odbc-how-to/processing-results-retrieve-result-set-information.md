---
title: Recuperare informazioni sul Set di risultati (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2211e77ed927c9c2bb5fd9cc3e5df89bc20a5245
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430250"
---
# <a name="processing-results---retrieve-result-set-information"></a>L'elaborazione dei risultati - recuperare le informazioni sul Set di risultati
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-get-information-about-a-result-set"></a>Per recuperare informazioni su un set di risultati  
  
1.  Chiamare [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) per ottenere il numero di colonne nel set di risultati.  
  
2.  Per ogni colonna del set di risultati, effettuare le operazioni seguenti:  
  
    -   Chiamare [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) per ottenere informazioni sulla colonna dei risultati.  
  
     e  
  
    -   Chiamare [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) per ottenere informazioni del descrittore specifiche sulla colonna dei risultati.  
  
## <a name="see-also"></a>Vedere anche  
[Elaborare i risultati &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Determinazione delle caratteristiche di un Set di risultati &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
