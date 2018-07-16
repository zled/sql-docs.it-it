---
title: Proprietà di un livello | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- user hierarchies [Analysis Services]
- hierarchies [Analysis Services], user
ms.assetid: dabb7335-887b-442a-b67c-4901ba1242b7
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28c5c9149d1734f410417df1d727b81e6e86ea1a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288047"
---
# <a name="level-properties"></a>Proprietà di livello 
  Nella tabella seguente vengono elencate e descritte le proprietà di un livello in una gerarchia definita dall'utente.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|Description|Contiene la descrizione del livello.|  
|HideMemberIf|Indica se e quando un membro di un livello deve essere nascosto per le applicazioni client. I possibili valori della proprietà sono i seguenti:<br /><br /> Never<br /> I membri non vengono mai nascosti. Si tratta del valore predefinito.<br /><br /> OnlyChildWithNoName<br /> Un membro viene nascosto quando il membro è l'unico figlio del relativo padre e il nome del membro è vuoto.<br /><br /> OnlyChildWithParentName<br /> Un membro viene nascosto quando il membro è l'unico figlio del relativo padre e il nome del membro è uguale a quello del relativo padre.<br /><br /> NoName<br /> Un membro viene nascosto quando il nome del membro è vuoto.<br /><br /> ParentName<br /> Un membro viene nascosto quando il nome del membro è uguale a quello del relativo padre.|  
|ID|Contiene l'identificatore univoco (ID) del livello.|  
|nome|Contiene il nome descrittivo del livello. Per impostazione predefinita, il nome di un livello è uguale al nome dell'attributo di origine.|  
|SourceAttribute|Contiene il nome dell'attributo di origine sul quale si basa il livello.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà delle gerarchie definite dall'utente](user-hierarchies-properties.md)  
  
  
