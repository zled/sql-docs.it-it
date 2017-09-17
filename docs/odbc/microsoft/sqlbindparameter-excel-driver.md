---
title: SQLBindParameter (Driver per Excel) | Documenti Microsoft
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
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 013f19579815dfcac2fcfe78cbbe41919bff9c15
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (Driver per Excel)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver Excel. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Quando viene utilizzato il driver per Microsoft Excel, l'esecuzione di un'istruzione INSERT che utilizza un parametro per inserire un valore NULL in una colonna SQL_CHAR restituirà SQL_SUCCESS_WITH_INFO con SQLSTATE 01004, "Dati troncati".
