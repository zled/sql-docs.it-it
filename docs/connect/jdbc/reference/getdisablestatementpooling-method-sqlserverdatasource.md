---
title: Metodo getDisableStatementPooling (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7da0c0139af73e207a4aa28ae6e99fc291039da
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634599"
---
# <a name="getdisablestatementpooling-method-sqlserverdatasource"></a>Metodo getDisableStatementPooling (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il valore del **disableStatementPooling** proprietà di connessione. Questa impostazione controlla se l'istruzione di limitazione delle richieste è abilitata o meno per questa connessione.

  
## <a name="syntax"></a>Sintassi  
  
```
public boolean getDisableStatementPooling();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **booleana** che contiene il valore di **disableStatementPooling** proprietà di connessione.
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e progressiva.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
