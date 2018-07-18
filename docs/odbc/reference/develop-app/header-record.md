---
title: Record di intestazione | Documenti Microsoft
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
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 095135d0fb199ddcc89203d5ba5cc4cbf334d273
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908956"
---
# <a name="header-record"></a>Record di intestazione
I campi nel record di intestazione contengono informazioni generali sull'esecuzione di una funzione, incluso il codice restituito, conteggio delle righe, numero di record di stato e tipo di istruzione eseguita. Il record di intestazione viene sempre creato, a meno che la funzione non restituisca SQL_INVALID_HANDLE. Per un elenco completo dei campi nel record di intestazione, vedere il [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) descrizione della funzione.
