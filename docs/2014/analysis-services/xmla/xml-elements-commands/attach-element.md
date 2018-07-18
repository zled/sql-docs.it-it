---
title: Elemento Attach | Microsoft Docs
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
helpviewer_keywords:
- Attach command
ms.assetid: a315d1f1-e220-4296-97cb-6d35606b9640
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 12b450f705640de4ab4990c75794f17a82ea83a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321144"
---
# <a name="attach-element"></a>Elemento Attach
  Collega all'istanza del server corrente un database di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] precedentemente scollegato dall'istanza del server corrente o da un'altra istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Attach>  
      <Folder>...</Folder>  
            <ReadWriteMode>...</ReadWriteMode>  
            <Password>...</Password>  
   </Attach>  
</Command>  
  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Cartella](../xml-elements-properties/folder-element-xmla.md)<br /><br /> [ReadWriteMode](../xml-elements-properties/readwritemode-element.md)<br /><br /> [Password](../xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Elemento Detach](detach-element.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Proprietà readwritemode del database](../../multidimensional-models/database-readwritemodes.md)   
 [Passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
