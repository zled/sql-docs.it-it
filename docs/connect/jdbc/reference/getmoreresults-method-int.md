---
title: Metodo getMoreResults (int) | Documenti Microsoft
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
- SQLServerStatement.getMoreResults (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6419e5a8-8b3a-4d5b-8226-95865c52c723
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75609ec8f24674dd7ff9d1a6724cbc458be47f84
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32837746"
---
# <a name="getmoreresults-method-int"></a>Metodo getMoreResults (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Passa al risultato successivo di questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) riguarda eventuali risultati attualmente aperti e oggetto impostate oggetti in base alle istruzioni specificate dalla modalità fornita.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final boolean getMoreResults(int mode)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Modalità*  
  
 Un **int** che indica come gestire gli oggetti del set di risultati attualmente aperto. Deve essere una delle costanti seguenti:  
  
 CLOSE_CURRENT_RESULT  
  
 KEEP_CURRENT_RESULT (non supportata dal driver JDBC)  
  
 CLOSE_ALL_RESULTS  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il risultato restituito è un set di risultati. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getMoreResults viene specificato dal metodo getMoreResults nell'interfaccia Java.SQL. Statement.  
  
 Se il metodo getMoreResults viene chiamato prima del recupero dei risultati, si comporta come specificato da di *modalità* argomento e passa al risultato successivo.  
  
> [!NOTE]  
>  Il driver JDBC non supporta l'utilizzo della costante KEEP_CURRENT_RESULT. Se utilizzata, verrà generata un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getMoreResults &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
