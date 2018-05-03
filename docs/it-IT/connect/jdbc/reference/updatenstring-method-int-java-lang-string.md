---
title: Metodo updateNString (int, lang) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1bb909f1-4a96-4be1-adea-36c8d9703112
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d39f1780e8da5ba41e5231a36170b1ed46eb7eb5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updatenstring-method-int-javalangstring"></a>Metodo updateNString (int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un **stringa** valore utilizzando l'indice della colonna specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateNString(int columnIndex,  
                        java.lang.String nString)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
 *nString*  
  
 Oggetto **stringa** oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateNString viene specificato dal metodo updateNString nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo passa Java **stringa** selezionato **nchar**, **nvarchar (max)**, **ntext**, e **xml** colonne. L'utilizzo di questo metodo su colonne con altri tipi di dati genererà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateNString &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
