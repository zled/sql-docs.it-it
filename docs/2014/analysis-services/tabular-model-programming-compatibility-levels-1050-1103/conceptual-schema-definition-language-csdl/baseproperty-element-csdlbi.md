---
title: Elemento BaseProperty (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3dcea67deac28838f190947c0b890b86537536c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198811"
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
  
  
