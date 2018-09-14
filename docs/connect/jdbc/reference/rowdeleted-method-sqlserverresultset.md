---
title: Metodo rowDeleted (SQLServerResultSet) | Microsoft Docs
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
- SQLServerResultSet.rowDeleted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90dc0d90de6c0ae55b29085b7658b7b71f21e32d
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786666"
---
# <a name="rowdeleted-method-sqlserverresultset"></a>Metodo rowDeleted (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera informazioni circa l'eventuale eliminazione di una riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se è stata eliminata una riga e le eliminazioni vengono rilevate. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo rowDeleted viene specificato dal metodo rowDeleted nell'interfaccia ResultSet.  
  
 Una riga eliminata potrebbe lasciare uno spazio vuoto visibile in un set di risultati. Questo metodo può essere utilizzato per rilevare gli spazi vuoti in un set di risultati. Il valore restituito dipende dalla possibilità dell'oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) di rilevare le eliminazioni.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rileva le righe eliminate per tutti i tipi di cursore aggiornabile, anche se il rilevamento è temporaneo per i cursori forward e dinamici.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
