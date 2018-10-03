---
title: I dati dei parametri con valori di tabella di conversione e altri errori e avvisi | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), data conversion
- table-valued parameters (ODBC), error messages
ms.assetid: edd45234-59dc-4338-94fc-330e820cc248
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2fc0e9889c5872280ef4d5f0baf00f84b88ef99
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176271"
---
# <a name="table-valued-parameter-data-conversion-and-other-errors-and-warnings"></a>Conversione di dati dei parametri con valori di tabella e altri errori e avvisi
  I valori delle colonne dei parametri con valori di tabella possono essere convertiti tra tipi di dati client e server in modo analogo agli altri valori di colonna e di parametro. Poiché un parametro con valori di tabella può contenere più colonne e più righe, è importante poter identificare il valore effettivo in cui si è verificato l'errore.  
  
 Quando viene rilevato un errore o un avviso in una colonna dei parametri con valori di tabella, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client genera un record di diagnostica. Il messaggio di errore conterrà il numero del parametro con valori di tabella, oltre al numero ordinale di colonna e al numero di riga. Un'applicazione può utilizzare anche i campi di diagnostica SQL_DIAG_SS_TABLE_COLUMN_NUMBER e SQL_DIAG_SS_TABLE_ROW_NUMBER all'interno dei record di diagnostica per determinare i valori che vengono associati agli errori e agli avvisi. Questi campi di diagnostica sono disponibili in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive.  
  
 L'identificativo di errore SQLSTATE e il messaggio dei record di diagnostica saranno conformi al comportamento esistente di ODBC in tutti gli altri aspetti, ovvero ad eccezione delle informazioni di identificazione di parametri, righe e colonne, i messaggi di errore avranno gli stessi valori dei parametri con valori di tabella esattamente come per i parametri non con valori di tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [I parametri con valori di tabella &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
