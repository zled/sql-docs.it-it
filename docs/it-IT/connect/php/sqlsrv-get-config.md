---
title: sqlsrv_get_config | Microsoft Docs
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
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f7792781b5ead7f0b9a8c035d1282ddd4c4c1e0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvgetconfig"></a>sqlsrv_get_config
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce il valore corrente dell'impostazione di configurazione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### <a name="parameters"></a>Parametri  
*$setting*: impostazione di configurazione per la quale viene restituito il valore. Per un elenco di impostazioni configurabili, vedere [sqlsrv_configure](../../connect/php/sqlsrv-configure.md).  
  
## <a name="return-value"></a>Valore restituito  
Il valore dell'impostazione specificata dal parametro *$setting* . Se viene specificata un'impostazione non valida, viene restituito **false** e viene aggiunto un errore alla raccolta degli errori.  
  
## <a name="remarks"></a>Osservazioni  
Se **false** config **sqlsrv_get_config**, è necessario effettuare una chiamata a [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) per determinare se si è verificato un errore oppure se **false** è il valore dell'impostazione specificata dal parametro *$setting* .  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  

[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
