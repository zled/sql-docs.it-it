---
title: Elemento Original (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Original Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.original
- http://schemas.microsoft.com/analysisservices/2003/engine#Original
- urn:schemas-microsoft-com:xml-analysis#Original
helpviewer_keywords: Original element
ms.assetid: c98a3700-ac19-4341-85d9-5afedf662601
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 99b48bd1ddba0aa4ffab888103c7392a56a8d188
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="original-element-xmla"></a>Elemento Original (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contiene il percorso di archiviazione del sistema file originale utilizzato da un [cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Folder>  
   ...  
   <Original>...</Original>  
   ...  
</Folder>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **originale** elemento contiene un percorso UNC da sostituire con il valore di [nuovo](../../../analysis-services/xmla/xml-elements-properties/new-element-xmla.md) elemento contenuto nell'elemento padre **cartella** elemento per tutti gli oggetti ripristinati o sincronizzati, rispettivamente, durante un [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) o [Sincronizza](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) comando. Il valore di questo elemento viene confrontato con il valore della [StorageLocation](../../../analysis-services/scripting/properties/storagelocation-element-assl.md) elemento per ogni cubo, gruppo di misure o partizione e, se viene trovata una corrispondenza, il valore della **New** elemento viene usato per aggiornare il  **StorageLocation** dell'oggetto durante il ripristino o la sincronizzazione.  
  
 Per ulteriori informazioni sul backup e ripristino di oggetti, vedere [backup, ripristino e sincronizzazione di database &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
