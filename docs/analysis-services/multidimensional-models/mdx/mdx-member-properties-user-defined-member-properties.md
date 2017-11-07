---
title: "Proprietà dei membri (MDX) definito dall'utente | Documenti Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 12bc5ca42588d81e99490a4ed836c5e71dac49e2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-member-properties---user-defined-member-properties"></a>Proprietà di membro MDX - proprietà dei membri definite dall'utente
  Le proprietà dei membri definite dall'utente possono essere aggiunte a uno specifico livello denominato di una dimensione come relazioni tra attributi. Le proprietà dei membri definite dall'utente non possono essere aggiunte al livello **(All)** (Tutti) di una gerarchia né alla gerarchia stessa.  
  
## <a name="creating-user-defined-member-properties"></a>Creazione delle proprietà dei membri definite dall'utente  
 Le proprietà dei membri definite dall'utente possono essere aggiunte a dimensioni o cubi basati su server tramite l'interfaccia utente o a livello di programmazione:  
  
-   Per aggiungere proprietà dei membri definite dall'utente tramite l'interfaccia utente, usare Progettazione dimensioni in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Per altre informazioni, vedere [Definire relazioni tra attributi](../../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
-   Per aggiungere proprietà dei membri definite dall'utente a livello di programmazione, è possibile utilizzare AMO (Analysis Manager Objects) o una combinazione di XMLA (XML for Analysis) e ASSL (Analysis Services Scripting Language). Per altre informazioni, vedere [Relazioni tra attributi](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Recupero delle proprietà dei membri definite dall'utente  
 Per recuperare le proprietà dei membri definite dall'utente è possibile usare la parola chiave **PROPERTIES** o la funzione [Proprietà](../../../mdx/properties-mdx.md) .  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Utilizzo della parola chiave PROPERTIES per il recupero delle proprietà dei membri definite dall'utente  
 La sintassi da utilizzare per il recupero delle proprietà dei membri definite dall'utente è simile a quella utilizzata per il recupero delle proprietà intrinseche dei membri dei livelli, come illustrato di seguito:  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 La parola chiave **PROPERTIES** compare dopo l'espressione set che specifica l'asse. Nella query MDX seguente, ad esempio, la parola chiave **PROPERTIES** recupera le proprietà membro definite dall'utente `List Price` e `Dealer Price` , quindi viene visualizzata dopo l'espressione set che identifica i prodotti venduti a gennaio:  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a>Utilizzo della funzione Properties per il recupero delle proprietà dei membri definite dall'utente  
 In alternativa, per accedere alle proprietà personalizzate dei membri è possibile usare la funzione **Proprietà** . Nella query MDX seguente viene ad esempio usata la parola chiave **WITH** per creare un membro calcolato costituito dalla proprietà `List Price` di un membro:  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 Per altre informazioni sulla compilazione di membri calcolati, vedere [Compilazione di membri calcolati in MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle proprietà dei membri &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [Proprietà &#40; MDX &#41;](../../../mdx/properties-mdx.md)  
  
  

