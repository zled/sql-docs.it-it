---
title: Elemento BaseProperty (CSDLBI) | Microsoft Docs
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
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6de9e321e3cd5122a6252663c533be2d536800d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320841"
---
# <a name="baseproperty-element-csdlbi"></a>Elemento BaseProperty (CSDLBI)
  L'elemento BaseProperty è un tipo complesso che funge da base per altri elementi.  
  
 Gli attributi possono essere visualizzati in colonne e misure.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento BaseProperty.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Alignment|no|Il nome assegnato al membro (colonna, misura, proprietà di navigazione, gerarchia o livello) definito dall'implementazione del tipo Member|  
|FormatString|no|Nome visualizzato per il membro.|  
|IsRightToLeft|no|Valore booleano che indica se il campo contiene un testo che può essere letto da destra a sinistra.<br /><br /> Se questo attributo viene omesso, viene utilizzata l'impostazione predefinita del modello.|  
|SortDirection|no|Valore che indica la modalità di ordinamento dei valori del campo. Il contenuto di questo attributo è definito dal tipo semplice SortDirection.<br /><br /> Se questo attributo viene omesso, la direzione di ordinamento viene assegnata in base al tipo di dati del campo.|  
|Unità|no|Simbolo applicato ai valori del campo per esprimere unità.<br /><br /> Se omesso, le unità non sono note.|  
  
## <a name="alignment-element"></a>Elemento Alignment  
 Questo tipo semplice definisce il formato di denominazione utilizzato per eliminare le ambiguità dei membri.  
  
|valore|Description|  
|-----------|-----------------|  
|None|Utilizzare il nome dell'attributo.|  
|Contesto|Utilizzare il nome della relazione in entrata.|  
|Merge|Concatenare il nome della relazione in entrata e il nome della proprietà in base alle regole della grammatica corrente.|  
  
## <a name="sortdirection-element"></a>Elemento SortDirection  
 Questo tipo semplice definisce il formato di denominazione utilizzato per eliminare le ambiguità dei membri.  
  
|valore|Description|  
|-----------|-----------------|  
|None|Utilizzare il nome dell'attributo.|  
|Contesto|Utilizzare il nome della relazione in entrata.|  
|Merge|Concatenare il nome della relazione in entrata e il nome della proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
