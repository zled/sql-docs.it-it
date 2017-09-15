---
title: 'Pdostatement:: Execute | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2e80566-fa41-4918-8521-cf2e05374cbd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b98b91afada5f484843188729996e0b55472f765
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementexecute"></a>PDOStatement::execute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Esegue un'istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::execute ([ $input ] );  
```  
  
#### <a name="parameters"></a>Parametri  
*$input*: (facoltativo) matrice associativa contenente i valori per i marcatori di parametro.  
  
## <a name="return-value"></a>Valore restituito  
true se ha esito positivo; in caso contrario, false.  
  
## <a name="remarks"></a>Osservazioni  
Le istruzioni eseguite con PDOStatement::execute devono prima essere preparate con [PDO::prepare](../../connect/php/pdo-prepare.md). Per informazioni su come specificare l'esecuzione di istruzioni diretta o preparata, vedere [Esecuzione di istruzioni diretta e preparata nel driver PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md) .  
  
Tutti i valori della matrice di parametri di input vengono trattati come valori PDO::PARAM_STR.  
  
Se l'istruzione preparata include marcatori di parametro, è necessario chiamare PDOStatement::bindParam per associare le variabili PHP ai marcatori di parametro o passare una matrice di valori di parametro solo input.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query );  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
  
echo "\n";  
$param = "Owner";  
$query = "select * from Person.ContactType where name = ?";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

