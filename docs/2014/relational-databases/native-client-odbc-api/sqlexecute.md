---
title: SQLExecute | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c422b06c23e2d8f42c48b3b7e03525e285db2769
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063595"
---
# <a name="sqlexecute"></a>SQLExecute
  Se l'attributo di istruzione che sql_sopt_ss_param_focus non è impostata su 0, SQLExecute restituirà SQL_ERROR e genererà un record di diagnostica con SQLSTATE = HY024 e il messaggio "valore attributo non valido, SQL_SOPT_SS_PARAM_FOCUS (deve essere zero in fase di esecuzione)". Per ulteriori informazioni su SQL_SOPT_SS_PARAM_FOCUS, vedere [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
## <a name="remarks"></a>Remarks  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=80708)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  