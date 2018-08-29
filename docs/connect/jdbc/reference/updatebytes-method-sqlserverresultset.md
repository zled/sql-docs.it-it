---
title: Metodo updateBytes (SQLServerResultSet) | Microsoft Docs
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
- SQLServerResultSet.updateBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3050c836-fbb3-4475-99e5-05637a48a932
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b5235f270b7f95f11157d54f30351141d7cd644
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786311"
---
# <a name="updatebytes-method-sqlserverresultset"></a>Metodo updateBytes (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con una matrice di valori **byte**.  
  
## <a name="overload-list"></a>Elenco degli overload  
  
|nome|Descrizione|  
|----------|-----------------|  
|[updateBytes (int, byte&#91;&#93;)](../../../connect/jdbc/reference/updatebytes-method-int-byte.md)|Aggiorna la colonna designata con una matrice di valori **byte** in base all'indice della colonna.|  
|[updateBytes (java.lang.String, byte&#91;&#93;)](../../../connect/jdbc/reference/updatebytes-method-java-lang-string-byte.md)|Aggiorna la colonna designata con una matrice di valori **byte** in base al nome della colonna.|  
  
## <a name="remarks"></a>Remarks  
 In una versione precedente di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] era possibile usare SQLServerResultSet.updateBytes per convertire valori tra matrici di byte e i tipi di dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **date**, **time**, **datetime2** e **datetimeoffset**. In questa versione l'utilizzo del metodo con questi tipi di dati provoca un'eccezione indicante che la conversione non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
