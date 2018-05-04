---
title: Copia di massa dei dati di testo e immagine | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 785233a597818a78223438ce74c940ef2b7a9c3f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="bulk-copying-text-and-image-data"></a>Copia bulk di dati di tipo text e image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Grande **testo**, **ntext**, e **immagine** i valori vengono copiate utilizzando il [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) (funzione). Si codice [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) per il **testo**, **ntext**, o **immagine** colonna con un *pData* puntatore impostato su NULL che indica i dati verranno forniti con **bcp_moretext**. È importante specificare la lunghezza esatta dei dati forniti per ogni **testo**, **ntext**, o **immagine** colonna in ogni riga con la copia bulk. Se la lunghezza dei dati per una colonna è diversa dalla lunghezza della colonna specificata [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), utilizzare [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) per impostare la lunghezza sul valore appropriato. Oggetto [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) invia tutto il non -**testo**, non-**ntext**e non-**immagine** dati; quindi chiamare **bcp_moretext** per inviare il **testo**, **ntext**, o **immagine** dati in unità distinte. Funzioni di copia bulk determinano che tutti i dati è stato inviato per l'oggetto corrente **testo**, **ntext**, o **immagine** colonna quando la somma delle lunghezze dei dati inviati tramite **bcp_moretext** è uguale alla lunghezza specificata nell'ultimo **bcp_collen** o **bcp_bind**.  
  
 **bcp_moretext** non ha un parametro per identificare una colonna. Se ci sono più **testo**, **ntext**, o **immagine** colonne in una riga, **bcp_moretext** opera sul **testo**, **ntext**, o **immagine** colonne a partire dalla colonna con il numero ordinale più basso e procede con la colonna con il numero ordinale più alto. **bcp_moretext** va da una colonna a quella successiva quando la somma delle lunghezze dei dati inviati è uguale alla lunghezza specificata nell'ultimo **bcp_collen** o **bcp_bind** per la colonna corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
