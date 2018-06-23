---
title: Elemento roles (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Roles Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Roles
helpviewer_keywords:
- Roles element
ms.assetid: 4191b7ce-bae4-4200-8550-3904420efafd
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f8ced51e40e2804054a0c63368622d2df70f81fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166261"
---
# <a name="roles-element-assl"></a>Elemento Roles (ASSL)
  Contiene la raccolta di elementi [Role](../objects/role-element-assl.md) definiti all'interno dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database> <!-- or Server -->  
   ...  
   <Roles>  
      <Role>...</Role>  
   </Roles>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Database](../objects/database-element-assl.md), [Server](../objects/server-element-assl.md)|  
|Elementi figlio|[Ruolo](../objects/role-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 L'elemento `Roles` associato a un elemento `Server` contiene solo uno ruolo, denominato Administrators, che rappresenta il ruolo di amministratore del server. Il ruolo di amministratore del server non può essere modificato o eliminato, né altri ruoli possono essere aggiunti alla raccolta.  
  
 L'elemento `Roles` associato a un elemento `Database` contiene i ruoli definiti per il database.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.RoleCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  