---
title: "Definire una relazione di tipo fatti e le relative proprietà | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 46cf5d6b942751fb0ca76942e8762cec271a5b4c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Definire una relazione di tipo Fatti e le relative proprietà
  Quando si definisce un nuovo gruppo di misure o una nuova dimensione del cubo, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prova a rilevare la presenza di una relazione tra dimensioni dei fatti e quindi imposta l'utilizzo delle dimensioni su **Fatti**. È possibile visualizzare o modificare una relazione di tipo Fatti nella scheda **Utilizzo dimensioni** di Progettazione cubi. La relazione di tipo Fatti tra una dimensione e un gruppo di misure presenta i vincoli seguenti:  
  
-   Una dimensione del cubo può avere un'unica relazione di tipo Fatti con un particolare gruppo di misure.  
  
-   Una dimensione del cubo può avere diverse relazioni di tipo Fatti con più gruppi di misure.  
  
-   L'attributo di granularità per la relazione deve essere l'attributo chiave, ad esempio il numero di transazione, della dimensione. Viene così creata una relazione uno-a-uno tra la dimensione e i fatti della tabella dei fatti.  
  
  
