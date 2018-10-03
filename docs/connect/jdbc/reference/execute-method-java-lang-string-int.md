---
title: Metodo Execute (lang. String, int[]) | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf42996fac6ac5f48a41311aa072866ebd79f8b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667479"
---
# <a name="execute-method-javalangstring-int"></a>Metodo execute (java.lang.String, int[])

  Esegue l'istruzione SQL specificata, che può restituire più risultati, e segnala a [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] che le chiavi generate automaticamente indicate nella matrice specificata devono essere rese disponibili per il recupero.

## <a name="syntax"></a>Sintassi

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>Parametri
*sql*

Valore **String** contenente un'istruzione SQL.

*columnIndexes*

Matrice di valori **int** che indicano gli indici di colonna delle chiavi generate automaticamente che devono essere resi disponibili.

## <a name="return-value"></a>Valore restituito
**true** se il primo risultato è un set di risultati. In caso contrario, **false**.
  
## <a name="exceptions"></a>Eccezioni
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
Questo metodo execute viene specificato dal metodo execute dell'interfaccia Statement.

## <a name="see-also"></a>Vedere anche

[eseguire il metodo &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[Membri di SQLServerStatement](./sqlserverstatement-members.md)

[Classe SQLServerStatement](./sqlserverstatement-class.md)
