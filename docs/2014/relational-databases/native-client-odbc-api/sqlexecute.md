---
title: SQLExecute | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 017eb7f8c7df6064b0808a2d8d6406e0b9df6ffd
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408247"
---
# <a name="sqlexecute"></a>SQLExecute
  Se l'attributo di istruzione che sql_sopt_ss_param_focus non è impostata su 0, SQLExecute restituirà SQL_ERROR e genererà un record di diagnostica con SQLSTATE = HY024 e il messaggio "valore attributo non valido, SQL_SOPT_SS_PARAM_FOCUS (deve essere zero in fase di esecuzione)". Per altre informazioni su SQL_SOPT_SS_PARAM_FOCUS, vedere [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sui parametri con valori di tabella, vedere [parametri con valori di tabella &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=80708)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
