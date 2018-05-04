---
title: Nome di elemento (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Name Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Name
helpviewer_keywords:
- Name element
ms.assetid: caf2af86-5f9c-4e14-8168-f3a79248b4fe
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b7111e9321ebc68c7ad29c0278f12622f84800cc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="name-element-assl"></a>Elemento Name (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il nome dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Name>...</Name>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Stringa (fino a 100 caratteri)|  
|Valore predefinito|Variabile|  
|Cardinalità|1-1: elemento obbligatorio che si presenta una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md), [aggregazione](../../../analysis-services/scripting/objects/aggregation-element-assl.md), [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md), [AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md), [annotazione](../../../analysis-services/scripting/objects/annotation-element-assl.md), [ Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md), [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md), [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md), [Database](../../../analysis-services/scripting/objects/database-element-assl.md), [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md), [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [Gruppo](../../../analysis-services/scripting/objects/group-element-assl.md), [gerarchia](../../../analysis-services/scripting/objects/hierarchy-element-assl.md), [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md), [livello](../../../analysis-services/scripting/objects/level-element-assl.md), [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md), [ Misura](../../../analysis-services/scripting/objects/measure-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MemberProperty](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md), [ MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md), [partizione](../../../analysis-services/scripting/objects/partition-element-assl.md), [autorizzazione](../../../analysis-services/scripting/data-type/permission-data-type-assl.md), [ Prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md), [PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md), [ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md), [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md), [ Ruolo](../../../analysis-services/scripting/objects/role-element-assl.md), [Server](../../../analysis-services/scripting/objects/server-element-assl.md), [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md), [traccia](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Ogni elemento che viene utilizzato per definire un oggetto (un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], una gerarchia, un attributo e così via) ha un **nome** elemento come una proprietà. Il valore di un **nome** elemento presenta le restrizioni seguenti:  
  
-   Il valore non deve contenere spazi iniziali o finali. Se gli spazi iniziali o finali sono inclusi nel valore di un **nome** elemento, tali spazi verranno rimossi implicitamente da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Nel valore non dovrebbero essere contenuti caratteri di controllo. La presenza di caratteri di controllo in un nome è fortemente sconsigliata e può talvolta causare errori di convalida XML.  
  
     Per gli oggetti creati utilizzando il **GetNewName** metodo [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], verifica la presenza di AMO e successivamente rimuove i caratteri di controllo, spazi, spazi iniziali o finali nel nome. Per questo motivo, l'utilizzo **GetNewName** è l'approccio consigliato per l'impostazione di nomi di oggetto.  
  
     Tuttavia, se si imposta la **nome** proprietà direttamente, la stessa convalida controlli non vengono eseguiti, potrebbero verificarsi errori di convalida XML. L'effettiva generazione di un errore dipende dal carattere di controllo visualizzato nel nome.  
  
     Sebbene i caratteri di controllo non debbano mai essere utilizzati nel nome di un oggetto, non vengono impediti espressamente da Analysis Services. Talvolta, nelle versioni precedenti di Analysis Services venivano accettati i caratteri di controllo nel nome di un oggetto. Per questo motivo, SQL Server 2016 Analysis Services e versioni successive ignorerà i caratteri di controllo nei nomi degli oggetti per evitare di compromettere le soluzioni precedenti.  
  
-   Impossibile utilizzare i seguenti valori riservati:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 tramite COM9 (COM1, COM2, COM3 e così via)  
  
    -   CON  
  
    -   LPT1 tramite LPT9 (LPT1, LPT2, LPT3 e così via)  
  
    -   NUL  
  
    -   PRN  
  
 Nella tabella seguente sono elencati caratteri aggiuntivi che non possono essere utilizzati all'interno del valore di un **nome** elemento, a seconda dell'elemento padre.  
  
|Elemento padre|Caratteri non validi|  
|--------------------|------------------------|  
|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|Il nome deve seguire le regole per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] i nomi del computer di Windows. Gli indirizzi IP non sono validi.|  
|[Origine dati](../../../analysis-services/scripting/objects/datasource-element-assl.md)|:/\\*&#124;?" [] (){}<>|  
|[Livello](../../../analysis-services/scripting/objects/level-element-assl.md), [attributi elemento](../../../analysis-services/scripting/objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! + = []{}<>|  
|Tutti gli altri elementi padre|.,;' `:/\\*&#124;?" & % $! [] () + ={}<>|  
  
## <a name="see-also"></a>Vedere anche  
 [ID elemento &#40;ASSL&#41;](../../../analysis-services/scripting/properties/id-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
