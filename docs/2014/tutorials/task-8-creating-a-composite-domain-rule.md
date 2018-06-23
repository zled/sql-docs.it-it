---
title: 'Attività 8: Creazione di una regola dominio composito | Documenti Microsoft'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 18461e889e56f647b869d2b60cae49d662786160
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169345"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>Attività 8: Creazione di una regola per un dominio composito
  In questa attività, viene creata una regola per il **Address Validation** dominio composito. Viene definita una regola tra domini: se **City** viene **Los Angeles**, **stato** deve essere **autorità di certificazione** in **Città** e **stato** sono due domini.  
  
1.  Nel riquadro di destra, passare il **regole CD** scheda.  
  
2.  Fare clic su **aggiungere una nuova regola di dominio** dalla barra degli strumenti.  
  
3.  Tipo di **City-state Rule** per **nome** , quindi premere **invio**.  
  
4.  Nel **compila una regola** riquadro, selezionare **Città** nell'elenco di domini e selezionare la condizione **valore è uguale a** e il tipo **Los Angeles** per il valore.  
  
5.  Nel **quindi** riquadro, selezionare **stato** nell'elenco di domini e selezionare **valore è uguale a**, tipo **autorità di certificazione** per il valore e premere **Scheda**.  
  
     ![Regola dominio composito](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "regola dominio composito")  
  
6.  Fare clic su **Chiudi** pulsante nella parte inferiore della pagina per passare alla pagina principale del Client DQS. Nella lezione successiva verrà pubblicata la Knowledge Base. Si noti che la Knowledge Base è nello stato bloccato (icona di blocco).  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 9: Configurazione di un servizio dati di riferimento](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  