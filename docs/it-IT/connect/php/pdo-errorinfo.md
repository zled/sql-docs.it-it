---
title: PDO::errorInfo | Microsoft Docs
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
ms.assetid: 9d5481d5-13bc-4388-b3aa-78676c0fc709
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f9dae03d323b0ca557a93d29ebe41551fd562f3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
Se non si è verificato alcun errore o se SQLSTATE non è impostato, i campi specifici del driver sono NULL.  
  
## <a name="remarks"></a>Osservazioni  
PDO::errorInfo recupera solo le informazioni sugli errori per le operazioni eseguite direttamente sul database. Usare PDOStatement::errorInfo quando viene creata un'istanza di PDOStatement mediante PDO::prepare o PDO::query.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
In questo esempio, il nome della colonna errato (`Cityx` anziché `City`), causando un errore, che viene quindi segnalato.  
  
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

[PDO](http://php.net/manual/book.pdo.php)  
  
