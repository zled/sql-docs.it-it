---
title: Metodo (lang) getClientInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb792035b5926d94654dec3a445599165cd5fbdf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645809"
---
# <a name="getclientinfo-method-javalangstring"></a>Metodo getClientInfo (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore di una proprietà delle informazioni client specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>Parametri  
 *name*  
  
 Valore String contenente il nome della proprietà delle informazioni client da recuperare.  
  
## <a name="return-value"></a>Valore restituito  
 Valore String contenente il valore della proprietà delle informazioni client.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getClientInfo viene specificato dal metodo getClientInfo nell'interfaccia Java.  
  
 Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non supporta alcuna proprietà delle informazioni client. Di conseguenza, questo metodo restituisce **null**.  
  
 Analogamente, le applicazioni possono usare il metodo [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) della classe [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) per recuperare un elenco delle proprietà delle informazioni client supportate dal driver. Il metodo [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) restituisce un set di risultati vuoto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
