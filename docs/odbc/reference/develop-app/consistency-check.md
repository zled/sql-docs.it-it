---
title: Verifica di coerenza | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2711f7d45ba433d97c36adb83b8400c6a386eac
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="consistency-check"></a>Verifica di coerenza
Un controllo di coerenza viene eseguito automaticamente dal driver ogni volta che un'applicazione imposta il campo SQL_DESC_DATA_PTR del APD, ARD o IPD. Ogni volta che questo campo è impostato, il driver verificherà che il valore del campo SQL_DESC_TYPE e i valori applicabili per il campo SQL_DESC_TYPE dello stesso record siano validi e coerenti.  
  
 Il campo SQL_DESC_DATA_PTR di un IPD non è in genere impostato; Tuttavia, un'applicazione può farlo per forzare un controllo di coerenza dei campi IPD. Il valore impostato per il campo SQL_DESC_DATA_PTR del IPD non vengono effettivamente archiviato e non è possibile recuperare da una chiamata a **SQLGetDescField** o **SQLGetDescRec**; l'impostazione viene eseguita solo per forzare il verifica della coerenza. Impossibile eseguire una verifica coerenza su un'implementazione.  
  
 Per ulteriori informazioni sulla verifica di coerenza, vedere [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
