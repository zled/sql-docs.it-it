---
title: PDOStatement::closeCursor | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8997ab61-e948-4d54-8d32-fc080d55525c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f380e7fcd6e5cb13c594877309087979f22844d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementclosecursor"></a>PDOStatement::closeCursor
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Chiude il cursore, consentendo all'istruzione di essere eseguita nuovamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::closeCursor();  
```  
  
## <a name="return-value"></a>Valore restituito  
Restituisce true in caso di esito positivo; in caso contrario, false.  
  
## <a name="remarks"></a>Osservazioni  
closeCursor ha effetto quando l'opzione di connessione MultipleActiveResultSets è impostata su false.  Per ulteriori informazioni sull'opzione di connessione MultipleActiveResultSets, vedere [procedura: disabilitare il set di risultati MARS (Multiple Active)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).  
  
Anziché chiamare closeCursor, è anche possibile limitarsi a impostare l'handle di istruzione su Null.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets' => false ) );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
$stmt2 = $conn->prepare('SELECT * FROM HumanResources.Department');  
  
$stmt->execute();  
  
$result = $stmt->fetch();  
print_r($result);  
  
$stmt->closeCursor();  
  
$stmt2->execute();  
$result = $stmt2->fetch();  
print_r($result);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

