---
title: Metodo getResponseBuffering (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c682e28244bf85ce761ab6f8d0b54d5f5f054679
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680409"
---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>Metodo getResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la modalità di memorizzazione delle risposte nel buffer per questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene una minuscola **completo** oppure **adattivo**.  
  
## <a name="remarks"></a>Remarks  
 Il valore **adaptive** specifica la memorizzazione nel buffer della quantità di dati minima possibile, quando necessario.  
  
 Il valore **full** specifica la lettura dell'intero risultato dal server in fase di esecuzione.  
  
 **Adaptive** è il valore predefinito nel Driver JDBC versione 2.0 e 3.0. **completa** era l'impostazione predefinita prima della versione 2.0 del Driver JDBC.  
  
 Per altre informazioni sull'uso la modalità di memorizzazione delle risposte, vedere [Using Adaptive Buffering](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setResponseBuffering &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
