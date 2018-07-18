---
title: Estensione di OLAP tramite personalizzazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf7785c3acd3815f78e656951e8ae3f05e125245
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280357"
---
# <a name="extending-olap-through-personalizations"></a>Estensione di OLAP tramite personalizzazioni
  In Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] sono disponibili diverse funzioni intrinseche da utilizzare con i linguaggi MDX (Multidimensional Expressions) e DMX (Data Mining Extensions). Queste funzioni sono progettate per consentire l'esecuzione di qualsiasi operazione, dai calcoli statistici standard all'attraversamento dei membri di una gerarchia. Come avviene per qualsiasi altro prodotto complesso e affidabile, tuttavia, si è avvertita l'esigenza di estendere ulteriormente le funzionalità di questo servizio.  
  
 A tale scopo, Analysis Services offre la possibilità di aggiungere assembly ed estensioni personalizzate a un'istanza del servizio, per soddisfare le diverse esigenze aziendali ogni volta che le funzionalità standard si rivelano insufficienti.  
  
## <a name="assemblies"></a>Assembly  
 Gli assembly consentono di estendere la funzionalità business dei linguaggi MDX e DMX. È necessario compilare la funzionalità desiderata in una libreria, ad esempio in una libreria a collegamento dinamico (DLL), quindi aggiungere tale libreria come assembly a un'istanza o a un database di Analysis Services. I metodi pubblici della libreria vengono quindi esposti come funzioni definite dall'utente in espressioni MDX e DMX, procedure, calcoli, azioni e applicazioni client.  
  
## <a name="personalized-extensions"></a>Estensioni personalizzate  
 Le estensioni della personalizzazione di SQL Server Analysis Services rappresentano la struttura di base dell'implementazione di un'architettura plug-in. Le estensioni della personalizzazione di Analysis Services rappresentano una semplice ed elegante modifica all'architettura dell'assembly gestito esistente e vengono esposte nel modello a oggetti <xref:Microsoft.AnalysisServices.AdomdServer> di Analysis Services, nella sintassi MDX e nei set di righe degli schemi.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modelli multidimensionali](../multidimensional-model-assemblies-management.md)   
 [Analysis Services Personalization Extensions](analysis-services-personalization-extensions.md)  
  
  
