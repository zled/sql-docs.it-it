---
title: Classe SQLServerException | Documenti Microsoft
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
ms.topic: article
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd15bec08cce38405e9de8e75da9936c6742eb0a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverexception-class"></a>Classe SQLServerException
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta un'esecuzione non riuscita o incompleta di un'istruzione SQL.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** SqlException  
  
 **Implementa:** java.io.Serializable  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>Osservazioni  
 La classe SQLServerException gestisce i codici di stato SQL 92 sia XOPEN. Sono intercambiabili tramite una proprietà di connessione specificata dall'utente. Le eccezioni vengono scritte in qualsiasi file di log aperto che è stato specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
