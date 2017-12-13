---
title: "Definire una relazione di tipo regolare e le proprietà di relazione di tipo regolare | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
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
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 10025f3c362a0be45d782644ca36a41661e13c68
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Definire una relazione di tipo Regolare e le relative proprietà
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Quando si definisce una nuova dimensione del cubo o un nuovo gruppo di misure, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tenterà di rilevare se una relazione di tipo regolare e quindi imposta l'utilizzo della dimensione **regolare**. È possibile visualizzare o modificare la relazione di una dimensione regolare nella scheda **Utilizzo dimensioni** di Progettazione cubi.  
  
 Quando si definisce la relazione tra una dimensione del cubo e un gruppo di misure, si specifica inoltre l'attributo di granularità per la relazione. L'attributo di granularità definisce il livello di dettaglio più basso disponibile nel cubo per la dimensione, che in genere corrisponde all'attributo chiave per la dimensione. Talvolta, tuttavia, potrebbe essere necessario impostare diversamente la granularità di una particolare dimensione del cubo in un determinato gruppo di misure. Potrebbe ad esempio rivelarsi utile impostare l'attributo di granularità per la dimensione Time su Month anziché su Day, se si utilizza un gruppo di misure Sales Quotas o Budget. Quando si specifica l'attributo di granularità in base a un attributo diverso dall'attributo chiave, è necessario garantire che tutti gli altri attributi della dimensione siano collegati direttamente o indirettamente a quest'altro attributo tramite relazioni tra attributi. In caso contrario, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non sarà in grado di eseguire correttamente l'aggregazione dei dati.  
  
  
