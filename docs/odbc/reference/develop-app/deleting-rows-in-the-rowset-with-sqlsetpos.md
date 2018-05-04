---
title: Eliminazione di righe nel set di righe con SQLSetPos | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60d225926a6c11ac81ae8fe6fea8935ee88f1778
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Eliminazione di righe nel set di righe con SQLSetPos
L'operazione di eliminazione di **SQLSetPos** consente all'origine dati di eliminare uno o più righe selezionate di una tabella. Per eliminare le righe con **SQLSetPos**, l'applicazione chiama **SQLSetPos** con *operazione* impostato su SQL_DELETE e *RowNumber* impostato il numero di riga da eliminare. Se *RowNumber* è 0, vengono eliminate tutte le righe nel set di righe.  
  
 Dopo aver **SQLSetPos** restituisce, la riga eliminata è la riga corrente e lo stato è SQL_ROW_DELETED. La riga non può essere utilizzata in tutte le operazioni posizionate ulteriormente, quali chiamate a **SQLGetData** o **SQLSetPos**.  
  
 Quando si eliminano tutte le righe del set di righe (*RowNumber* è uguale a 0), l'applicazione può impedire il driver di eliminare determinate righe utilizzando la matrice di operazione di riga, esattamente come per l'operazione di aggiornamento di **SQLSetPos** . (Vedere [l'aggiornamento delle righe nel set di righe con SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Ogni riga eliminata deve essere una riga che esiste nel set di risultati. Se il buffer dell'applicazione sono state riempite mediante il recupero e se è stata mantenuta una matrice di stato di riga, è possibile che i valori in ognuna di queste posizioni delle righe non devono essere SQL_ROW_DELETED, SQL_ROW_ERROR o SQL_ROW_NOROW.
