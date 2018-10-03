---
title: sqlsrv_get_config | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3aa0093405e197e2ad65c3dea5b5eedbd7e9efc9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641989"
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
  
## <a name="remarks"></a>Remarks  
Se **false** config **sqlsrv_get_config**, è necessario effettuare una chiamata a [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) per determinare se si è verificato un errore oppure se **false** è il valore dell'impostazione specificata dal parametro *$setting* .  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  

[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
