---
title: ErrorInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9d5481d5-13bc-4388-b3aa-78676c0fc709
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16810cbe7ba634661cf7a1e22c44b69144e66769
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606321"
---
# <a name="pdoerrorinfo"></a>PDO::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera informazioni dettagliate sugli errori dell'ultima operazione dell'handle di database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array PDO::errorInfo();  
```  
  
## <a name="return-value"></a>Valore restituito  
Una matrice di informazioni sugli errori dell'ultima operazione dell'handle di database. La matrice include i campi seguenti:  
  
-   Codice di errore SQLSTATE.  
  
-   Codice di errore specifico del driver.  
  
-   Messaggio di errore specifico del driver.  
  
Se non si verificano errori o se il valore di SQLSTATE non è impostato, i campi specifici del driver sono NULL.  
  
## <a name="remarks"></a>Remarks  
PDO::errorInfo recupera solo le informazioni sugli errori per le operazioni eseguite direttamente sul database. Usare PDOStatement::errorInfo quando viene creata un'istanza di PDOStatement mediante PDO::prepare o PDO::query.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
In questo esempio il nome della colonna errato (`Cityx` anziché `City`) causa un errore, che viene quindi segnalato.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
echo "\n";  
print_r ($conn->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
