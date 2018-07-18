---
title: Nome elemento (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 695e43a2657db97e624c00e46e397fd17a70ae57
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293911"
---
# <a name="name-element-for-server-dta"></a>Elemento Name per Server (DTA)
  Contiene il nome del server in cui si trovano i database che si desidera ottimizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|`string`, tra 1 e 255 caratteri.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta per elemento **Server** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento server &#40;DTA&#41;](server-element-dta.md)|  
|**Elementi figlio**|Nessuna.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento **Name** , vedere [Server Element &#40;DTA&#41;](server-element-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
