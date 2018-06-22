---
title: Editor vincoli di precedenza | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1753bb3469b5909bfd74728eca1f3a49fd4f2ba9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062417"
---
# <a name="precedence-constraint-editor"></a>Editor vincoli di precedenza
  Utilizzare la finestra di dialogo **Editor vincoli di precedenza** per configurare i vincoli di precedenza.  
  
## <a name="options"></a>Opzioni  
 **Operazione di valutazione**  
 Consente di specificare l'operazione di valutazione utilizzata dal vincolo di precedenza. Le operazioni sono **Vincolo**, **Espressione**, **Espressione e vincolo**e **Espressione o vincolo**.  
  
 **Value**  
 Consente di specificare il valore di vincolo, ovvero **Operazione completata**, **Errore**oppure **Completamento**.  
  
> [!NOTE]  
>  La riga del vincolo di precedenza è di colore verde in caso di **Esito positivo**, evidenziata per **Esito negativo**e blu per **Completamento**.  
  
 **Espressione**  
 Se si usano le operazioni **Espressione**, **Espressione e vincolo**o **Espressione o vincolo**, digitare un'espressione o avviare Generatore di espressioni per creare l'espressione. L'espressione deve restituire un valore booleano.  
  
 **Test**  
 Consente di convalidare l'espressione.  
  
 **AND logico**  
 Selezionare questa opzione per specificare che devono essere valutati contemporaneamente più vincoli di precedenza nello stesso file eseguibile. Tutti i vincoli devono restituire `True`.  
  
> [!NOTE]  
>  Questo tipo di vincolo di precedenza viene visualizzato come riga di colore verde, evidenziata o blu continua.  
  
 **OR logico**  
 Selezionare questa opzione per specificare che devono essere valutati contemporaneamente più vincoli di precedenza nello stesso file eseguibile. Almeno un vincolo deve restituire `True`.  
  
> [!NOTE]  
>  Questo tipo di vincolo di precedenza viene visualizzato come riga di colore verde, evidenziata o blu tratteggiata.  
  
## <a name="see-also"></a>Vedere anche  
 [Vincoli di precedenza](control-flow/precedence-constraints.md)   
 [Attività di Integration Services](control-flow/integration-services-tasks.md)   
 [Contenitori in Integration Services](control-flow/integration-services-containers.md)   
 [Espressioni di Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md)  
  
  