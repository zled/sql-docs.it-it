---
title: Gli errori aritmetici | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0a24a87c814c51bcf3270298b56b5ffec01fa29
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="arithmetic-errors"></a>Errori aritmetici
Il driver ODBC restituisce la clausola WHERE in un'istruzione SELECT come il recupero di ogni riga. Se una riga contiene un valore che provoca un errore aritmetico, ad esempio overflow numerico o di divisione per zero, il driver restituisce tutte le righe, ma restituisce errori per le colonne con gli errori aritmetici. Durante l'inserimento o aggiornamento, tuttavia, il driver ODBC arresta inserimento o aggiornamento dei dati quando viene rilevato il primo errore aritmetico.
