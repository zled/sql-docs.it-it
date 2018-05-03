---
title: sqlsrv_client_info | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_client_info
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_client_info
- sqlsrv_client_info
ms.assetid: 3e2d3679-436a-45d8-8bdc-7c633b65a720
caps.latest.revision: 47
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05f2521ecb88360137a979f839c7f97aa8b22bbd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvclientinfo"></a>sqlsrv_client_info
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce informazioni circa la connessione e lo stack client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_client_info( resource $conn)  
```  
  
#### <a name="parameters"></a>Parametri  
*$conn*: risorsa di connessione mediante la quale il client è connesso.  
  
## <a name="return-value"></a>Valore restituito  
Matrice associativa con chiavi descritte nella tabella seguente o **false** se la risorsa di connessione è Null.  
  
**Per PHP per SQL Server versione 3.2 e 3.1**:  
  
|Key|Description|  
|-------|---------------|  
|DriverDllName|MSODBCSQL11.DLL (ODBC Driver 11 for SQL Server)|  
|DriverODBCVer|Versione ODBC (xx.yy)|  
|DriverVer|Versione DLL di ODBC Driver 11 for SQL Server:<br /><br />ZZZZ ([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] versione 3.2 o 3.1)|  
|ExtensionVer|versione di php_sqlsrv.dll:<br /><br />3.2.xxxx.x (per [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] versione 3.2)<br /><br />3.1.xxxx.x (per [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] versione 3.1)|  
  
**Per PHP per SQL Server versione 3.0 e 2.0**:  
  
|Key|Description|  
|-------|---------------|  
|DriverDllName|SQLNCLI10. DLL ([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] versione 2.0)|  
|DriverODBCVer|Versione ODBC (xx.yy)|  
|DriverVer|Versione DLL di SQL Server Native Client:<br /><br />10.50.xxx ([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] versione 2.0)|  
|ExtensionVer|versione di php_sqlsrv.dll:<br /><br />2.0.xxxx.x ([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] versione 2.0)|  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente vengono scritte informazioni client nella console quando l'esempio viene eseguito dalla riga di comando. Nell'esempio si presuppone che SQL Server sia installato nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
if( $client_info = sqlsrv_client_info( $conn))  
{  
       foreach( $client_info as $key => $value)  
      {  
              echo $key.": ".$value."\n";  
      }  
}  
else  
{  
       echo "Client info error.\n";  
}  
  
/* Close connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
  
