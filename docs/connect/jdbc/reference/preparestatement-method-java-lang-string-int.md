---
title: Metodo (lang) prepareStatement | Documenti Microsoft
ms.custom: ''
ms.date: 02/07/2017
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
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26f242db545a79e27ba72808e6c6ce466dbe5f40
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="preparestatement-method-javalangstring"></a>Metodo prepareStatement (java.lang.String)

Crea un [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md) oggetto per l'invio di parametri di istruzioni SQL al database.

## <a name="syntax"></a>Sintassi

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>Parametri
*sql*

Oggetto **stringa** contenente un'istruzione SQL.

## <a name="return-value"></a>Valore restituito
Un oggetto PreparedStatement.

## <a name="exceptions"></a>Eccezioni  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Osservazioni
Questo metodo prepareStatement viene specificato dal metodo prepareStatement nell'interfaccia Java.SQL. Connection.

## <a name="see-also"></a>Vedere anche

[Metodo prepareStatement &#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[Membri di SQLServerConnection](./sqlserverconnection-members.md)

[Classe SQLServerConnection](./sqlserverconnection-class.md)
