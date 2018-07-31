---
title: Metodo valueOf (java.sql.Timestamp, java.util.Calendar) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2b742e3ccdf297aaa6ede4feb5bb93b04224823
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38039239"
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>Metodo valueOf (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea una **DateTimeOffset** oggetto che rappresenta un punto nel tempo in un particolare offset GMT in base a un valore Java e un valore java.util.Calendar che indica l'offset.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Parametri  
 *timestamp*  
  
 Valore java.sql.Timestamp.  
  
 *calendario*  
  
 Valori di offset.  I componenti della data e ora *calendario* verrà impostato in base al *timestamp* valore.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto DateTimeOffset che rappresenta il punto nel tempo dato dall'oggetto Java al fuso orario dell'oggetto java.util.Calendar specificato.  
  
## <a name="remarks"></a>Remarks  
 Questo metodo imposta inoltre l'oggetto java.util.Calendar al punto nel tempo dato dall'oggetto java.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Membri di DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
