---
title: Unione di partizioni (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- merging partitions [XMLA]
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
ms.assetid: 657e1d4d-6d50-40f8-a771-7b20c9d865f8
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3a3de50e053ed8b3e16373e4aa5b162991f286dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332721"
---
# <a name="merging-partitions-xmla"></a>Unione di partizioni (XMLA)
  Se le partizioni hanno la stessa progettazione delle aggregazioni e struttura, è possibile unire la partizione tramite il [MergePartitions](../xmla/xml-elements-commands/mergepartitions-element-xmla.md) comando XML for Analysis (XMLA). L'unione è un'azione particolarmente importante da eseguire quando si gestiscono partizioni, soprattutto per le partizioni che contengono dati cronologici partizionati in base alla data.  
  
 Un cubo finanziario può utilizzare ad esempio due partizioni:  
  
-   Una partizione rappresenta i dati finanziari per l'anno corrente utilizzando impostazioni di archiviazione OLAP relazionale (ROLAP) in tempo reale per motivi di prestazioni.  
  
-   Un'altra partizione contiene dati finanziari per gli anni precedenti utilizzando impostazioni di archiviazione OLAP multidimensionale (MOLAP) per l'archiviazione.  
  
 Entrambe le partizioni utilizzano impostazioni di archiviazione diverse, ma la stessa progettazione delle aggregazioni. Anziché elaborare il cubo attraverso anni di dati cronologici al termine dell'anno, è possibile utilizzare il comando `MergePartitions` per unire la partizione relativa all'anno corrente con quella relativa agli anni precedenti. In questo modo è possibile mantenere i dati aggregati senza che sia necessaria un'elaborazione completa del cubo che potrebbe richiedere molto tempo.  
  
## <a name="specifying-partitions-to-merge"></a>Specifica di partizioni da unire  
 Quando il `MergePartitions` comando viene eseguito, i dati aggregati archiviati nelle partizioni di origine specificate nella [origine](../xmla/xml-elements-properties/source-element-xmla.md) viene aggiunta alla partizione di destinazione specificata nella proprietà il [destinazione](../xmla/xml-elements-properties/target-element-xmla.md) proprietà.  
  
> [!NOTE]  
>  La proprietà `Source` può contenere più di un riferimento all'oggetto partizione, a differenza della proprietà `Target`.  
  
 Per essere unite, le partizioni specificate nelle proprietà `Source` e `Target` devono essere contenute dallo stesso gruppo di misure e devono utilizzare la stessa progettazione delle aggregazioni. In caso contrario si verifica un errore.  
  
 Le partizioni specificate in `Source` vengono eliminate dopo che il comando `MergePartitions` è stato completato correttamente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Description  
 L'esempio seguente unisce tutte le partizioni del **Customer Counts** gruppo di misure del **Adventure Works** cubo la **Adventure Works DW** esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] di database nel **Customers_2004** partizione.  
  
### <a name="code"></a>codice  
  
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
 [Sviluppo con XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
