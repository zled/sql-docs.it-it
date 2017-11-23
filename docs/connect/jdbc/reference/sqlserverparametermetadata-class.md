---
title: Classe SQLServerParameterMetaData | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dd97c5667d774829fb801ad22211d338afde1453
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverparametermetadata-class"></a>Classe SQLServerParameterMetaData
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta i metadati per i parametri delle istruzioni preparate.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** lang  
  
 **Implementa:** Java.SQL. parametermetadata  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerParameterMetaData  
```  
  
## <a name="remarks"></a>Osservazioni  
 Per recuperare i metadati del parametro, le istruzioni preparate vengono eseguite con SET FMT ONLY. Le istruzioni disponibili per la chiamata chiamano sp_sproc_columns per recuperare nomi e metadati per i parametri della procedura.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
