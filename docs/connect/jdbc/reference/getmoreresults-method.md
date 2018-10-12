---
title: Metodo getMoreResults () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMoreResults ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: df89db50-0b2f-4094-820a-30be25ad72fe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2a0b2994bf377610574efbd5c3ff78b0d55035d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718369"
---
# <a name="getmoreresults-method-"></a>Metodo getMoreResults ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Passa al risultato successivo di questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final boolean getMoreResults()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il risultato restituito è un set di risultati. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getMoreResults viene specificato dal metodo getMoreResults nell'interfaccia Statement.  
  
 La chiamata del metodo getMoreResults chiude in modo implicito tutti gli oggetti del set di risultati ottenuti con il metodo [getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMoreResults &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
