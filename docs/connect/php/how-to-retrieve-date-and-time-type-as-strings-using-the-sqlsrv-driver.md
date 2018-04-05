---
title: Recuperare tipo data e ora come stringhe usando il Driver SQLSRV | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- date and time types, retrieving as strings
ms.assetid: 58a974ea-4daf-4e3b-98ed-9731b9c9250f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 43517dce78fe7303c1b4e687b4d3e786fc627a20
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver"></a>Procedura: Recuperare il tipo data e ora come stringhe usando il driver SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Questa funzionalità è stata aggiunta nella versione 1.1 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ed è valida solo quando si usa il driver SQLSRV per [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. È errato usare l'opzione di connessione ReturnDatesAsStrings con il driver PDO_SQLSRV.  
  
È possibile recuperare i tipi di data e ora (**datetime**, **data**, **ora**, **datetime2**, e **datetimeoffset**) come stringhe specificando un'opzione nella stringa di connessione.  
  
### <a name="to-retrieve-date-and-time-types-as-strings"></a>Per recuperare i tipi di data e ora come stringhe  
  
-   Usare l'opzione di connessione seguente:  
  
    ```  
    'ReturnDatesAsStrings'=>true  
    ```  
  
    Il valore predefinito è **false**, vale a dire che i tipi **datetime**, **Date**, **Time**, **DateTime2**e **DateTimeOffset** verranno restituiti come tipi di **Datetime** PHP.  
  
## <a name="example"></a>Esempio  
L'esempio seguente illustra la sintassi per specificare il recupero dei tipi di data e ora come stringhe.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings '=> true);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente viene illustrato che è possibile recuperare le date come stringhe specificando UTF-8 quando si recupera la stringa, anche quando la connessione è stata eseguita con `"ReturnDatesAsStrings" => false`.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", "ReturnDatesAsStrings" => false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0, SQLSRV_PHPTYPE_STRING("UTF-8"));  
  
if( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente viene illustrato come recuperare le date come stringhe specificando UTF-8 e `"ReturnDatesAsStrings" => true` nella stringa di connessione.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings'=> true, "CharacterSet" => 'utf-8' );  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Esempio  
L'esempio seguente illustra come recuperare la data come tipo PHP. `'ReturnDatesAsStrings'=> false` è attivato per impostazione predefinita.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$date_string = date_format( $date, 'jS, F Y' );  
echo "Date = $date_string\n";  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Recupero di dati](../../connect/php/retrieving-data.md)  
  
