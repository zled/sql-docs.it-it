---
title: Metodo setBytes (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f264f1a6-ee35-4eaf-81d8-ecf99f03b35d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d9aee2dc6c93e12a224a7b582ce53a9df7272bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697369"
---
# <a name="setbytes-method-sqlservercallablestatement"></a>Metodo setBytes (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sulla matrice di valori **byte** specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setBytes(java.lang.String sCol,  
                     byte[] b)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Valore **String** contenente il nome del parametro.  
  
 *b*  
  
 Matrice di **byte** valori.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 In una versione precedente del driver era possibile usare SQLServerCallableStatement.setBytes per convertire valori tra matrici di byte e il tipo di dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **date**, **time**, **datetime2** o **datetimeoffset**. In questa versione l'utilizzo del metodo con questi tipi di dati provoca un'eccezione indicante che la conversione non è supportata.  
  
 Questo metodo setBytes viene specificato dal metodo setBytes nell'interfaccia java.sql.CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
