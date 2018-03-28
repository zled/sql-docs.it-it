---
title: sqlsrv_get_config | Microsoft Docs
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
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 841cc20172a024ee6f86cfb8151c4f01e70e326e
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
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
  
