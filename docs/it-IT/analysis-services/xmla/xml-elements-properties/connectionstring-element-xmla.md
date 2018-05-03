---
title: Elemento ConnectionString (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ConnectionString Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.connectionstring
- urn:schemas-microsoft-com:xml-analysis#ConnectionString
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionString
helpviewer_keywords:
- ConnectionString element
ms.assetid: 3b0575aa-79ed-4f14-ae7e-dd587af4cdb1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 45f89128f21362b1a1eb936be04bf17e1a450178
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connectionstring-element-xmla"></a>Elemento ConnectionString (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una stringa di connessione utilizzata dall'elemento padre [percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) o [origine](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Cardinalità|  
|------------------------|-----------------|  
|[Percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|1-1: elemento obbligatorio visualizzato una sola volta.|  
|[Origine](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [origine](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per **percorso** elementi, il **ConnectionString** elemento contiene la stringa di connessione utilizzata dal **ripristinare** o **Sincronizza** comando per aggiornare un'origine dati locale o connettersi a un'istanza remota.  
  
 Per **origine** elementi, il **ConnectionString** elemento contiene la stringa di connessione utilizzata dal **Sincronizza** comando per connettersi all'istanza di origine.  
  
 Per ulteriori informazioni sul backup e ripristino di oggetti, vedere [backup, ripristino e sincronizzazione di database & #40; XMLA & #41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristinare l'elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Sincronizzare elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
