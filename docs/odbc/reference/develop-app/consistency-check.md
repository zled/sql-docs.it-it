---
title: Verifica di coerenza | Documenti Microsoft
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
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7be399dc7f8fda9d5223fa6a1749e1849bc9ee88
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908716"
---
# <a name="consistency-check"></a>Verifica di coerenza
Un controllo di coerenza viene eseguito automaticamente dal driver ogni volta che un'applicazione imposta il campo SQL_DESC_DATA_PTR del APD, ARD o IPD. Ogni volta che questo campo è impostato, il driver verificherà che il valore del campo SQL_DESC_TYPE e i valori applicabili per il campo SQL_DESC_TYPE dello stesso record siano validi e coerenti.  
  
 Il campo SQL_DESC_DATA_PTR di un IPD non è in genere impostato; Tuttavia, un'applicazione può farlo per forzare un controllo di coerenza dei campi IPD. Il valore impostato per il campo SQL_DESC_DATA_PTR del IPD non vengono effettivamente archiviato e non è possibile recuperare da una chiamata a **SQLGetDescField** o **SQLGetDescRec**; l'impostazione viene eseguita solo per forzare il verifica della coerenza. Impossibile eseguire una verifica coerenza su un'implementazione.  
  
 Per ulteriori informazioni sulla verifica di coerenza, vedere [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
