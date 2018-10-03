---
title: Recuperare informazioni sul Set di risultati (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b34f5bb8f272014c6207d0f1ea14d5154be341b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607169"
---
# <a name="processing-results---retrieve-result-set-information"></a>Elaborazione dei risultati - Recuperare le informazioni sul set di risultati
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
  
  
