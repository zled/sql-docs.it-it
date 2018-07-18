---
title: Gli errori aritmetici | Documenti Microsoft
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
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 867de0b8982b22f9f9574c334226bccc01798065
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="arithmetic-errors"></a>Errori aritmetici
Il driver ODBC restituisce la clausola WHERE in un'istruzione SELECT come il recupero di ogni riga. Se una riga contiene un valore che provoca un errore aritmetico, ad esempio overflow numerico o di divisione per zero, il driver restituisce tutte le righe, ma restituisce errori per le colonne con gli errori aritmetici. Durante l'inserimento o aggiornamento, tuttavia, il driver ODBC arresta inserimento o aggiornamento dei dati quando viene rilevato il primo errore aritmetico.
