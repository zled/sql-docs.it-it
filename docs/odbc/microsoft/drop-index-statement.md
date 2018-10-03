---
title: Istruzione DROP INDEX | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DROP INDEX [ODBC]
- SQL grammar [ODBC], DROP INDEX
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b00f15f6a660025930ac401278a571f5cb617697
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636749"
---
# <a name="drop-index-statement"></a>Istruzione DROP INDEX
Quando viene usato il driver Paradox, dBASE o Microsoft Access, la sintassi dell'istruzione DROP INDEX è "DROP INDEX a in b" dove "a" è il nome dell'indice e "b" è il nome della tabella (non DROP INDEX *-nome dell'indice*).  
  
 Quando viene usato il driver Paradox, l'istruzione DROP INDEX Elimina i file di indice secondario Paradox.  
  
 L'istruzione DROP INDEX non è supportata per i driver di Microsoft Excel o di testo.
