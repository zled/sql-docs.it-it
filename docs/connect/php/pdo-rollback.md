---
title: PDO::rollback | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d918c1e3-1be0-4001-b3b0-000db6d9e8b8
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bdb5d1e59e1b2d29225568abf53d3f6bf90d03d0
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="pdorollback"></a>PDO::rollback
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Elimina i comandi di database che sono stati rilasciati dopo la chiamata a [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) e restituisce la connessione in modalità di commit automatico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDO::rollBack ();  
```  
  
## <a name="return-value"></a>Valore restituito  
true se la chiamata al metodo ha avuto esito positivo; in caso contrario, false.  
  
## <a name="remarks"></a>Osservazioni  
PDO::rollback non è influenzato e non influisce sul valore di PDO::ATTR_AUTOCOMMIT.  
  
Per un esempio d'uso di PDO::rollback, vedere [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) .  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
