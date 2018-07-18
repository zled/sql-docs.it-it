---
title: Elemento BaseProperty (CSDLBI) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f1e14b3bcfe862083aa78d634ca20ecaa0f4dd5c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040848"
---
# <a name="baseproperty-element-csdlbi"></a>Elemento BaseProperty (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  L'elemento BaseProperty è un tipo complesso che funge da base per altri elementi.  
  
 Gli attributi possono essere visualizzati in colonne e misure.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento BaseProperty.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Alignment|No|Il nome assegnato al membro (colonna, misura, proprietà di navigazione, gerarchia o livello) definito dall'implementazione del tipo Member|  
|FormatString|No|Nome visualizzato per il membro.|  
|IsRightToLeft|No|Valore booleano che indica se il campo contiene un testo che può essere letto da destra a sinistra.<br /><br /> Se questo attributo viene omesso, viene utilizzata l'impostazione predefinita del modello.|  
|SortDirection|No|Valore che indica la modalità di ordinamento dei valori del campo. Il contenuto di questo attributo è definito dal tipo semplice SortDirection.<br /><br /> Se questo attributo viene omesso, la direzione di ordinamento viene assegnata in base al tipo di dati del campo.|  
|Unità|No|Simbolo applicato ai valori del campo per esprimere unità.<br /><br /> Se omesso, le unità non sono note.|  
  
## <a name="alignment-element"></a>Elemento Alignment  
 Questo tipo semplice definisce il formato di denominazione utilizzato per eliminare le ambiguità dei membri.  
  
|Valore|Description|  
|-----------|-----------------|  
|Nessuno|Utilizzare il nome dell'attributo.|  
|Contesto|Utilizzare il nome della relazione in entrata.|  
|Merge|Concatenare il nome della relazione in entrata e il nome della proprietà in base alle regole della grammatica corrente.|  
  
## <a name="sortdirection-element"></a>Elemento SortDirection  
 Questo tipo semplice definisce il formato di denominazione utilizzato per eliminare le ambiguità dei membri.  
  
|Valore|Description|  
|-----------|-----------------|  
|Nessuno|Utilizzare il nome dell'attributo.|  
|Contesto|Utilizzare il nome della relazione in entrata.|  
|Merge|Concatenare il nome della relazione in entrata e il nome della proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare alla compatibilità 1050 1103 tramite i livelli](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
