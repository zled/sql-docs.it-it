---
title: PDOStatement::fetchColumn | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf385c-ddb0-4c53-9dc6-7df0d3740b04
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 472082861b1290ba4607259092c8a5cb07969ec6
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementfetchcolumn"></a>PDOStatement::fetchColumn
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce una colonna in una riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
string PDOStatement::fetchColumn ([ $column_number ] );  
```  
  
#### <a name="parameters"></a>Parametri  
$*col*: intero facoltativo che indica il numero di colonna in base zero. Il valore predefinito è 0 (la prima colonna della riga).  
  
## <a name="return-value"></a>Valore restituito  
Una colonna oppure false se non sono presenti più righe.  
  
## <a name="remarks"></a>Osservazioni  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   while ( $result = $stmt->fetchColumn(1)) {   
      print($result . "\n");   
   }  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

