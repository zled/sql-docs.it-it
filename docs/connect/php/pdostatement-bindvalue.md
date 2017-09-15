---
title: PDOStatement::bindValue | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c006ba33bad8d0afb010b0f0bbe316d7a5e3e28f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Associa un valore a un segnaposto denominato o punto interrogativo nell'istruzione SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::bindValue( $parameter, $value [,$data_type] );  
```  
  
#### <a name="parameters"></a>Parametri  
$*parametro*: un identificatore di parametro (misto). Per un'istruzione che usa segnaposti denominati, un nome di parametro (:name). Per un'istruzione preparata che usa la sintassi punto interrogativo, questo sarà l'indice in base 1 del parametro.  
  
$*valore*: il valore (misto) da associare al parametro.  
  
$*data_type*: il tipo di dati (intero) facoltativo rappresentato da una costante PDO::PARAM_ *. Il valore predefinito è PDO::PARAM_STR.  
  
## <a name="return-value"></a>Valore restituito  
TRUE in caso di esito positivo; in caso contrario, FALSE.  
  
## <a name="remarks"></a>Osservazioni  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
Questo esempio mostra che dopo l'associazione del valore di $contact, la modifica del valore non modifica il valore passato nella query.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

