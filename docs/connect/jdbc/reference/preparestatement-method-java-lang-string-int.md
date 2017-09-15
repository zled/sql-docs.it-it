---
title: Metodo (lang) prepareStatement | Documenti Microsoft
ms.custom: 
ms.date: 02/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c2452837aba5b8c5a146c12de838a3259f65be38
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="preparestatement-method-javalangstring"></a>Metodo prepareStatement (java.lang.String)

Crea un [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md) oggetto per l'invio di parametri di istruzioni SQL al database.

## <a name="syntax"></a>Sintassi

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>Parametri
*SQL*

Oggetto **stringa** contenente un'istruzione SQL.

## <a name="return-value"></a>Valore restituito
Un oggetto PreparedStatement.

## <a name="exceptions"></a>Eccezioni  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Osservazioni
Questo metodo prepareStatement viene specificato dal metodo prepareStatement nell'interfaccia Java.SQL. Connection.

## <a name="see-also"></a>Vedere anche

[Metodo prepareStatement &#40; SQLServerConnection &#41;](./preparestatement-method-sqlserverconnection.md)

[Membri di SQLServerConnection](./sqlserverconnection-members.md)

[Classe SQLServerConnection](./sqlserverconnection-class.md)

