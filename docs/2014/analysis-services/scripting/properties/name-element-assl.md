---
title: Nome elemento (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Name
helpviewer_keywords:
- Name element
ms.assetid: caf2af86-5f9c-4e14-8168-f3a79248b4fe
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7dde1de33d7ff2219bf2f73696c8a83236b46eb6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211591"
---
# <a name="name-element-assl"></a>Elemento Name (ASSL)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Stringa (fino a 100 caratteri)|  
|Valore predefinito|Variabile|  
|Cardinalità|1-1: elemento obbligatorio che si presenta una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Azione](../objects/action-element-assl.md), [aggregazione](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [AlgorithmParameter](../objects/algorithmparameter-element-assl.md), [annotazione](../objects/annotation-element-assl.md), [ Assembly](../objects/assembly-element-assl.md), [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md), [cubo](../objects/cube-element-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [Database](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [dimensione](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [Gruppo](../objects/group-element-assl.md), [gerarchia](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [livello](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [ Misura](../objects/measure-element-assl.md), [MeasureGroup](../objects/measuregroup-element-assl.md), [MemberProperty](../objects/attributerelationship-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [ Elemento MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [partizione](../objects/partition-element-assl.md), [autorizzazione](../data-type/permission-data-type-assl.md), [ Prospettiva](../objects/perspective-element-assl.md), [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md), [ReportFormatParameter](../objects/reportformatparameter-element-asl.md), [ReportParameter](../objects/reportparameter-element-assl.md), [ Ruolo](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [ServerProperty](../objects/serverproperty-element-assl.md), [traccia](../objects/trace-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Tutti gli elementi che viene usato per definire un oggetto (un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], una gerarchia, un attributo e così via) ha un `Name` elemento rappresenta una proprietà. Il valore di un elemento `Name` ha le seguenti restrizioni.  
  
-   Il valore non deve contenere spazi iniziali o finali. Se gli spazi iniziali o finali sono inclusi nel valore di un elemento `Name`, verranno rimossi implicitamente da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Nel valore non dovrebbero essere contenuti caratteri di controllo. La presenza di caratteri di controllo in un nome è fortemente sconsigliata e può talvolta causare errori di convalida XML.  
  
     Per gli oggetti creati utilizzando il metodo `GetNewName` in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], tramite AMO vengono cercati e, successivamente, rimossi tutti i caratteri di controllo, nonché gli spazi iniziali o finali nel nome. Per questo motivo, l'utilizzo di `GetNewName` è l'approccio consigliato per impostare i nomi degli oggetti.  
  
     Tuttavia, se si imposta direttamente la proprietà `Name`, non vengono effettuati gli stessi controlli di convalida e, pertanto, potrebbero verificarsi errori di convalida XML. L'effettiva generazione di un errore dipende dal carattere di controllo visualizzato nel nome.  
  
     Sebbene i caratteri di controllo non debbano mai essere utilizzati nel nome di un oggetto, non vengono impediti espressamente da Analysis Services. Talvolta, nelle versioni precedenti di Analysis Services venivano accettati i caratteri di controllo nel nome di un oggetto. Per evitare quindi di compromettere le soluzioni precedenti, in [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] verranno ignorati i caratteri di controllo nel nome di un oggetto.  
  
-   Impossibile utilizzare i seguenti valori riservati:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 tramite COM9 (COM1, COM2, COM3 e così via)  
  
    -   CON  
  
    -   LPT1 tramite LPT9 (LPT1, LPT2, LPT3 e così via)  
  
    -   NUL  
  
    -   PRN  
  
 Nella tabella seguente vengono elencati caratteri aggiuntivi che non possono essere utilizzati all'interno del valore di un elemento `Name`, a seconda dell'elemento padre.  
  
|Elemento padre|Caratteri non validi|  
|--------------------|------------------------|  
|[Server](../objects/server-element-assl.md)|Il nome deve seguire le regole per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] i nomi del computer di Windows. Gli indirizzi IP non sono validi.|  
|[Origine dati](../objects/datasource-element-assl.md)|:/\\*&#124;?" [] (){}<>|  
|[Livello](../objects/level-element-assl.md), [attributo a elemento](../objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! + = []{}<>|  
|Tutti gli altri elementi padre|.,;' `:/\\*&#124;?" & % $! + = [] (){}<>|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ID &#40;ASSL&#41;](id-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
