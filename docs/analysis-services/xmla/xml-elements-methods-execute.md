---
title: Metodo Execute (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 56a48ffaf6d290d99503d7c8e1018f17e8d99a33
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods---execute"></a>Eseguire gli elementi XML - metodi-
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Invia XML per i comandi Analysis (XMLA) a un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Include richieste che comportano il trasferimento dei dati, ad esempio recuperando o aggiornando dati nel server.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
 **Azione SOAP** "urn: schemas-microsoft-com: XML-analysis: eseguire"  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|Nessuno|  
|Elementi figlio|[Comando](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md), [parametri](../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md), [proprietà](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Execute** comandi XMLA forniti nell'esecuzione del metodo di **comando** elemento e restituisce eventuali dati risultanti utilizzando XMLA [set di righe](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) tipo di dati (per i risultati tabulari Imposta) o XMLA [MDDataSet](../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) del tipo di dati (per il set di risultati multidimensionali.)  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito è riportato un esempio di un **Execute** chiamata al metodo che contiene un'istruzione SELECT di MDX (Multidimensional Expressions).  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML & #40; XMLA & #41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Metodo Discover &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)   
 [I metodi &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [Gli elementi XML & #40; XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Set di righe dello Schema di Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
