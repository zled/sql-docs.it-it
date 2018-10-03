---
title: Metodo locatorsUpdateCopy (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.locatorsUpdateCopy
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6ec8c1d-7ff8-4bc5-8bd3-0199a9294a6e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e98a27b0afb23d0631d6d0bc0b5569324dea5d73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758019"
---
# <a name="locatorsupdatecopy-method-sqlserverdatabasemetadata"></a>Metodo locatorsUpdateCopy (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se gli aggiornamenti di un LOB vengono eseguiti su una copia o direttamente sul LOB.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean locatorsUpdateCopy()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se gli aggiornamenti vengono eseguiti in una copia. **false** se gli aggiornamenti vengono eseguiti direttamente.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Questo metodo locatorsUpdateCopy viene specificato dal metodo locatorsUpdateCopy nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
