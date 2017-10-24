---
title: Unione di partizioni (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5528a4392eb5e6554cafc179e0ceedc14b26c0c7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="merging-partitions-xmla"></a>Unione di partizioni (XMLA)
  Se le partizioni hanno la stessa progettazione delle aggregazioni e una struttura, è possibile unire la partizione usando il [MergePartitions](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md) comando XML for Analysis (XMLA). L'unione è un'azione particolarmente importante da eseguire quando si gestiscono partizioni, soprattutto per le partizioni che contengono dati cronologici partizionati in base alla data.  
  
 Un cubo finanziario può utilizzare ad esempio due partizioni:  
  
-   Una partizione rappresenta i dati finanziari per l'anno corrente utilizzando impostazioni di archiviazione OLAP relazionale (ROLAP) in tempo reale per motivi di prestazioni.  
  
-   Un'altra partizione contiene dati finanziari per gli anni precedenti utilizzando impostazioni di archiviazione OLAP multidimensionale (MOLAP) per l'archiviazione.  
  
 Entrambe le partizioni utilizzano impostazioni di archiviazione diverse, ma la stessa progettazione delle aggregazioni. Anziché elaborare il cubo attraverso anni di dati cronologici alla fine dell'anno, è possibile utilizzare invece il **MergePartitions** comando per unire la partizione per l'anno corrente della partizione degli anni precedenti. In questo modo è possibile mantenere i dati aggregati senza che sia necessaria un'elaborazione completa del cubo che potrebbe richiedere molto tempo.  
  
## <a name="specifying-partitions-to-merge"></a>Specifica di partizioni da unire  
 Quando il **MergePartitions** comando viene eseguito, i dati aggregati archiviati nelle partizioni di origine specificate nella [origine](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) proprietà viene aggiunta alla partizione di destinazione specificata nella [destinazione ](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md) proprietà.  
  
> [!NOTE]  
>  Il **origine** proprietà può contenere più di un riferimento all'oggetto di partizione. Tuttavia, il **destinazione** non è di proprietà.  
  
 Per essere unite, le partizioni specificate in entrambi i **origine** e **destinazione** deve essere incluso nello stesso gruppo di misure e utilizzare la stessa progettazione delle aggregazioni. In caso contrario si verifica un errore.  
  
 Le partizioni specificate nel **origine** vengono eliminati dopo il **MergePartitions** comando è stato completato correttamente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Description  
 Nell'esempio seguente vengono unite tutte le partizioni nel **Customer Counts** gruppo di misure del **Adventure Works** cubo il **Adventure Works DW** esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database nel **Customers_2004** partizione.  
  
### <a name="code"></a>Codice  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

