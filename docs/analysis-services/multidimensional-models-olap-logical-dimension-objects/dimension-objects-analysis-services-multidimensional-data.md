---
title: Dimensione oggetti (Analysis Services - dati multidimensionali) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af27299b776158d34786d7f9c60badd1549f503f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Oggetti dimensione (Analysis Services - Dati multidimensionali)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Una semplice <xref:Microsoft.AnalysisServices.Dimension> oggetto è composto da informazioni di base, attributi e gerarchie. Le informazioni di base includono il nome e il tipo della dimensione, l'origine dati, la modalità di archiviazione e altro. Gli attributi definiscono i dati effettivi nella dimensione. Sebbene gli attributi non appartengano necessariamente a una gerarchia, le gerarchie sono compilate dagli attributi. Una gerarchia crea elenchi ordinati di livelli e definisce le modalità di esplorazione della dimensione da parte di un utente.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Negli argomenti seguenti vengono fornite ulteriori informazioni sulla progettazione e sull'implementazione degli oggetti dimensione.  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Dimensioni &#40;Analysis Services - Dati multidimensionali&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le dimensioni sono un componente essenziale dei cubi. Le dimensioni consentono di organizzare i dati in relazione a un'area di interesse per gli utenti, ad esempio relativa a clienti, archivi o dipendenti.|  
|[Attributi e gerarchie di attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)|Le dimensioni sono raccolte di attributi, associate a una o più colonne in una tabella o una vista della vista origine dati.|  
|[Relazioni tra attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)|In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], gli attributi all'interno di una dimensione sono sempre correlati direttamente o indirettamente all'attributo chiave. Quando si definisce una dimensione in base a uno schema star, in cui tutti gli attributi della dimensione sono derivati dalla stessa tabella relazionale, viene automaticamente definita una relazione tra l'attributo chiave e ogni attributo non chiave della dimensione. Quando si definisce una dimensione in base a uno schema snowflake, in cui gli attributi della dimensione sono derivati da più tabelle correlate, viene automaticamente definita una relazione tra attributi come indicato di seguito:<br /><br /> Tra l'attributo chiave e ogni attributo non chiave associato alle colonne della tabella principale della dimensione.<br /><br /> Tra l'attributo chiave e l'attributo associato alla chiave esterna della tabella secondaria che collega le tabelle delle dimensioni sottostanti.<br /><br /> Tra l'attributo associato alla chiave esterna della tabella secondaria e ogni attributo non chiave associato alle colonne della tabella secondaria.|  
  
  
