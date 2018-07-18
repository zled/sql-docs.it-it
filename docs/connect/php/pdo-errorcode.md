---
title: PDO::errorCode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73bc57c0519c3371b77e38b00b7cc2a8a203b811
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307901"
---
# <a name="pdoerrorcode"></a>PDO::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO::errorCode recupera il valore SQLSTATE dell'ultima operazione dell'handle di database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
mixed PDO::errorCode();  
```  
  
## <a name="return-value"></a>Valore restituito  
PDO::errorCode restituisce un valore SQLSTATE di cinque caratteri sotto forma di stringa oppure NULL se non sono state eseguite operazioni nell'handle di database.  
  
## <a name="remarks"></a>Remarks  
PDO:: ErrorCode nel driver PDO_SQLSRV restituisce avvisi circa alcune operazioni riuscite. Ad esempio, per una connessione riuscita, PDO:: ErrorCode restituisce "01000" che indica SQL_SUCCESS_WITH_INFO.  
  
PDO::errorCode recupera i codici di errore solo per le operazioni eseguite direttamente sul database. Se si crea un'istanza di PDOStatement mediante PDO:: Prepare o PDO:: query e un errore viene generato per l'oggetto istruzione, PDO:: ErrorCode non recuperare tale errore. Sarà necessario chiamare PDOStatement::errorCode per recuperare il codice di errore relativo a un'operazione eseguita su un particolare oggetto istruzione.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
In questo esempio, il nome della colonna errato (`Cityx` anziché `City`), causando un errore, che viene quindi segnalato.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
