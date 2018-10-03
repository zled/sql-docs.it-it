---
title: Metodo getApplicationName (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f71e501c-ccd7-4a1e-b6ea-4d47a81c18c6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aad921f5c496500d4f9dc5265568bf2956d8c41a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692909"
---
# <a name="getapplicationname-method-sqlserverdatasource"></a>Metodo getApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il nome dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getApplicationName()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **String** contenente il nome dell'applicazione o "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]" se non è impostato alcun valore.  
  
## <a name="remarks"></a>Remarks  
 Il nome dell'applicazione viene usato per identificare l'applicazione specifica nei diversi strumenti di profiling e registrazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se il nome dell'applicazione non è impostato, il metodo getApplicationName restituisce la stringa non localizzata "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]".  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
