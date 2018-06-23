---
title: Elemento Detach | Documenti Microsoft
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
- Detach command
ms.assetid: adbc7920-2a4a-4842-9e6f-37006fa19ff8
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e63bad3a6bbedc847307530cfa7a7afcd4138263
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156270"
---
# <a name="detach-element"></a>Elemento Detach
  Scollega un database [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] dall'istanza del server corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Detach>  
      <Object>...</Object>  
      <Password>...</Password>  
   </Detach>  
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
|Elementi figlio|[Oggetto](../xml-elements-properties/object-element-xmla.md)<br /><br /> [Password](../xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Elemento Attach](attach-element.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Proprietà readwritemode del database](../../multidimensional-models/database-readwritemodes.md)   
 [Passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  