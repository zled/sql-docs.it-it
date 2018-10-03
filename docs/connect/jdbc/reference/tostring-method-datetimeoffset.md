---
title: Metodo toString (DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e77b9be3-1a02-4769-8acf-ac71d48d6a76
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 990cb7cccd972ac926824ca3f8d99de3f0d6e305
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687739"
---
# <a name="tostring-method-datetimeoffset"></a>Metodo toString (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce una rappresentazione di stringa del **DateTimeOffset** oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public String toString()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Rappresentazione di stringa del **DateTimeOffset** oggetto.  
  
## <a name="remarks"></a>Remarks  
 La stringa ha il formato *YYYY*-*MM*-*gg * * hh*:*mm*:*ss*[. *fffffff*] [+ |-]*hh*:*mm*.  
  
 Nei secondi frazionari della stringa restituita vengono aggiunti zero alla precisione dichiarata. Ad esempio, un **datetimeoffset(6)** con un valore di "12:34:56.78 2010-03-10-08:00" verrà formattato da DateTimeOffset. ToString come "12:34:56.780000 2010-03-10-08:00".  
  
## <a name="see-also"></a>Vedere anche  
 [Classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Membri di DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
