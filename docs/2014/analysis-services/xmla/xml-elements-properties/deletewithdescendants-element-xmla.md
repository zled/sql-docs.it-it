---
title: Elemento DeleteWithDescendants (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DeleteWithDescendants Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DeleteWithDescendants
- microsoft.xml.analysis.deletewithdescendants
- urn:schemas-microsoft-com:xml-analysis#DeleteWithDescendants
helpviewer_keywords:
- DeleteWithDescendants element
ms.assetid: adfc9437-aaa7-4364-bcdb-128fcc9a410d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93a6d92e675e0ae016327e064fabb6ec2c012aac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199941"
---
# <a name="deletewithdescendants-element-xmla"></a>Elemento DeleteWithDescendants (XMLA)
  Indica se i discendenti di membri dell'attributo vengono eliminati anche dall'elemento padre [Drop](../xml-elements-commands/drop-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Drop>  
   ...  
   <DeleteWithDescendants>...</DeleteWithDescendants>  
   ...  
</Drop>  
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
|Elementi padre|[DROP](../xml-elements-commands/drop-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il `DeleteWithDescendants` elemento determina se il `Drop` comando deve eliminare i membri dell'attributo identificati dal [in cui](where-element-xmla.md) elemento, ma anche che devono essere eliminati anche i discendenti di quei membri dell'attributo.  
  
> [!NOTE]  
>  Questo elemento si applica solo a membri attributo nelle gerarchie padre-figlio.  
  
 Per altre informazioni sull’eliminazione e l’aggiornamento di membri di attributo, vedere [Inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
