---
title: Classe SQLServerParameterMetaData | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d24d63765f31f6c3218d8ed161af77298326ab7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797225"
---
# <a name="sqlserverparametermetadata-class"></a>Classe SQLServerParameterMetaData
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta i metadati per i parametri delle istruzioni preparate.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.lang.Object  
  
 **Implementa:** java.sql.ParameterMetaData  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerParameterMetaData  
```  
  
## <a name="remarks"></a>Remarks  
 Per recuperare i metadati del parametro, le istruzioni preparate vengono eseguite con SET FMT ONLY. Le istruzioni disponibili per la chiamata chiamano sp_sproc_columns per recuperare nomi e metadati per i parametri della procedura.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Informazioni di riferimento sull'API del driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
