---
title: Metodo valueOf (Java, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 290878fc0a3687a95fd6335eba4b6ed6e1c2fda2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979183"
---
# <a name="valueof-method-javasqltimestamp-int"></a>Metodo valueOf (java.sql.Timestamp, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un oggetto **DateTimeOffset** che rappresenta un punto nel tempo in un particolare offset GMT in base a un valore java.sql.Timestamp e un valore che indica l'offset in minuti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, int minutesOffset)  
```  
  
#### <a name="parameters"></a>Parametri  
 *timestamp*  
  
 Valore java.sql.Timestamp.  
  
 *minutesOffset*  
  
 Offset in minuti.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto DateTimeOffset che rappresenta il punto nel tempo dato dall'oggetto Java in corrispondenza dell'offset specificato, in minuti, rispetto a GMT.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Membri di DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
