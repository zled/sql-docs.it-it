---
title: Inserimento di righe con SQLBulkOperations | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd79255e4cda68d1fd4d425544702e589f44336b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Inserimento di righe con SQLBulkOperations
Inserimento di dati con **SQLBulkOperations** è simile all'aggiornamento dei dati con **SQLBulkOperations** poiché utilizza i dati dai buffer di applicazione associata.  
  
 In modo che ogni colonna nella nuova riga ha un valore, tutti associati a colonne con un valore di lunghezza/indicatore di SQL_COLUMN_IGNORE e tutte le colonne non associate devono accettare valori NULL o disporre di un valore predefinito.  
  
 Per inserire righe con **SQLBulkOperations**, l'applicazione esegue le operazioni seguenti:  
  
1.  Imposta l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE sul numero di righe da inserire e inserisce i nuovi valori di dati nei buffer di applicazione associata. Per informazioni su come inviare dati di tipo long con **SQLBulkOperations**, vedere [dati di tipo Long e SQLSetPos e SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Imposta il valore nel buffer di lunghezza/indicatore di ogni colonna in base alle esigenze. Questa è la lunghezza in byte dei dati o SQL_NTS delle colonne associate ai buffer di stringa, la lunghezza in byte dei dati delle colonne associate a un buffer binario e SQL_NULL_DATA per tutte le colonne da impostare su NULL. L'applicazione imposta il valore nel buffer di lunghezza/indicatore di tali colonne che devono essere impostate sui valori predefiniti (se presente) o NULL (se ne esiste uno non) per SQL_COLUMN_IGNORE.  
  
3.  Chiamate **SQLBulkOperations** con il *operazione* argomento impostato su SQL_ADD.  
  
 Dopo aver **SQLBulkOperations** restituisce, la riga corrente rimane invariata. Se è associata la colonna del segnalibro (colonna 0), **SQLBulkOperations** restituisce i segnalibri di righe inserite nel buffer di set di righe associati a tale colonna.

