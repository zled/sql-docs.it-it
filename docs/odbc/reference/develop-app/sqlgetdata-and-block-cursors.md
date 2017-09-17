---
title: SQLGetData e cursori a blocchi | Documenti Microsoft
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
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 715e521f5c8ee5e578ee7a21dd324d3dfb2bb239
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData e cursori a blocchi
**SQLGetData** opera su una singola colonna di una singola riga e non è possibile recuperare una matrice contenente i dati da più righe. Infatti, l'uso primario di **SQLGetData** consiste nel recuperare dati long in parti, viene rilevato non è necessario eseguire questa operazione per più di una riga alla volta.  
  
 Per utilizzare **SQLGetData** con un cursore a blocchi, un'applicazione chiama innanzitutto **SQLSetPos** per posizionare il cursore su una singola riga. Chiama quindi **SQLGetData** per una colonna in tale riga. Tuttavia, questo comportamento è facoltativo. Per determinare se un driver supporta l'utilizzo di **SQLGetData** con cursori a blocchi, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_GETDATA_EXTENSIONS.
