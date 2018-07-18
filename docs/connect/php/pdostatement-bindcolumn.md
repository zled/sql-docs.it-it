---
title: 'Pdostatement:: Bindcolumn | Documenti Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bbdcea53-d23d-4769-89a0-95c7cf4d5390
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b01f19dcb7b55da9c547d07d07784fe1730cdd66
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308450"
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
  
## <a name="remarks"></a>Remarks  
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
  
