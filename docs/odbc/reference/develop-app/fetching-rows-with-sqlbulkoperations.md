---
title: Recupero di righe con SQLBulkOperations | Documenti Microsoft
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
- SQLBulkOperations function [ODBC], fetching rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2481fe60919a120c0e286c6b7bf3554923bdd0d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912266"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>Recupero di righe con SQLBulkOperations
I dati possono essere refetched in un set di righe mediante segnalibri da una chiamata a **SQLBulkOperations.** Recuperare le righe sono identificate mediante i segnalibri in una colonna del segnalibro associato. Le colonne con un valore di SQL_COLUMN_IGNORE non vengono recuperate.  
  
 Per eseguire operazioni di recupero di massa con **SQLBulkOperations**, l'applicazione esegue le operazioni seguenti:  
  
1.  Recupera e memorizza nella cache i segnalibri di tutte le righe da aggiornare. Se è presente più di un segnalibro e viene utilizzata l'associazione per colonna, i segnalibri vengono archiviati in una matrice. Se è presente più di un segnalibro e viene utilizzata l'associazione per riga, i segnalibri vengono archiviati in una matrice di strutture di riga.  
  
2.  Imposta l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE sul numero di righe da recuperare e associa i buffer contenente il valore di segnalibro o la matrice dei segnalibri, alla colonna 0.  
  
3.  Imposta il valore nel buffer di lunghezza/indicatore di ogni colonna in base alle esigenze. Questa è la lunghezza in byte dei dati o SQL_NTS delle colonne associate ai buffer di stringa, la lunghezza in byte dei dati delle colonne associate a un buffer binario e SQL_NULL_DATA per tutte le colonne da impostare su NULL. L'applicazione imposta il valore nel buffer di lunghezza/indicatore di tali colonne che devono essere impostate sui valori predefiniti (se presente) o NULL (se ne esiste uno non) per SQL_COLUMN_IGNORE.  
  
4.  Chiamate **SQLBulkOperations** con il *operazione* argomento impostato su SQL_FETCH_BY_BOOKMARK.  
  
 Non è necessario per l'applicazione di utilizzare la matrice di operazione della riga per evitare l'operazione da eseguire su determinate colonne. L'applicazione consente di selezionare le righe che si desidera recuperare la copia solo i segnalibri per le righe nella matrice segnalibro associato.
