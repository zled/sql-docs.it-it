---
title: Metodo getCharacterStream (int) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getCharacterStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f9f230d-be4c-469a-b3dc-f24531429aae
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a7541baecfd25c9c5cc65923686ab9bfb2dc6c51
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32832036"
---
# <a name="getcharacterstream-method-int"></a>Metodo getCharacterStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore di indice della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto java.IO. Reader.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.Reader getCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto del lettore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getCharacterStream viene specificato dal metodo getCharacterStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo leggerà solo [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipi di dati carattere Unicode, ad esempio nchar, nvarchar, nvarchar (max) e ntext. Tutti gli altri tipi di dati, inclusi i tipi di caratteri ASCII, genereranno un'eccezione. Per leggere i tipi di dati ASCII, utilizzare il [getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
