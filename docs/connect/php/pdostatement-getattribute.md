---
title: PDOStatement::getAttribute | Documenti Microsoft
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 752f76d161f56ac9a44b1a4c854c6fbe9eba8081
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera il valore di un attributo PDOStatement predefinito o di un attributo personalizzato del driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Parametri  
$*attributo*: un numero intero, una delle PDO::ATTR_ * PDO::SQLSRV_ATTR_\* costanti. Sono supportati gli attributi che è possibile impostare con [pdostatement:: SetAttribute](../../connect/php/pdostatement-setattribute.md), PDO:: sqlsrv_attr_direct_query (per ulteriori informazioni, vedere [esecuzione di istruzioni diretta e preparata nel il Driver PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO:: attr_cursor e PDO:: sqlsrv_attr_cursor_scroll_type (per ulteriori informazioni, vedere [tipi di cursore (Driver PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)).  
  
## <a name="return-value"></a>Valore restituito  
In caso di esito positivo, restituisce un valore misto per un attributo predefinito del PDO o per un attributo personalizzato del driver. In caso di errore, restituisce Null.  
  
## <a name="remarks"></a>Osservazioni  
Per un esempio, vedere [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) .  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
