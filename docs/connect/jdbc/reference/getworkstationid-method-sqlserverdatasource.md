---
title: Metodo getWorkstationID (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ece266f25a57c2a99e8acb0b308f7bd918189057
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673629"
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>Metodo getWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il nome del computer client utilizzato per la connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **String** contenente il nome del computer client.  
  
## <a name="remarks"></a>Remarks  
 L'oggetto workstationID è il nome del computer o della workstation client. Se la proprietà workstationID non è impostata, il valore predefinito viene costruito chiamando il metodo InetAddress.getLocalHost().getHostName(). Se getHostName restituisce un valore vuoto, viene chiamato il metodo getHostAddress().toString().  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
