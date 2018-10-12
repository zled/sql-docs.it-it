---
title: Metodo setNClob (java.lang.String, java.io.Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c1b95ee7-7e82-418f-8f30-948589086f63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1af4961609b132ebf6b508b54386e4c02ee3e6e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850079"
---
# <a name="setnclob-method-javalangstring-javaioreader-long"></a>Metodo setNClob (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sull'oggetto Reader specificato, che contiene il numero specificato di caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.io.Reader reader,  
              long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterName*  
  
 Valore **String** contenente il nome del parametro.  
  
 *reader*  
  
 Oggetto lettore.  
  
 *length*  
  
 Valore **long** che indica il numero di caratteri nel flusso.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo deve essere usato per **NCHAR**, **NVARCHAR**, **NTEXT**, e **XML** tipi di dati di parametro.  
  
 Questo metodo setNClob viene specificato dal metodo setNClob nell'interfaccia java.sql.CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setNClob &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
