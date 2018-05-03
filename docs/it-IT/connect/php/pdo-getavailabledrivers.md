---
title: 'PDO:: getavailabledrivers | Documenti Microsoft'
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
ms.assetid: eab561e6-1229-401a-9482-008c23f9a4e6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ccc7d27f4e96c2e0694b40edd3b0d9644831f6c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="pdogetavailabledrivers"></a>PDO::getAvailableDrivers
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce una matrice dei driver PDO nell'installazione di PHP.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array PDO::getAvailableDrivers ();  
```  
  
## <a name="return-value"></a>Valore restituito  
Una matrice con l'elenco dei driver PDO.  
  
## <a name="remarks"></a>Osservazioni  
Il nome del driver PDO usato in PDO::__construct per creare un'istanza PDO.  
  
PDO::getAvailableDrivers non deve essere implementata dai driver PHP. Per altre informazioni su questo metodo, vedere la documentazione di PHP.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
print_r(PDO::getAvailableDrivers());  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
