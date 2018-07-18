---
title: Costruttore SQLServerBlob (SQLServerConnection, byte) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection, byte[].SQLServerBlob
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d93e5bee03976c5ae9c55247f98ba180e237a4e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32847036"
---
# <a name="sqlserverblob-constructor-sqlserverconnection-byte"></a>Costruttore SQLServerBlob (SQLServerConnection, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inizializza una nuova istanza di [SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md) classe quando viene specificato un [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto e un **byte** matrice.  
  
> [!NOTE]  
>  Questo metodo è deprecato nella versione 2.0 del driver JDBC. Utilizzare invece il [createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public SQLServerBlob(SQLServerConnection connection,  
                     byte[] data)  
```  
  
#### <a name="parameters"></a>Parametri  
 *connessione*  
  
 Oggetto SQLServerConnection.  
  
 *data*  
  
 Oggetto **byte** matrice.  
  
## <a name="see-also"></a>Vedere anche  
 [Costruttori SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [Membri di SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Classe SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
