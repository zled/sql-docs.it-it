---
title: Metodo getAsciiStream (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getAsciiStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1ec7e246-4b91-4420-9a4c-0ebd98e2e38b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a96c4e91c449c6055d960fee13f429867ffddd0c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47643014"
---
# <a name="getasciistream-method-int"></a>Metodo getAsciiStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore dell'indice di colonna designato nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come flusso di caratteri ASCII.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.InputStream getAsciiStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Valore **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto InputStream.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getAsciiStream viene specificato dal metodo getAsciiStream nell'interfaccia ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getAsciiStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
