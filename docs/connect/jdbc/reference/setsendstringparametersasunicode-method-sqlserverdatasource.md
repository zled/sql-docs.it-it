---
title: Metodo setSendStringParametersAsUnicode (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 554c7e2483e96e27de627f764193a1d4fcabb6dd
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setsendstringparametersasunicode-method-sqlserverdatasource"></a>Metodo setSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un **booleano** valore che indica se l'invio di parametri di stringa al server in formato UNICODE è abilitato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sendStringParametersAsUnicode*  
  
 **true** se i parametri string vengono inviati al server in formato UNICODE. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà sendStringParametersAsUnicode è impostata su **true**, vale a dire il valore predefinito, i parametri string vengono inviati al server in formato UNICODE. Se sendStringParametersAsUnicode è impostata su **false** i parametri di stringa vengono inviati al server in formato ASCII/MBCS, non in formato UNICODE. Se non è impostata, [getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md) restituisce il valore predefinito di **true**.  
  
 Per ulteriori informazioni sulla proprietà di connessione sendStringParametersAsUnicode, vedere [impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

