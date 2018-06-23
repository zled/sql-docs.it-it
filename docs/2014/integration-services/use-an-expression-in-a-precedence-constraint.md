---
title: Utilizzare un'espressione in un vincolo di precedenza | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e9752ccb8a925f144abc256db01a6eab683e7d6b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171251"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a>Utilizzo di un'espressione in un vincolo di precedenza
  Questa procedura descrive come aggiungere un'espressione a un vincolo di precedenza tramite la finestra di dialogo **Editor vincoli di precedenza**. È possibile aggiungere un'espressione a un vincolo di precedenza solo se il pacchetto include almeno due eseguibili, costituiti da attività o contenitori, connessi da un vincolo di precedenza.  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a>Per aggiungere un'espressione a un vincolo di precedenza  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo** .  
  
4.  Nell'area di progettazione della scheda **Flusso di controllo** fare doppio clic sul vincolo di precedenza. Verrà aperta la finestra di dialogo **Editor vincoli di precedenza** .  
  
5.  Selezionare **Espressione**, **Espressione e vincolo**o **Espressione o vincolo** nell'elenco **Operazione valutazione** .  
  
6.  Digitare un'espressione nella casella di testo **Espressione** o avviare Generatore di espressioni per creare un'espressione.  
  
7.  Per convalidare la sintassi dell'espressione, fare clic su **Test**.  
  
8.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Vincoli di precedenza](control-flow/precedence-constraints.md)   
 [Connessione di attività e contenitori tramite un vincolo di precedenza predefinito](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Impostare il valore di un vincolo di precedenza tramite il Menu di scelta rapida](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Impostare le proprietà di un vincolo di precedenza](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)   
 [Espressioni di Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)  
  
  