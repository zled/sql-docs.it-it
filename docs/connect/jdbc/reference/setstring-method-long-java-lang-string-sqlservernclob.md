---
title: setString (long, lang) - metodo NClob | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 698073b2-3f0c-449c-ad68-48144698fe8f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 151ff8f36ad3397321dc168b46a949de38e10bd6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689899"
---
# <a name="setstring-method-long-javalangstring-sqlservernclob"></a>Metodo setString (long, java.lang.String) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Scrive l'oggetto specificato **stringa** per il **NCLOB** iniziando in corrispondenza della posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int setString(long pos,  
              java.lang.String str)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Posizione di inizio della scrittura nell'oggetto **NCLOB**. La prima posizione è 1.  
  
 *str*  
  
 Stringa da scrivere nell'oggetto **NCLOB**.  
  
## <a name="return-value"></a>Valore restituito  
 Numero di caratteri scritti.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo setString viene specificato dal metodo nell'interfaccia java.sql.NClob setString.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
