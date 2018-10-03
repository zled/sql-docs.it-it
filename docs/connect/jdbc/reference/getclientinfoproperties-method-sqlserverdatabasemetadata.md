---
title: Metodo getClientInfoProperties (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0d9ae2b4adf53e54b53acfe6dd334fe072a308d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47691742"
---
# <a name="getclientinfoproperties-method-sqlserverdatabasemetadata"></a>Metodo getClientInfoProperties (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un elenco di proprietà delle informazioni client supportate dal driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto set di risultati.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getClientInfoProperties viene specificato dal metodo getClientInfoProperties nell'interfaccia DatabaseMetaData.  
  
> [!NOTE]  
>  Questo metodo restituisce un set di risultati vuoto. Il driver supporta l'impostazione solo il **NomeApplicazione** e imposta la **applicationName** solo al momento della connessione. SQL Server non supporta l'aggiornamento delle informazioni sull'applicazione client una volta stabilita la connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
