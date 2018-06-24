---
title: Copia di massa dei dati di testo e immagine | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c674c24b4000ada4651dfb44ed2d49e9fd5bde83
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062638"
---
# <a name="bulk-copying-text-and-image-data"></a>Copia bulk di dati di tipo text e image
  Large **testo**, **ntext**, e **immagine** i valori vengono copiati tramite la [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) (funzione). Si codice [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) per il **testo**, **ntext**, oppure **immagine** colonna con un *pData* puntatore impostato su NULL che indica i dati vengano forniti insieme **bcp_moretext**. È importante specificare la lunghezza esatta dei dati forniti per ogni **testo**, **ntext**, o **immagine** colonna in ogni riga eseguita la copia bulk. Se la lunghezza dei dati per una colonna è diversa dalla lunghezza della colonna specificata nella [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), utilizzare [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) per impostare la lunghezza sul valore appropriato. Un [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) invia tutto il non -**testo**, non-**ntext**e non-**immagine** dati; è quindi chiamare **bcp_moretext** per inviare il **testo**, **ntext**, o **immagine** dati in unità distinte. Funzioni di copia bulk determinano che tutti i dati è stato inviato per l'oggetto corrente **testo**, **ntext**, o **immagine** colonna quando la somma delle lunghezze dei dati inviati tramite **bcp_moretext** è uguale alla lunghezza specificata nell'ultimo **bcp_collen** o **bcp_bind**.  
  
 **bcp_moretext** non ha un parametro per identificare una colonna. Se ci sono più **testo**, **ntext**, o **immagine** colonne in una riga **bcp_moretext** opera sul **testo**, **ntext**, oppure **immagine** colonne inizia con la colonna con il numero ordinale più basso e procedendo verso la colonna con il numero ordinale più alto. **bcp_moretext** va da una colonna a quella successiva quando la somma delle lunghezze dei dati inviati è uguale alla lunghezza specificata nell'ultimo **bcp_collen** o **bcp_bind** per la colonna corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  