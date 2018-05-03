---
title: 'PDO:: quote | Documenti Microsoft'
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
ms.assetid: ab9ddc48-42f8-4edf-aa8b-b0fc66706161
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: def52b7c8cba89b6d2981bb358b692be925da700
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="pdoquote"></a>PDO::quote
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Elabora una stringa da usare in una query, inserendo le virgolette per racchiudere la stringa di input come richiesto dal database di SQL Server sottostante. PDO::quote ignorerà i caratteri speciali all'interno della stringa di input usando uno stile di delimitazione appropriato per SQL Server.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
string PDO::quote( $string[, $parameter_type ] )  
```  
  
#### <a name="parameters"></a>Parametri  
$*string*: stringa da delimitare.  
  
$*tipo_parametro*: simbolo (intero) facoltativo che indica il tipo di dati.  Il valore predefinito è PDO::PARAM_STR.  
  
## <a name="return-value"></a>Valore restituito  
Stringa delimitata che può essere passata a un'istruzione SQL oppure FALSE in caso di errore.  
  
## <a name="remarks"></a>Osservazioni  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
$database = "test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = 'a \' g';  
$param2 = $conn->quote( $param );  
  
$query = "INSERT INTO Table1 VALUES( ?, '1' )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
$query = "INSERT INTO Table1 VALUES( ?, ? )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param, $param2));  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
