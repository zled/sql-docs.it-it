---
title: Metodo setNString (int, lang) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b7da6d44-f5b1-44f8-95f5-40179968b1b0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cef8c88654cf29f9a860a30fc3b79ef6d5124ce4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650019"
---
# <a name="setnstring-method-int-javalangstring"></a>Metodo setNString (int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sull'oggetto **String** specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setNString(int parameterIndex,  
                                                  java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parametro parameterIndex*  
  
 Valore **int** che specifica l'indice del parametro.  
  
 *Valore*  
  
 Oggetto **String** contenente il valore del parametro.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo deve essere usato per **NCHAR**, **NVARCHAR**, **NTEXT**, e **XML** i tipi di dati.  
  
 Questo metodo setNString viene specificato dal metodo setNString nell'interfaccia java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
