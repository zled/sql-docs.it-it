---
title: Esegue il Commit delle transazioni Force istruzione di definizione dati. | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.dataDefinitionCausesTransactionCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf04fa73-b9f1-4403-b6a0-e53d0d27c671
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d1956341fd4842b9452a7b81eecef3c7e0ad2096
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760429"
---
# <a name="datadefinitioncausestransactioncommit-method-sqlserverdatabasemetadata"></a>Metodo dataDefinitionCausesTransactionCommit (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se un'istruzione di definizione dei dati all'interno di una transazione forza il commit della transazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean dataDefinitionCausesTransactionCommit()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'istruzione DDL forza un'operazione di commit. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo dataDefinitionCausesTransactionCommit viene specificato dal metodo dataDefinitionCausesTransactionCommit nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
