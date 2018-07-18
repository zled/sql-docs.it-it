---
title: Metodo updateNClob (lang, Java.SQL. NClob) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a025d124-3634-49fa-8bb5-e9b98f2d5de3
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a355e311847d1226174d268e6c5b864fa8a231b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851086"
---
# <a name="updatenclob-method-javalangstring-javasqlnclob"></a>Metodo updateNClob (java.lang.String, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un **NClob** valore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateNClob(java.lang.String columnLabel,  
                        java.sql.NClob x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Oggetto **stringa** che indica l'etichetta di colonna.  
  
 *x*  
  
 Un oggetto NClob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateNClob viene specificato dal metodo updateNClob nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo è supportato solo in **nvarchar (max)**, **ntext**, e **xml** colonne. L'utilizzo di questo metodo su qualsiasi altro tipo di dati genererà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateNClob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
