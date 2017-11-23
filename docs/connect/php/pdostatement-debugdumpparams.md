---
title: PDOStatement::debugDumpParams | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf156d65-d933-4235-b89a-18e172d61c15
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6ad0ae3f7149ff2ee9725b746b095167a452535b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="pdostatementdebugdumpparams"></a>PDOStatement::debugDumpParams
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Visualizza un'istruzione preparata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::debugDumpParams();  
```  
  
## <a name="remarks"></a>Osservazioni  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = "Owner";  
  
$stmt = $conn->prepare("select * from Person.ContactType where name = :param");  
$stmt->execute(array($param));  
$stmt->debugDumpParams();  
  
echo "\n\n";  
  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->execute(array($param));  
$stmt->debugDumpParams();  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
