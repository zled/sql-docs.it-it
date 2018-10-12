---
title: Metodo getClientInfo () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a89f2afa50b0ee1b83e72c05bf675d49dac662ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757769"
---
# <a name="getclientinfo-method-"></a>Metodo getClientInfo ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un elenco che contiene il nome e il valore corrente di ogni proprietà delle informazioni client supportata dal driver JDBC.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto Properties che contiene il nome e il valore corrente di ogni proprietà delle informazioni client supportata dal driver.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getClientInfo viene specificato dal metodo getClientInfo nell'interfaccia Java.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non supporta alcuna proprietà delle informazioni client. Di conseguenza, questo metodo restituisce un oggetto di proprietà vuoto.  
  
 Analogamente, le applicazioni possono usare il metodo [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) della classe [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) per recuperare un elenco delle proprietà delle informazioni client supportate dal driver. Il metodo [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) restituisce un set di risultati vuoto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
