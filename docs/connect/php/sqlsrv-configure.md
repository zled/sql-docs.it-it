---
title: sqlsrv_configure | Documenti Microsoft
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
- sqlsrv_configure
apitype: NA
helpviewer_keywords:
- sqlsrv_configure
- API Reference, sqlsrv_configure
ms.assetid: 9393f975-a4ef-4c50-b4dd-14892fc55cc9
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee3da7943b4bba95335de991e38d45b6261f96e3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvconfigure"></a>sqlsrv_configure
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Modifica le impostazioni delle opzioni di registrazione e gestione degli errori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_configure( string $setting, mixed $value )  
```  
  
#### <a name="parameters"></a>Parametri  
*$setting*: nome dell'impostazione da configurare. Vedere la tabella sottostante per l'elenco delle impostazioni.  
  
*$value*: valore da applicare all'impostazione specificata nel parametro *$setting* . I valori possibili per questo parametro dipendono dall'impostazione specificata. Nella tabella seguente sono elencate le combinazioni possibili:  
  
|Impostazione|Valori possibili per il parametro $value (equivalente Integer tra parentesi)|Valore predefinito|  
|-----------|------------------------------------------------------------------------------|-----------------|  
|ClientBufferMaxKBSize<sup>1</sup>|Numero non negativo fino al limite di memoria PHP.<br /><br />Zero (0) indica nessun limite per le dimensioni del buffer.|10240|  
|LogSeverity<sup>2</sup>|SQLSRV_LOG_SEVERITY_ALL (-1)<br /><br />SQLSRV_LOG_SEVERITY_ERROR (1)<br /><br />SQLSRV_LOG_SEVERITY_NOTICE (4)<br /><br />SQLSRV_LOG_SEVERITY_WARNING (2)|SQLSRV_LOG_SEVERITY_ERROR (1)|  
|LogSubsystems<sup>2</sup>|SQLSRV_LOG_SYSTEM_ALL (-1)<br /><br />SQLSRV_LOG_SYSTEM_CONN (2)<br /><br />SQLSRV_LOG_SYSTEM_INIT (1)<br /><br />SQLSRV_LOG_SYSTEM_OFF (0)<br /><br />SQLSRV_LOG_SYSTEM_STMT (4)<br /><br />SQLSRV_LOG_SYSTEM_UTIL (8)|SQLSRV_LOG_SYSTEM_OFF (0)|  
|WarningsReturnAsErrors<sup>3</sup>|**true** (1) o **false** (0)|**true** (1)|  
  
## <a name="return-value"></a>Valore restituito  
Se viene eseguita una chiamata a **sqlsrv_configure** con un'impostazione o un valore non supportato, la funzione restituisce **false**. In caso contrario, la funzione restituisce **true**.  
  
## <a name="remarks"></a>Osservazioni  
(1) per ulteriori informazioni sulle query sul lato client, vedere [tipi di cursore &#40; Driver SQLSRV &#41; ](../../connect/php/cursor-types-sqlsrv-driver.md).  
  
(2) per ulteriori informazioni sulla registrazione, vedere [Logging Activity](../../connect/php/logging-activity.md).  
  
(3) per ulteriori informazioni sulla configurazione di errori e degli avvisi, vedere [procedura: configurazione di errori e degli avvisi usando il Driver SQLSRV](../../connect/php/how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md).  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Guida di programmazione per il driver SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md) 
  

