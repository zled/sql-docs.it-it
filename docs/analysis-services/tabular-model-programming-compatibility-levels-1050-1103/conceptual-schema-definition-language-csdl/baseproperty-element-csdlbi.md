---
title: Elemento BaseProperty (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: d0f63e52-7330-4b2c-a929-7a517acc6921
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c0dfb628e7c70edf6e5daf197e3f0d48d4cc9b20
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="baseproperty-element-csdlbi"></a>Elemento BaseProperty (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]L'elemento BaseProperty è un tipo complesso che funge da base per gli altri elementi.  
  
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
  
  
