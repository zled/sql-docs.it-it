---
title: Classe SQLServerXAConnection | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f2cc7956f36ee6fad113efd1cfe5afd5f58baff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782989"
---
# <a name="sqlserverxaconnection-class"></a>Classe SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta le connessioni JDBC che possono partecipare alle transazioni distribuite (XA).  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Implementa:** javax.sql.XAConnection  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Remarks  
 Un oggetto SQLServerXAConnection può essere integrato in una transazione distribuita tramite un oggetto [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md). Un responsabile transazioni, generalmente parte di un server di livello intermedio, gestisce un oggetto SQLServerXAConnection tramite l'oggetto SQLServerXAResource.  
  
> [!NOTE]  
>  I programmatori di applicazioni in genere non utilizzano direttamente questa interfaccia. Viene utilizzata principalmente da un responsabile transazioni che utilizza il server di livello intermedio.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Informazioni di riferimento sull'API del driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
