---
title: Metodo getResponseBuffering (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getResponseBuffering()
apilocation:
- SQLServerDataSource.getResponseBuffering()
apitype: Assembly
ms.assetid: 19585a93-88a4-415e-a20e-12ba58cddeaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f63ae057278b996b02b42668c3ad97bcf7b3f50
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645469"
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>Metodo getResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce la modalità di memorizzazione delle risposte nel buffer per questo oggetto [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene una minuscola **completo** oppure **adattivo**.  
  
## <a name="remarks"></a>Remarks  
 Il valore **full** specifica la lettura dell'intero risultato dal server in fase di esecuzione.  
  
 Il valore **adaptive** specifica la memorizzazione nel buffer della quantità di dati minima possibile, quando necessario. Il valore **adaptive** rappresenta la modalità di memorizzazione nel buffer predefinita.  
  
 Per altre informazioni sull'uso la modalità di memorizzazione delle risposte, vedere [Using Adaptive Buffering](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setResponseBuffering &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
