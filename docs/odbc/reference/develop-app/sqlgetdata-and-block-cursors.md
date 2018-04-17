---
title: SQLGetData e cursori a blocchi | Documenti Microsoft
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
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 29b41623fe5f4681401e9726adbc1b0993ef98b4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData e cursori a blocchi
**SQLGetData** opera su una singola colonna di una singola riga e non è possibile recuperare una matrice contenente i dati da più righe. Infatti, l'uso primario di **SQLGetData** consiste nel recuperare dati long in parti, viene rilevato non è necessario eseguire questa operazione per più di una riga alla volta.  
  
 Per utilizzare **SQLGetData** con un cursore a blocchi, un'applicazione chiama innanzitutto **SQLSetPos** per posizionare il cursore su una singola riga. Chiama quindi **SQLGetData** per una colonna in tale riga. Tuttavia, questo comportamento è facoltativo. Per determinare se un driver supporta l'utilizzo di **SQLGetData** con cursori a blocchi, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_GETDATA_EXTENSIONS.
