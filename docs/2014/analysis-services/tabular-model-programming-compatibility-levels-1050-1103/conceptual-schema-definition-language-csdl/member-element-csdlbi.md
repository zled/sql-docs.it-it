---
title: Elemento member (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 1ba225f5-3867-4aae-a519-e3c277688d1e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f193cb746b8df43c33aa65ea3d69d87ab7c36655
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218831"
---
# <a name="member-element-csdlbi"></a>Elemento Member (CSDLBI)
  L'elemento Member è un tipo complesso che funge da base per altri elementi.  
  
 Gli attributi vengano visualizzati in colonne, misure, proprietà di navigazione, gerarchie e livelli.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento Member.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|nome||Il nome assegnato al membro (colonna, misura, proprietà di navigazione, gerarchia o livello) definito dall'implementazione del tipo TMember|  
|Caption|Sì|Nome visualizzato per il membro.|  
|ContextualNameRule|Sì|Il formato di denominazione utilizzato per eliminare le ambiguità dei membri. Il contenuto di questo attributo è definito dal tipo semplice ContextualNameRule.|  
|Hidden||Valore booleano che indica se il membro sarà nascosto per il client.<br /><br /> Il valore predefinito è false, ovvero le colonne sono visibili nel client.|  
|ReferenceName||Identificatore utilizzato per fare riferimento al membro in una query DAX. Se questo attributo viene omesso, il nome del campo viene utilizzato|  
  
## <a name="contextualnamerule-element"></a>Elemento ContextualNameRule  
 Questo tipo semplice definisce il formato di denominazione utilizzato per eliminare le ambiguità dei membri.  
  
|valore|Description|  
|-----------|-----------------|  
|None|Utilizzare il nome dell'attributo.|  
|Contesto|Utilizzare il nome della relazione in entrata.|  
|Merge|Concatenare il nome della relazione in entrata e il nome della proprietà.|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
