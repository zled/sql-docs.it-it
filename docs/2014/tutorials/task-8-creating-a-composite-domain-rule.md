---
title: 'Attività 8: Creazione di una regola dominio composito | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 19b4922446f564435970fbb7f0422a3c98de48df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48151961"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>Attività 8: Creazione di una regola per un dominio composito
  In questa attività viene creata una regola per il **Address Validation** dominio composito. Definire una regola tra domini: se **Città** viene **Los Angeles**, **stato** deve essere **autorità di certificazione** dove **Città** e **stato** sono due domini.  
  
1.  Nel riquadro destro passare al **regole CD** scheda.  
  
2.  Fare clic su **aggiungere una nuova regola di dominio** nella barra degli strumenti.  
  
3.  Tipo di **City-state Rule** per **Name** , quindi premere **invio**.  
  
4.  Nel **compila una regola** riquadro, selezionare **City** nell'elenco di dominio, selezionare la condizione **valore è uguale a** e digitare **Los Angeles** per il valore.  
  
5.  Nel **quindi** riquadro, selezionare **stato** nell'elenco di dominio e selezionare **valore è uguale a**, tipo **autorità di certificazione** per il valore, quindi premere **Scheda**.  
  
     ![Regola dominio composito](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "regola dominio composito")  
  
6.  Fare clic su **Chiudi** nella parte inferiore della pagina per passare alla pagina principale del Client DQS. Nella lezione successiva verrà pubblicata la Knowledge Base. Si noti che la Knowledge Base è nello stato bloccato (icona di blocco).  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 9: Configurazione di un servizio dati di riferimento](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
