---
title: L'aggiornamento, eliminazione o recupero tramite segnalibro | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5af3cad39739c3b85a0c6298d682d8e75a5918d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765806"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Aggiornamento, eliminazione o recupero tramite segnalibro
I segnalibri sono utilizzabile per identificare i dati vengano aggiornati nel set di risultati, eliminato dal risultato impostato o recuperato dall'insieme ai buffer di set di righe di risultati. Queste operazioni vengono eseguite da una chiamata a **SQLBulkOperations** con un *opzione* argomento SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK o SQL_FETCH_BY_BOOKMARK. I segnalibri utilizzati in queste operazioni vengono archiviati nella colonna 0 dei buffer di righe. Quando si aggiorna tramite segnalibro, i dati che le colonne del set di risultati vengono aggiornati a viene recuperato dai buffer di set di righe. Per altre informazioni, vedere [l'aggiornamento dati con SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
