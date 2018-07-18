---
title: L'aggiornamento delle righe dal segnalibro con SQLBulkOperations | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], updating rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: c9ad82b7-8dba-45b0-bdb9-f4668b37c0d6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e69a8a2da8b4d246ab99217af23737d7b10eb1b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updating-rows-by-bookmark-with-sqlbulkoperations"></a>L'aggiornamento delle righe dal segnalibro con SQLBulkOperations
Quando si aggiorna una riga dal segnalibro, **SQLBulkOperations** consente all'origine dati di aggiornare una o più righe della tabella. Le righe sono identificate mediante il segnalibro in una colonna del segnalibro associato. La riga viene aggiornata utilizzando i dati nei buffer di applicazione per ogni colonna associata (tranne quando il valore nel buffer di lunghezza/indicatore per una colonna è SQL_COLUMN_IGNORE). Le colonne non associate non verranno aggiornate.  
  
 Per aggiornare le righe dal segnalibro con **SQLBulkOperations**, l'applicazione:  
  
1.  Recupera e memorizza nella cache i segnalibri di tutte le righe da aggiornare. Se è presente più di un segnalibro e viene utilizzata l'associazione per colonna, i segnalibri vengono archiviati in una matrice. Se è presente più di un segnalibro e viene utilizzata l'associazione per riga, i segnalibri vengono archiviati in una matrice di strutture di riga.  
  
2.  Imposta l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE sul numero di segnalibri e associa i buffer contenente il valore di segnalibro o la matrice dei segnalibri, alla colonna 0.  
  
3.  Inserisce i nuovi valori di dati nei buffer di set di righe. Per informazioni su come inviare dati di tipo long con **SQLBulkOperations**, vedere [dati di tipo Long e SQLSetPos e SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
4.  Imposta il valore nel buffer di lunghezza/indicatore di ogni colonna in base alle esigenze. Questa è la lunghezza in byte dei dati o SQL_NTS delle colonne associate ai buffer di stringa, la lunghezza in byte dei dati delle colonne associate a un buffer binario e SQL_NULL_DATA per tutte le colonne da impostare su NULL.  
  
5.  Imposta il valore nel buffer di lunghezza/indicatore di tali colonne che non devono essere aggiornati a SQL_COLUMN_IGNORE. Anche se l'applicazione è possibile ignorare questo passaggio e inviare nuovamente i dati esistenti, questo è inefficiente e rischi in termini di invio di valori all'origine dati che sono stati troncati quando sono stati letti.  
  
6.  Chiamate **SQLBulkOperations** con il *operazione* argomento impostato su SQL_UPDATE_BY_BOOKMARK.  
  
 Per ogni riga che viene inviato all'origine dati come un aggiornamento, i buffer dell'applicazione devono disporre dei dati di riga valida. Se il buffer dell'applicazione sono state riempite mediante il recupero, se è stata mantenuta una matrice di stato di riga e se il valore di stato per una riga è SQL_ROW_DELETED, SQL_ROW_ERROR o SQL_ROW_NOROW, dati non validi potrebbero inavvertitamente inviati all'origine dati.
