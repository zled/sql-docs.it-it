---
title: Copia di massa dei dati di testo e immagine | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
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
ms.openlocfilehash: f647e9dae0a54bfb35ff9b0868891e74cfd7d125
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416710"
---
# <a name="bulk-copying-text-and-image-data"></a>Copia bulk di dati di tipo text e image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Grandi **testo**, **ntext**, e **immagine** valori vengono copiati tramite i [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) (funzione). Codice [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) per il **testo**, **ntext**, oppure **immagine** colonna con un *pData* puntatore impostato su NULL che indica i dati vengano forniti insieme **bcp_moretext**. È importante specificare la lunghezza esatta dei dati fornita per ogni **testo**, **ntext**, o **immagine** colonna in ogni riga la copia bulk. Se la lunghezza dei dati per una colonna è diversa dalla lunghezza della colonna specificata nella [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), usare [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) per impostare la lunghezza sul valore appropriato. Oggetto [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) invia tutto il non -**testo**, non-**ntext**e non-**immagine** dati; è quindi chiamare **bcp_moretext** per inviare il **testo**, **ntext**, oppure **immagine** dati in unità distinte. Funzioni di copia bulk determinano che tutti i dati è stato inviato per l'oggetto corrente **testo**, **ntext**, o **immagine** colonna quando la somma delle lunghezze dei dati inviati tramite **bcp_moretext** è uguale alla lunghezza specificata nell'ultimo **bcp_collen** oppure **bcp_bind**.  
  
 **bcp_moretext** non ha un parametro per identificare una colonna. Quando sono presenti più **testo**, **ntext**, o **immagine** colonne in una riga **bcp_moretext** opera sul **testo**, **ntext**, o **immagine** colonne iniziando dalla colonna con il numero ordinale più basso e procedendo verso la colonna con il numero ordinale più alto. **bcp_moretext** va da una colonna a quella successiva quando la somma delle lunghezze dei dati inviati è uguale alla lunghezza specificata nell'ultimo **bcp_collen** oppure **bcp_bind** per la colonna corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
