---
title: 'Attività 9: Configurazione di un servizio dati di riferimento | Documenti Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5a08d3848ddaf65b9e10b654f55e8a0a4d9be690
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171495"
---
# <a name="task-9-configuring-a-reference-data-service"></a>Attività 9: Configurazione di un servizio dati di riferimento
  In questa attività viene configurato DQS per l'utilizzo del servizio dati di riferimento in Windows Azure Marketplace. Nell'attività successiva, si configurerà il **Address Validation** dominio da usare questo servizio. In fase di esecuzione durante l'attività di pulizia, DQS passa i valori dei domini nel **Address Validation** dominio al servizio per la pulizia. Vedere [Configure DQS to Use Reference Data](http://msdn.microsoft.com/library/hh213070.aspx) per altri dettagli.  
  
1.  Nella pagina principale del **Client DQS**nella **amministrazione** riquadro, fare clic su **configurazione**.  
  
2.  Assicurarsi che **i dati di riferimento** scheda è attiva.  
  
3.  Nel **le impostazioni di rete** area, digitare i valori appropriati nel **Server Proxy** e **porta** i campi se è necessario utilizzare un server proxy per la connessione a Internet.  
  
4.  Tipo di **chiave Account di Windows Azure Marketplace** per il **ID Account DataMarket** campo.  
  
     ![Account del servizio dati di Azure Market riferimento Data](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Account del servizio dati di Azure Market riferimento Data")  
  
5.  Fare clic su **Validate** pulsante accanto alla casella di testo per convalidare l'ID dell'account  
  
6.  Fare clic su **OK** nella finestra di messaggio.  
  
7.  Fare clic su **Chiudi** nella parte inferiore della pagina per passare alla pagina principale del Client DQS.  
  
## <a name="next-task"></a>Attività successiva  
 [Attività 10: Configurazione del dominio composito per l'utilizzo di servizio dati di riferimento](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  