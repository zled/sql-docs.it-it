---
title: PDOStatement::bindValue | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 099da725f1d8103499ea5a6a31f2cf2ca0538249
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983503"
---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Associa un valore a un segnaposto denominato o punto interrogativo nell'istruzione SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::bindValue($parameter, $value[, $data_type]);  
```  
  
#### <a name="parameters"></a>Parametri  
$*parameter*: identificatore del parametro (misto). Per un'istruzione che usa segnaposti denominati, usare un nome parametro (:name). Per un'istruzione preparata che usa la sintassi punto interrogativo, è l'indice in base 1 del parametro.
  
$*value*: valore (misto) da associare al parametro.  
  
$*data_type*: tipo di dati (intero) facoltativo rappresentato da una costante PDO::PARAM_*. Il valore predefinito è PDO::PARAM_STR.  
  
## <a name="return-value"></a>Valore restituito  
TRUE in caso di esito positivo; in caso contrario, FALSE.  
  
## <a name="remarks"></a>Remarks  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
Questo esempio mostra che dopo l'associazione del valore di $contact, la modifica del valore non modifica il valore passato nella query.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```

> [!NOTE]
> È consigliabile usare le stringhe come input durante l'associazione di valori da un [colonna decimal o numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) per garantire precisione e accuratezza come PHP ha limitato la precisione per [numeri a virgola mobile](http://php.net/manual/en/language.types.float.php). Lo stesso vale per le colonne di tipo bigint, soprattutto quando i valori sono di fuori dell'intervallo di un' [integer](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a>Esempio  
Questo esempio di codice viene illustrato come associare un valore decimale come parametro di input.  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
