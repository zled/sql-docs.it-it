---
title: 'PDO:: commit | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a0db4a00-9700-4f49-ab16-6522dd1101d3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8b60b75aea820f1f9ef41c099aa8d9b2bb98b875
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979683"
---
# <a name="pdocommit"></a>PDO::commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Invia al database i comandi rilasciati dopo la chiamata a [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) e restituisce la connessione in modalità di commit automatico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDO::commit();  
```  
  
## <a name="return-value"></a>Valore restituito  
true se la chiamata al metodo ha avuto esito positivo; in caso contrario, false.  
  
## <a name="remarks"></a>Remarks  
PDO::commit non è influenzato e non influisce sul valore di PDO::ATTR_AUTOCOMMIT.  
  
Per un esempio d'uso di PDO::commit, vedere [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) .  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
