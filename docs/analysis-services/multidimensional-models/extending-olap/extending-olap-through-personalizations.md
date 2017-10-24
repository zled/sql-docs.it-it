---
title: Estensione di OLAP tramite personalizzazioni | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a676978e37f257293b863786c3bcfae103ed4c4
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="extending-olap-through-personalizations"></a>Estensione di OLAP tramite personalizzazioni
  Analysis Services fornisce diverse funzioni intrinseche da utilizzare con i linguaggi MDX (Multidimensional Expressions) e le estensioni DMX (Data Mining). Queste funzioni sono progettate per consentire l'esecuzione di qualsiasi operazione, dai calcoli statistici standard all'attraversamento dei membri di una gerarchia. Come avviene per qualsiasi altro prodotto complesso e affidabile, tuttavia, si è avvertita l'esigenza di estendere ulteriormente le funzionalità di questo servizio.  
  
 A tale scopo, Analysis Services offre la possibilità di aggiungere assembly ed estensioni personalizzate a un'istanza del servizio, per soddisfare le diverse esigenze aziendali ogni volta che le funzionalità standard si rivelano insufficienti.  
  
## <a name="assemblies"></a>Assembly  
 Gli assembly consentono di estendere la funzionalità business dei linguaggi MDX e DMX. È necessario compilare la funzionalità desiderata in una libreria, ad esempio in una libreria a collegamento dinamico (DLL), quindi aggiungere tale libreria come assembly a un'istanza o a un database di Analysis Services. I metodi pubblici della libreria vengono quindi esposti come funzioni definite dall'utente in espressioni MDX e DMX, procedure, calcoli, azioni e applicazioni client.  
  
## <a name="personalized-extensions"></a>Estensioni personalizzate  
 Le estensioni della personalizzazione di SQL Server Analysis Services rappresentano la struttura di base dell'implementazione di un'architettura plug-in. Le estensioni della personalizzazione di Analysis Services rappresentano una semplice ed elegante modifica all'architettura dell'assembly gestito esistente e vengono esposte nel modello a oggetti <xref:Microsoft.AnalysisServices.AdomdServer> di Analysis Services, nella sintassi MDX e nei set di righe degli schemi.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modelli multidimensionali](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Analysis Services Personalization Extensions](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
  

