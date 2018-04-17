---
title: Data-at-Execution e Text, ntext o Image Columns | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-text-image-columns
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a7b2e9fb51696b6a9f0c31b25719338b24097e47
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Colonne data-at-execution di tipo text, ntext o image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC data-at-execution è una caratteristica che consente alle applicazioni di utilizzare quantità estremamente elevate di dati su colonne o parametri associati. Quando si recuperano grandi **testo**, **ntext**, o **immagine** colonne, un'applicazione potrebbe non essere in grado di allocare un buffer di grandi dimensioni, associare la colonna del buffer e il recupero semplicemente la riga. Durante l'aggiornamento di dimensioni molto grandi **testo**, **ntext**, o **immagine** colonne, l'applicazione potrebbe non essere in grado di allocare un buffer di grandi dimensioni è sufficiente, associarlo a un marcatore di parametro in un SQL istruzione e quindi eseguire l'istruzione. In questi casi, l'applicazione deve utilizzare [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) o [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md) con le opzioni di data-at-execution.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di colonne di tipo text e image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
