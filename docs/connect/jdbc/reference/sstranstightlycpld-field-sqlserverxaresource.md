---
title: Campo SSTRANSTIGHTLYCPLD (SQLServerXAResource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation: SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 88a6ea09e8809ac028b45e2bd0fd2035b095430b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>Campo SSTRANSTIGHTLYCPLD (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Utilizzato per consentire le transazioni XA "a regime di controllo stretto ("tightly-coupled")" che dispongono di diversi ID di transazione dei rami XA (XID), ma dello stesso ID di transazione globale (GTRID).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>Valore di campo  
 Un **int** valore 32768.  
  
## <a name="remarks"></a>Osservazioni  
 Ogni transazione viene identificata da un ID di transazione dei rami XA (XID) e da un ID di transazione globale (GTRID). Per consentire alle applicazioni di utilizzare le transazioni XA fortemente accoppiate con XID differenti ma con stesso GTRID, è necessario impostare il [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) sul parametro del metodo XAResource.start flag. Per ulteriori informazioni su come utilizzare questo flag, vedere [nozioni fondamentali sulle transazioni XA](../../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Campi SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [Membri di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Classe SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
