---
title: Le istruzioni di definizione dei dati MDX (MultiDimensional Expression) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: abd819871af876d15354af4258c3cd76e0e52197
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579673"
---
# <a name="mdx-data-definition-statements-mdx"></a>Istruzioni MDX per la definizione dei dati (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  In MDX (Multidimensional Expression) le istruzioni per la definizione dei dati consentono di creare, eliminare e manipolare oggetti multidimensionali. Nella tabella seguente vengono elencate le istruzioni per la definizione dei dati disponibili.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Istruzione ALTER CUBE &#40;MDX&#41;](../mdx/mdx-data-definition-alter-cube.md)|Modifica la struttura di un cubo specificato.|  
|[Istruzione CREATE ACTION &#40;MDX&#41;](../mdx/mdx-data-definition-create-action.md)|Crea un'azione che può essere associata a un cubo, a una dimensione, a una gerarchia o a un oggetto subordinato.|  
|[Istruzione CREATE CELL CALCULATION &#40;MDX&#41;](../mdx/mdx-data-definition-create-cell-calculation.md)|Crea una formula di calcolo che valuta un'espressione MDX su un set di tuple specificato all'interno di un cubo.|  
|[Istruzione CREATE GLOBAL CUBE &#40;MDX&#41;](../mdx/mdx-data-definition-create-global-cube.md)|Crea e popola un cubo persistente in locale in base a un sottocubo da un cubo nel server. Non è necessaria una connessione al server per connettersi al cubo locale persistente.|  
|[Istruzione CREATE MEMBER &#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)|Crea un membro calcolato.|  
|[Istruzione CREATE SESSION CUBE &#40;MDX&#41;](../mdx/mdx-data-definition-create-session-cube.md)|Crea e popola un cubo disponibile per tutte le query nella stessa sessione, in base a cubi sul server.|  
|[Istruzione CREATE SET &#40;MDX&#41;](../mdx/mdx-data-definition-create-set.md)|Crea un set denominato per un cubo specificato.|  
|[Istruzione CREATE SUBCUBE &#40;MDX&#41;](../mdx/mdx-data-definition-create-subcube.md)|Ridefinisce in base a un sottocubo specificato lo spazio di un cubo o sottocubo specificato.|  
|[Dichiarazione di azione di rilascio &#40;MDX&#41;](../mdx/mdx-data-definition-drop-action.md)|Elimina un'azione specificata da un cubo specificato.|  
|[Istruzione di calcolo di celle DROP &#40;MDX&#41;](../mdx/mdx-data-definition-drop-cell-calculation.md)|Rimuove la formula per il calcolo di celle specificato.|  
|[Istruzione DROP membro &#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)|Rimuove un membro calcolato.|  
|[Istruzione DROP SET &#40;MDX&#41;](../mdx/mdx-data-definition-drop-set.md)|Rimuove un set denominato.|  
|[DROP SUBCUBE-istruzione &#40;MDX&#41;](../mdx/mdx-data-definition-drop-subcube.md)|Elimina un sottocubo specificato, ripristinando il cubo definito in precedenza o la definizione di sottocubo con il nome specificato.|  
|[Istruzione di aggiornamento cubo &#40;MDX&#41;](../mdx/mdx-data-definition-refresh-cube.md)|Aggiorna la cache del client per un cubo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento istruzione MDX &#40;MDX&#41;](../mdx/mdx-statement-reference-mdx.md)   
 [Istruzioni MDX di manipolazione dei dati &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Istruzioni di Scripting MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
