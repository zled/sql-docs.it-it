---
title: 'Attività 9: Configurazione di un servizio dati di riferimento | Microsoft Docs'
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
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3a743fd3fe576296a67072762cdfa3a186584cd0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326857"
---
# <a name="task-9-configuring-a-reference-data-service"></a>Attività 9: Configurazione di un servizio dati di riferimento
  In questa attività viene configurato DQS per l'utilizzo del servizio dati di riferimento in Windows Azure Marketplace. Nell'attività successiva, si configurerà il **Address Validation** dominio per usare questo servizio. In fase di esecuzione durante l'attività di pulizia, DQS passa i valori dei domini nel **Address Validation** dominio al servizio per la pulizia. Visualizzare [Configure DQS to Use Reference Data](http://msdn.microsoft.com/library/hh213070.aspx) per altri dettagli.  
  
1.  Nella pagina principale del **Client DQS**, nella **amministrazione** riquadro, fare clic su **configurazione**.  
  
2.  Assicurarsi che **i dati di riferimento** scheda è attiva.  
  
3.  Nel **le impostazioni di rete** area, digitare i valori appropriati nel **Server Proxy** e **porta** campi se è necessario usare un server proxy per connettersi a Internet.  
  
4.  Tipo di **chiave di Account di Windows Azure Marketplace** per il **ID Account DataMarket** campo.  
  
     ![Account del servizio dati riferimento dati Azure Market](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Account del servizio dati riferimento mercato dei dati di Azure")  
  
5.  Fare clic su **Validate** pulsante accanto alla casella di testo per convalidare l'ID dell'account.  
  
6.  Fare clic su **OK** nella finestra di messaggio.  
  
7.  Fare clic su **Chiudi** nella parte inferiore della pagina per passare alla pagina principale del Client DQS.  
  
## <a name="next-task"></a>Attività successiva  
 [Attività 10: Configurazione del dominio composito per usare il servizio dati di riferimento](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
