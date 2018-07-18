---
title: Opzioni di convalida delle sottoscrizioni (sottoscrizioni di tipo merge) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ba1d468b04ab25ee97cacde6ef582f193d8a1856
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166752"
---
# <a name="subscription-validation-options-merge-subscriptions"></a>Opzioni di convalida delle sottoscrizioni (sottoscrizioni di tipo merge)
  Utilizzare la finestra di dialogo **Opzioni di convalida delle sottoscrizioni** per specificare se la convalida deve utilizzare solo il conteggio delle righe o deve utilizzare il conteggio delle righe e il checksum binario.  
  
## <a name="options"></a>Opzioni  
 **Verifica solo il conteggio delle righe**  
 Consente di verificare che la tabella nel Sottoscrittore abbia lo stesso numero di righe della tabella nel server di pubblicazione. Questa opzione non convalida la corrispondenza del contenuto delle righe. La convalida del conteggio delle righe è un controllo non approfondito che consente comunque di evidenziare eventuali problemi dei dati.  
  
 **Verifica il conteggio delle righe e confronta i valori di checksum per la verifica dei dati delle righe**  
 Oltre al conteggio delle righe nel server di pubblicazione e nel Sottoscrittore, viene calcolato un checksum di tutti i dati utilizzando l'algoritmo di checksum binario. In caso di esito negativo durante il conteggio delle righe il checksum non viene eseguito. Questa opzione non è valida per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Convalidare i dati nel Sottoscrittore](validate-data-at-the-subscriber.md)   
 [Convalidare i dati replicati](validate-replicated-data.md)  
  
  
