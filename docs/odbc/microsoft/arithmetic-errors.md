---
title: Gli errori aritmetici | Documenti Microsoft
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
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d3585f6e1be7a3f9451231004979321202d7852
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="arithmetic-errors"></a>Errori aritmetici
Il driver ODBC restituisce la clausola WHERE in un'istruzione SELECT come il recupero di ogni riga. Se una riga contiene un valore che provoca un errore aritmetico, ad esempio overflow numerico o di divisione per zero, il driver restituisce tutte le righe, ma restituisce errori per le colonne con gli errori aritmetici. Durante l'inserimento o aggiornamento, tuttavia, il driver ODBC arresta inserimento o aggiornamento dei dati quando viene rilevato il primo errore aritmetico.
