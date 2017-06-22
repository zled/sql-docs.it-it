---
title: Opzioni di convalida delle sottoscrizioni (sottoscrizioni transazionali) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: da21a38bf0797bf5368ddba1d1c2a47824bad369
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Opzioni di convalida delle sottoscrizioni (sottoscrizioni transazionali)
  La finestra di dialogo **Opzioni di convalida delle sottoscrizioni** consente di specificare se la convalida deve utilizzare solo un conteggio di righe o un conteggio di righe e un checksum binario.  
  
## <a name="options"></a>Opzioni  
 **Verificare che il Sottoscrittore includa lo stesso numero di righe di dati replicati del server di pubblicazione**  
 Consente di selezionare il tipo di convalida del conteggio di righe da eseguire. Per le pubblicazioni Oracle, l'unica opzione disponibile è **Esegui il conteggio di righe effettivo tramite una query diretta nelle tabelle**.  
  
 **Confronta i valori di checksum per la verifica dei dati delle righe**  
 Oltre al conteggio delle righe nel server di pubblicazione e nel Sottoscrittore, viene calcolato un checksum di tutti i dati utilizzando l'algoritmo di checksum binario. In caso di esito negativo durante il conteggio delle righe il checksum non viene eseguito.  
  
 **Arresta l'agente di distribuzione al termine della convalida**  
 Per impostazione predefinita, l'agente di distribuzione viene eseguito in modo continuativo. Selezionare questa opzione per arrestare l'agente dopo l'esecuzione della convalida. In tal modo è possibile controllare se la convalida è riuscita prima di continuare la replica dei dati nel Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Convalidare i dati nel Sottoscrittore](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [Convalidare i dati replicati](../../relational-databases/replication/validate-replicated-data.md)  
  
  
