---
title: sqlsrv_server_info | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_server_info
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_server_info
- sqlsrv_server_info
ms.assetid: ef6fe2b7-d267-4379-b948-5626c4684367
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca2dd9e131a2c8b07945fdd4bf3d5afd2c5ebc4f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596970"
---
# <a name="sqlsrvserverinfo"></a>sqlsrv_server_info
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce informazioni sul server. Prima di effettuare una chiamata a questa funzione è necessario stabilire una connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_server_info( resource $conn)  
```  
  
#### <a name="parameters"></a>Parametri  
*$conn*: la risorsa di connessione mediante la quale il client e il server sono connessi.  
  
## <a name="return-value"></a>Valore restituito  
Una matrice associativa con le chiavi seguenti:  
  
|Key|Descrizione|  
|-------|---------------|  
|CurrentDatabase|Il database di destinazione corrente.|  
|SQLServerVersion|La versione di SQL Server.|  
|SQLServerName|Nome del server.|  
  
## <a name="example"></a>Esempio  
Quando viene eseguito dalla riga di comando, l'esempio seguente scrive le informazioni del server nel browser.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
$server_info = sqlsrv_server_info( $conn);  
if( $server_info )  
{  
      foreach( $server_info as $key => $value)  
      {  
             echo $key.": ".$value."\n";  
      }  
}  
else  
{  
      echo "Error in retrieving server info.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
  
