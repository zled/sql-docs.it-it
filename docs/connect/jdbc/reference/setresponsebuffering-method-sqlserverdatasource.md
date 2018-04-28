---
title: Metodo setResponseBuffering (SQLServerDataSource) | Documenti Microsoft
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
ms.topic: article
apiname:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f188e7310725f56f69cce65b7496205a668c109f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>Metodo setResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta la modalità per le connessioni create tramite questo di buffering delle risposte [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Valore*  
  
 Oggetto **stringa** che contiene la modalità di flusso e di memorizzazione nel buffer. La modalità valida può essere una delle seguenti stringhe tra maiuscole e minuscole: **completo** o **adattivo**.  
  
## <a name="remarks"></a>Osservazioni  
 Il **completo** valore specifica lettura dell'intero risultato dal server in fase di esecuzione.  
  
 Il **adattivo** valore specifica il buffer di dati minima possibile quando necessario. Il **adattivo** è il valore predefinito modalità di buffering.  
  
 Per ulteriori informazioni sull'utilizzo della modalità di buffering di risposta, vedere [utilizzando il buffer adattivo](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
