---
title: Definire una relazione di tipo fatti e le relative proprietà | Documenti Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c9ac99949cbac77b8a4edd806523acfc073c3dc2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Definire una relazione di tipo Fatti e le relative proprietà
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Quando si definisce una nuova dimensione del cubo o un nuovo gruppo di misure, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tenterà di rilevare se una relazione di tipo fatti e quindi imposta l'utilizzo della dimensione **fatti**. È possibile visualizzare o modificare una relazione di tipo Fatti nella scheda **Utilizzo dimensioni** di Progettazione cubi. La relazione di tipo Fatti tra una dimensione e un gruppo di misure presenta i vincoli seguenti:  
  
-   Una dimensione del cubo può avere un'unica relazione di tipo Fatti con un particolare gruppo di misure.  
  
-   Una dimensione del cubo può avere diverse relazioni di tipo Fatti con più gruppi di misure.  
  
-   L'attributo di granularità per la relazione deve essere l'attributo chiave, ad esempio il numero di transazione, della dimensione. Viene così creata una relazione uno-a-uno tra la dimensione e i fatti della tabella dei fatti.  
  
  
