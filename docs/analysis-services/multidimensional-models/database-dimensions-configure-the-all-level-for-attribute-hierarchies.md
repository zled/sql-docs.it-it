---
title: Configurare il livello (totale) per le gerarchie di attributi | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2378dafcda0d9eca8786fb81cadfd44b22d0998b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="database-dimensions---configure-the-all-level-for-attribute-hierarchies"></a>Le dimensioni del database, configurare il livello (totale) per le gerarchie di attributi
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]il livello (Totale) è un livello facoltativo generato dal sistema. Contiene un solo membro il cui valore è determinato dall'aggregazione dei valori di tutti i membri nel livello immediatamente subordinato. Questo membro è denominato membro Totale. Si tratta di un membro generato dal sistema non contenuto nella tabella della dimensione. Poiché il membro nel livello (Totale) si trova al primo livello della gerarchia, il relativo valore è determinato dall'aggregazione consolidata dei valori di tutti i membri della gerarchia. Il membro Totale spesso funge da membro predefinito di una gerarchia.  
  
 La presenza di un livello (Totale) nella gerarchia di un attributo dipende dall'impostazione della proprietà **IsAggregatable** dell'attributo, mentre la presenza di un livello (Totale) in una gerarchia definita dall'utente dipende dall'impostazione della proprietà **IsAggregatable** dell'attributo nel livello superiore della gerarchia definita dall'utente. Se la proprietà **IsAggregatable** è impostata su **True**, esisterà un livello (Totale). Se la proprietà **IsAggregatable** è impostata su **False**il livello (Totale) non sarà presente.  
  
## <a name="establishing-the-topmost-level"></a>Determinazione del livello superiore  
 Se la proprietà **IsAggregatable** è impostata su **False** nell'attributo di origine di un livello di una gerarchia, la gerarchia non potrà contenere un livello aggregabile al di sopra di tale livello. È necessario che il livello non aggregabile sia il livello superiore di qualsiasi gerarchia oppure che la proprietà **IsAggregatable** degli attributi di origine in qualsiasi livello al di sopra di quello non aggregabile sia anch'essa impostata su **False**.  
  
## <a name="all-member-and-all-level"></a>Membro Totale e livello (Totale)  
 Il singolo membro del livello (Totale) è denominato membro Totale. La proprietà **AttributeAllMemberName**di una dimensione specifica il nome del membro Totale per gli attributi in una dimensione. La proprietà **AllMemberName** di una gerarchia specifica il nome del membro Totale per la gerarchia.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire un membro predefinito](../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
