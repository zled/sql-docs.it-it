---
title: Elemento AllowOverwrite (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AllowOverwrite Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.allowoverwrite
- urn:schemas-microsoft-com:xml-analysis#EndSession
helpviewer_keywords:
- AllowOverwrite element
ms.assetid: e7e92481-5f29-47f2-9efd-4e5e60c002bb
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c47939bfc376589512fad8d4eb5367c9dc7fe5fb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="allowoverwrite-element-xmla"></a>Elemento AllowOverwrite (XMLA)
  Determina se l'elemento padre [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) o [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando tenta di sovrascrivere il file di destinazione o il database.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <AllowOverwrite>...</AllowOverwrite>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|False|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ripristino](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per **Backup** comandi, il **AllowOverwrite** elemento determina se il comando può sovrascrivere il file di backup specificato nella **File** elemento.  
  
 Per **ripristinare** elementi, il **AllowOverwrite** elemento determina se il comando può sovrascrivere il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database specificato nella **DatabaseName** elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DatabaseName &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/databasename-element-xmla.md)   
 [Elemento file &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

