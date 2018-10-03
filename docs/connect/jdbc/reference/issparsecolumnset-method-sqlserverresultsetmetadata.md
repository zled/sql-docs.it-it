---
title: Metodo isSparseColumnSet (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 54fb49527b8b755a884b779bd693044ee465c544
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716869"
---
# <a name="issparsecolumnset-method-sqlserverresultsetmetadata"></a>Metodo isSparseColumnSet (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se una colonna in un set di risultati è un set di colonne di tipo sparse.  
  
## <a name="syntax"></a>Sintassi  
  
```scr  
public boolean isSparseColumnSet(int column)  
```  
  
#### <a name="parameters"></a>Parametri  
 *column*  
  
 Indice della colonna (in base uno).  
  
## <a name="return-value"></a>Valore restituito  
 **true** se una colonna in un set di risultati è un set di colonne di tipo sparse, in caso contrario **false**.  
  
## <a name="remarks"></a>Remarks  
 Questo metodo non consente di recuperare informazioni dal database.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membri di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
