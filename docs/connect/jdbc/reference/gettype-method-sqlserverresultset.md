---
title: Metodo getType (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ffbc4a02-e851-431c-bc1a-7ab381d982bb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9beb1e335faa29dc83e727e2366208172713909
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726799"
---
# <a name="gettype-method-sqlserverresultset"></a>Metodo getType (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il tipo di cursore di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getType()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **int** che indica il tipo di cursore corrente. Può essere uno dei valori seguenti:  
  
 ResultSet.TYPE_FORWARD_ONLY  
  
 ResultSet.TYPE_SCROLL_INSENSITIVE  
  
 ResultSet.TYPE_SCROLL_SENSITIVE  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getType viene specificato dal metodo getType nell'interfaccia ResultSet.  
  
 Questo metodo può essere utilizzato per determinare il tipo di cursore effettivo. Se l'applicazione ha selezionato TYPE_FORWARD_ONLY o utilizzato un tipo di cursore predefinito, sarà restituito TYPE_FORWARD_ONLY.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
