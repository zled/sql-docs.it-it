---
title: Elemento NamingTemplate (ASSL) | Documenti Microsoft
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
api_name:
- NamingTemplate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplate
helpviewer_keywords:
- NamingTemplate element
ms.assetid: d68d765c-f012-40c1-acd4-32741ee2eadf
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d8eb2589b0b33a0b3268e6104b51c3e3612ad894
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069013"
---
# <a name="namingtemplate-element-assl"></a>Elemento NamingTemplate (ASSL)
  Definisce come vengono denominati i livelli in una gerarchia padre-figlio costruita dal [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <NamingTemplate>...</NamingTemplate>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore della `NamingTemplate` elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore del [utilizzo](usage-element-dimensionattribute-assl.md) elemento del `DimensionAttribute` elemento padre è impostato su *padre*).  
  
 Quando un attributo padre viene utilizzato per costruire una gerarchia, i livelli della gerarchia vengono determinati dalle relazioni padre-figlio fra membri contenuti nell'attributo padre. Impossibile dedurre i nomi del livello dai nomi di attributo utilizzati per la gerarchia, a differenza di altre dimensioni.  
  
 Invece, un modello di denominazione viene utilizzato per generare nomi del livello per le gerarchie padre-figlio. L'elemento `NamingTemplate`, definito nell'attributo padre, contiene un'espressione stringa utilizzata per definire nomi di livello. Ci sono due modalità per definire un modello di denominazione per un attributo padre. È possibile progettare un modello di denominazione, oppure è possibile specificare un elenco di nomi.  
  
 Un modello di denominazione contiene un asterisco (`*`come carattere del segnaposto per un contatore incrementato e inserito nel nome di ogni livello nuovo e più profondo. Ad esempio, `Level *`, si risolve in nomi di livello `Level 01`, `Level 02`, `Level 03`e così via, se non viene definito alcun livello (Tutto). Se un modello di denominazione non contiene il carattere del segnaposto, prima si utilizza così come si trova; quindi i nomi del livello successivo vengono creati aggiungendo uno spazio e un numero alla fine del modello. Ad esempio, `Level`, si risolve in nomi di livello `Level`, `Level 01`, `Level 02`e così via.  
  
 Per utilizzare un set specifico di nomi per la denominazione, il valore dell'elemento `NamingTemplate` viene impostato su un elenco di nomi del livello delimitato da punto e virgola. Ogni nome nell'elenco viene utilizzato per un nome del livello successivo. Se il numero di livelli supera il numero di nomi nell'elenco, l'ultimo nome nell'elenco viene utilizzato come modello per qualsiasi nome del livello aggiuntivo, con uno spazio e un numero ordinale aggiunti all'ultimo nome come descritto precedentemente. Ad esempio, `Division;Group;Unit`, si risolve in nomi di livello `Division`, `Group`, `Unit``Unit 01`, `Unit 02`e così via. Contrariamente, `Division;Group;Unit *` si risolve in nomi di livello `Division`, `Group``Unit 03`, `Unit 04`e così via.  
  
 Ogni nome nell'elenco viene trattato come modello per assicurare unicità di nomi di livello. Ad esempio, `Manager;Team Lead;Manager;Team Lead;Worker *`, si risolve in nomi di livello `Manager`, `Team Lead`, `Manager 01`, `Team Lead 01`, `Worker 05`, `Worker 06`.  
  
 Utilizzare due asterischi (*) per includere l'asterisco (\*) carattere in un nome di livello come parte di un modello di denominazione.  
  
 L'elemento che corrisponde al padre di `NamingTemplate` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento NamingTemplateTranslations &#40;ASSL&#41;](../collections/translations-element-assl.md)   
 [Tipo di dati DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  