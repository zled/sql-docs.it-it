---
title: Elemento AllowOverwrite (XMLA) | Microsoft Docs
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
- AllowOverwrite Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.allowoverwrite
- urn:schemas-microsoft-com:xml-analysis#EndSession
helpviewer_keywords:
- AllowOverwrite element
ms.assetid: e7e92481-5f29-47f2-9efd-4e5e60c002bb
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ad153d33b57f7fea763666d19e8e0b44fa155c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190901"
---
# <a name="allowoverwrite-element-xmla"></a>Elemento AllowOverwrite (XMLA)
  Determina se l'elemento padre [Backup](../xml-elements-commands/backup-element-xmla.md) oppure [ripristinare](../xml-elements-commands/restore-element-xmla.md) comando tenta di sovrascrivere il file di destinazione o il database.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <AllowOverwrite>...</AllowOverwrite>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|False|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Copia di backup](../xml-elements-commands/backup-element-xmla.md), [ripristinare](../xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per i comandi `Backup`, l'elemento `AllowOverwrite` determina se il comando può sovrascrivere il file di backup specificato nell'elemento `File`.  
  
 Per `Restore` elementi, il `AllowOverwrite` elemento determina se il comando può sovrascrivere il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database indicato con il `DatabaseName` elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DatabaseName &#40;XMLA&#41;](name-element-xmla.md)   
 [File di elemento &#40;XMLA&#41;](file-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
