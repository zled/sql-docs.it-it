---
title: Metodo Discover (XMLA) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 921afc6d17a0eddcba48e5a6a6064810a3b3b6ef
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979103"
---
# <a name="xml-elements---methods---discover"></a>Elementi XML - metodi - individuazione
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Recupera informazioni, ad esempio l'elenco dei database disponibili o i dettagli su un oggetto specifico, da un'istanza di Analysis Services. I dati recuperati con il metodo **Discover** dipendono dai valori dei parametri passati al metodo stesso.  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
 **Azione SOAP** "urn:schemas-microsoft-com:xml-analysis:Discover"  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Discover>  
   <RequestType>...</RequestType>  
   <Restrictions>...</Restrictions>  
   <Properties>...</Properties>  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|None|  
|Elementi figlio|[Le proprietà](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md), [RequestType](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md), [restrizioni](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il **Discover** metodo richiede i metadati sulle istanze e oggetti. I metadati vengono restituiti utilizzando XMLA [set di righe](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) tipo di dati.  
 
> [!TIP] 
> Se non si ha familiarità con i comandi XML, scegliere il modello di query XMLA la **Query** sulla barra degli strumenti in Management Studio per compilare la query e aggiungere i parametri. Per altre informazioni, vedere [Utilizzare i modelli di Analysis Services in SQL Server Management Studio](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md). 
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente, il client invia le **Discover** chiamata per richiedere un elenco di cubi dal [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] database di Analysis Services di esempio:  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>MDSCHEMA_CUBES</RequestType>  
   <Restrictions>  
      <RestrictionList>  
         <CATALOG_NAME>Adventure Works DW Multidimensional 2012</CATALOG_NAME>  
      </RestrictionList>  
   </Restrictions>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Tabular</Format>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="see-also"></a>Vedere anche
 [Tipi di dati XML &#40;XMLA&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Eseguire il metodo &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [I metodi &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [Elementi XML &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Set di righe dello schema di Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
