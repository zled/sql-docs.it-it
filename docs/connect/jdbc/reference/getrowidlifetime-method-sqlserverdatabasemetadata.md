---
title: Metodo getRowIdLifetime (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 317c0b44-fe3f-4142-9cab-e40e4c4fe070
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65541bc857dfcdd7c55caa8e2e7d3831026c79e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731519"
---
# <a name="getrowidlifetime-method-sqlserverdatabasemetadata"></a>Metodo getRowIdLifetime (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce uno stato che indica se è supportato il tipo di dati SQL RowId. Se il tipo è supportato, restituisce la durata di validità di un oggetto RowId.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.RowIdLifetime getRowIdLifetime()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto RowIdLifetime.  
  
> [!NOTE]  
>  Nel Driver JDBC versione 2.0, questo metodo restituisce il valore java.sql.RowIdLifetime.ROWID_UNSUPPORTED.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getRowIdLifetime viene specificato dal metodo getRowIdLifetime nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
