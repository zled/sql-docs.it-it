---
title: 'Pdostatement:: Bindcolumn | Documenti Microsoft'
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
ms.assetid: bbdcea53-d23d-4769-89a0-95c7cf4d5390
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 981790725a87d186af6c07c635909ae7269b7330
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="pdostatementbindcolumn"></a>PDOStatement::bindColumn
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Associa una variabile a una colonna in un set di risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::bindColumn($column, &$param[, $type[, $maxLen[, $driverdata ]]] );  
```  
  
#### <a name="parameters"></a>Parametri  
$*colonna*: il numero (misto) della colonna (indice in base 1) o nome della colonna nel set di risultati.  
  
&$*param*: il nome (misto) della variabile PHP a cui verrà associata la colonna.  
  
$*tipo*: il tipo di dati facoltativo del parametro, rappresentato da una costante PDO::PARAM_ *.  
  
$*maxLen*: intero facoltativo, non usato dai driver Microsoft per PHP per SQL Server.  
  
$*driverdata*: o parametri per il driver misti facoltativi. Ad esempio, è possibile specificare PDO::SQLSRV_ENCODING_UTF8 per associare la colonna a una variabile come stringa codificata in UTF-8.  
  
## <a name="return-value"></a>Valore restituito  
TRUE se ha esito positivo; in caso contrario, FALSE.  
  
## <a name="remarks"></a>Osservazioni  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
Questo esempio mostra l'associazione di una variabile a una colonna in un set di risultati.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "SELECT Title, FirstName, EmailAddress FROM Person.Contact where LastName = 'Estes'";  
$stmt = $conn->prepare($query);  
$stmt->execute();  
  
$stmt->bindColumn('EmailAddress', $email);  
while ( $row = $stmt->fetch( PDO::FETCH_BOUND ) ){  
   echo "$email\n";  
}  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
