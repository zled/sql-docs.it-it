---
title: "Configurare le proprietà delle misure | Documenti Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- additivity [Analysis Services]
- ID property
- ErrorConfiguration property
- AggregateFunction property
- DisplayFolder property
- IgnoreUnrelatedDimensions property
- FormatString property
- Description property
- semiadditive
- properties [Analysis Services], measure groups
- aggregate functions [Analysis Services]
- DataType property
- ProcessingMode property
- MeasureExpression property
- AggregationPrefix property
- Visible property
- properties [Analysis Services], measures
- StorageLocation property
- StorageMode property
- formats [Analysis Services], measures
- Source property
- aggregations [Analysis Services], measures
- measures [Analysis Services], properties
- nonadditive [Analysis Services]
- Name property
- measures [Analysis Services], display formats
- ProcessingPriority property
- measure groups [Analysis Services], properties
- Type property
- ProactiveCaching property
ms.assetid: e9031078-c4f5-4986-b0c9-4d064b622ab7
caps.latest.revision: "50"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e0ff496e40e85387e492fc6cfe355035c0e271ee
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="configure-measure-properties"></a>Configurare le proprietà delle misure
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Le misure sono incluse proprietà che consentono di definire come la funzione di misure e per controllare come le misure vengono visualizzate agli utenti.  
  
 È possibile impostare proprietà in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] durante la creazione o la modifica di un cubo o una misura. Queste proprietà possono essere impostate anche a livello di programmazione mediante MDX o AMO. Per informazioni dettagliate, vedere [Creare misure e gruppi di misure nei modelli multidimensionali](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md) o [Istruzione CREATE MEMBER &#40;MDX&#41;](../../mdx/mdx-data-definition-create-member.md) o [Programmazione di oggetti di base OLAP in AMO](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md).  
  
## <a name="measure-properties"></a>Proprietà delle misure  
 Le misure ereditano alcune proprietà dal gruppo di misure di cui sono membri, a meno che tali proprietà non vengano sostituite a livello di misura. Le proprietà delle misure ne determinano la modalità di aggregazione, il tipo di dati, il nome visualizzato dall'utente, la cartella di visualizzazione in cui appariranno, la stringa di formato, l'espressione, la colonna di origine sottostante e la visibilità da parte degli utenti.  
  
|Proprietà|Definizione|  
|--------------|----------------|  
|**AggregateFunction**|Obbligatorio. Determina la modalità di aggregazione delle misure. **Sum** è l'aggregazione predefinita. Per altre informazioni, vedere [Utilizzare le funzioni di aggregazione](../../analysis-services/multidimensional-models/use-aggregate-functions.md) per una descrizione di ogni funzione.|  
|**DataType**|Obbligatorio. Specifica il tipo di dati della colonna della tabella dei fatti sottostante a cui è associata la misura. Per impostazione predefinita, questo valore viene ereditato dalla colonna di origine.|  
|**Description**|Fornisce una descrizione della misura, che può essere esposta in applicazioni client.|  
|**DisplayFolder**|Specifica la cartella in cui verrà visualizzata la misura quando gli utenti si connettono al cubo. Quando in un cubo sono presenti numerose misure, è possibile usare le cartelle di visualizzazione per categorizzare le misure e migliorare l'esplorazione dell'utente.|  
|**FormatString**|È possibile selezionare il formato in cui gli utenti visualizzeranno i valori della misura usando la proprietà **FormatString** della misura.<br /><br /> Anche se in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]è disponibile un elenco di formati di visualizzazione, è possibile specificare formati aggiuntivi non inclusi nell'elenco. È possibile specificare qualsiasi formato denominato o definito dall'utente che risulti valido in Microsoft Visual Basic.|  
|**ID**|Obbligatorio. Visualizza l'identificatore univoco (ID) della misura. Questa proprietà è di sola lettura.|  
|**MeasureExpression**|Specifica un'espressione MDX vincolata che definisce il valore della misura. L'espressione viene valutata a livello foglia prima dell'aggregazione e consente la ponderazione di un valore, ad esempio in una conversione valuta in cui un importo di vendita viene ponderato in base al tasso di cambio.|  
|**Nome**|Obbligatorio. Specifica il nome della misura.|  
|**Origine**|Obbligatorio. Specifica la colonna nella vista origine dati a cui è associata la misura. Vedere [Origini dati e associazioni &#40;SSAS - multidimensionale&#41;](../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).|  
|**Visible**|Determina la visibilità della misura nelle applicazioni client.|  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare le proprietà dei gruppi di misure](../../analysis-services/multidimensional-models/configure-measure-group-properties.md)   
 [Modifica delle misure](../../analysis-services/lesson-3-1-modifying-measures.md)  
  
  
