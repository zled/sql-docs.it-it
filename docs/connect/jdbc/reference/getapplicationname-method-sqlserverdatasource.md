---
title: Metodo getApplicationName (SQLServerDataSource) | Documenti Microsoft
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
apiname:
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 12b6e13acc5e88f223298a0eb4c5d13aba602f43
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getapplicationname-method-sqlserverdatasource"></a>Metodo getApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il nome dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il nome dell'applicazione o "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]" se è impostato alcun valore.  
  
## <a name="remarks"></a>Osservazioni  
 Il nome dell'applicazione viene utilizzato per identificare l'applicazione specifica nei diversi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] strumenti di registrazione e analisi. Se il nome dell'applicazione non è impostato, il metodo getApplicationName restituisce la stringa non localizzata "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]".  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
