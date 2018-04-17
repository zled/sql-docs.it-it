---
title: Visual Studio associato. Non associati a colonne Text e Image | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b8677ba4369063f5364410799c3ca4f7bb75f267
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>Visual Studio associato. Colonne non associate Text e Image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Quando si utilizzano i cursori del server, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client è ottimizzato per non trasmettere i dati per unbound **testo**, **ntext**, o **immagine** colonne al momento **SQLFetch** viene eseguita. Il **testo**, **ntext**, o **immagine** dati non vengono effettivamente recuperati dal server fino a quando i problemi dell'applicazione [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) per la colonna.  
  
 Molte applicazioni possono essere scritte in modo che nessun **testo**, **ntext**, o **immagine** dati viene visualizzati quando un utente è semplicemente lo scorrimento verticale in un cursore. Quando un utente seleziona una riga per ottenere ulteriori dettagli, l'applicazione può quindi chiamare **SQLGetData** per recuperare il **testo**, **ntext**, o **immagine** dati. Questo comportamento evita la **testo**, **ntext**, o **immagine** dati per tutte le righe, l'utente non seleziona e può pertanto impediscono la trasmissione di grandi quantità di dati.  
  
## <a name="see-also"></a>Vedere anche  
 [La gestione di colonne Text e Image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)   
 [Funzionamento dei cursori](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
  
