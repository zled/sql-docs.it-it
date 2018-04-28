---
title: Metodo Execute (lang. String, int[]) | Documenti Microsoft
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
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86e02aa3ec56deffefe81ad5ebe4d282ecd10d53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="execute-method-javalangstring-int"></a>Metodo execute (java.lang.String, int[])

  Esegue l'istruzione SQL specificata, che può restituire più risultati e segnala [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion-md.md)] che le chiavi generate automaticamente indicate nella matrice specificata devono essere rese disponibili per il recupero.

## <a name="syntax"></a>Sintassi

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>Parametri
*sql*

Oggetto **stringa** che contiene un'istruzione SQL.

*columnIndexes*

Matrice di **int**che indica gli indici di colonna delle chiavi generate automaticamente che devono essere rese disponibili.

## <a name="return-value"></a>Valore restituito
**true** se il primo risultato è un set di risultati. In caso contrario, **false**.
  
## <a name="exceptions"></a>Eccezioni
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Osservazioni
Questo metodo execute viene specificato dal metodo execute nell'interfaccia Java.SQL. Statement.

## <a name="see-also"></a>Vedere anche

[eseguire il metodo &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[Membri di SQLServerStatement](./sqlserverstatement-members.md)

[Classe SQLServerStatement](./sqlserverstatement-class.md)
