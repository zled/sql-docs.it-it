---
title: Metodo getURL (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dd0d5d2c-91fe-4b0f-a162-69d898ba176e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 005da5eaf520fa1233b3c8ddcf6d42dcf5d8882a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="geturl-method-sqlserverdatasource"></a>Metodo getURL (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce l'URL utilizzato per la connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** contenente l'URL.  
  
## <a name="remarks"></a>Osservazioni  
 Per motivi di sicurezza, non includere la password nell'URL specificato per il [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md) metodo. poiché nei server applicazioni Java di terze parti sarà molto spesso visualizzato il set di valori per la proprietà URL nella relativa interfaccia utente di configurazione dell'origine dati. Utilizzare invece il [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) per impostare il valore della password. Nei server applicazioni Java non sarà visualizzata una password che viene impostata nella relativa origine dati nell'interfaccia utente di configurazione.  
  
> [!NOTE]  
>  Se il metodo setURL non viene chiamato prima di chiamare il metodo getURL, getURL restituisce il valore predefinito "JDBC: / /".  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
