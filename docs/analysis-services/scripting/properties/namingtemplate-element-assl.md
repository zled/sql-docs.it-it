---
title: Elemento NamingTemplate (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- NamingTemplate Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NamingTemplate
helpviewer_keywords:
- NamingTemplate element
ms.assetid: d68d765c-f012-40c1-acd4-32741ee2eadf
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6a3fb4f2adec6480205fdbe4d704a47e63a7aef4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="namingtemplate-element-assl"></a>Elemento NamingTemplate (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce come vengono denominati i livelli in una gerarchia padre-figlio costruita dal [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <NamingTemplate>...</NamingTemplate>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore della **NamingTemplate** elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore del [utilizzo](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) elemento del **DimensionAttribute** elemento padre è impostato su *padre*).  
  
 Quando un attributo padre viene utilizzato per costruire una gerarchia, i livelli della gerarchia vengono determinati dalle relazioni padre-figlio fra membri contenuti nell'attributo padre. Impossibile dedurre i nomi del livello dai nomi di attributo utilizzati per la gerarchia, a differenza di altre dimensioni.  
  
 Invece, un modello di denominazione viene utilizzato per generare nomi del livello per le gerarchie padre-figlio. Il **NamingTemplate** l'elemento definito nell'attributo padre, contiene un'espressione stringa utilizzata per definire nomi di livello. Ci sono due modalità per definire un modello di denominazione per un attributo padre. È possibile progettare un modello di denominazione, oppure è possibile specificare un elenco di nomi.  
  
 Un modello di denominazione contiene un asterisco (`*`come carattere del segnaposto per un contatore incrementato e inserito nel nome di ogni livello nuovo e più profondo. Ad esempio, `Level *`, si risolve in nomi di livello `Level 01`, `Level 02`, `Level 03`e così via, se non viene definito alcun livello (Tutto). Se un modello di denominazione non contiene il carattere del segnaposto, prima si utilizza così come si trova; quindi i nomi del livello successivo vengono creati aggiungendo uno spazio e un numero alla fine del modello. Ad esempio, `Level`, si risolve in nomi di livello `Level`, `Level 01`, `Level 02`e così via.  
  
 Per utilizzare un set specifico di nomi per la denominazione, il valore della **NamingTemplate** viene impostato su un elenco delimitato da punto e virgola di nomi di livello. Ogni nome nell'elenco viene utilizzato per un nome del livello successivo. Se il numero di livelli supera il numero di nomi nell'elenco, l'ultimo nome nell'elenco viene utilizzato come modello per qualsiasi nome del livello aggiuntivo, con uno spazio e un numero ordinale aggiunti all'ultimo nome come descritto precedentemente. Ad esempio, `Division;Group;Unit`, si risolve in nomi di livello `Division`, `Group`, `Unit``Unit 01`, `Unit 02`e così via. Contrariamente, `Division;Group;Unit *` si risolve in nomi di livello `Division`, `Group``Unit 03`, `Unit 04`e così via.  
  
 Ogni nome nell'elenco viene trattato come modello per assicurare unicità di nomi di livello. Ad esempio, `Manager;Team Lead;Manager;Team Lead;Worker *`, si risolve in nomi di livello `Manager`, `Team Lead`, `Manager 01`, `Team Lead 01`, `Worker 05`, `Worker 06`.  
  
 Utilizzare due asterischi (*) per includere l'asterisco (\*) carattere in un nome di livello come parte di un modello di denominazione.  
  
 L'elemento che corrisponde all'elemento padre **NamingTemplate** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento NamingTemplateTranslations &#40;ASSL&#41;](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)   
 [Tipo di dati DimensionAttribute &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
