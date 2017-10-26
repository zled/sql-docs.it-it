---
title: PDO::lastInsertId | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c617b53-a74b-4d5b-b76b-3ec7f1b8e8de
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6a3dd9f6c007f4f528a657230e198397331cb24b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="pdolastinsertid"></a>PDO::lastInsertId
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce l'identificatore dell'ultima riga inserita in una tabella del database. La tabella deve includere una colonna IDENTITY NOT NULL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
string PDO::lastInsertId ([ $name ] );  
```  
  
#### <a name="parameters"></a>Parametri  
$*name*: stringa facoltativa che consente di specificare la tabella.  
  
## <a name="return-value"></a>Valore restituito  
Una stringa dell'identificatore dell'ultima riga aggiunta. Una stringa vuota se la chiamata al metodo ha esito negativo.  
  
## <a name="remarks"></a>Osservazioni  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
   $database = "test";  
   $server = "(local)";  
   $conn = new PDO( "sqlsrv:server=$server; Database = $database", "", "");  
  
   $conn->exec("use Test");  
  
   $ret = $conn->exec("INSERT INTO Table1 VALUES( '19' )");  
   $ret = $conn->exec("INSERT INTO ScrollTest VALUES( 1, '19' )");  
  
   $lastRow = $conn->lastInsertId('Table1');  
   echo $lastRow . "\n";  
  
   // defaults to ScrollTest  
   $lastRow = $conn->lastInsertId();  
   echo $lastRow . "\n";  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

