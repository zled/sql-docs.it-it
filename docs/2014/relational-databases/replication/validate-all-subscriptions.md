---
title: Convalida tutte le sottoscrizioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
caps.latest.revision: 23
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ae84563b45f05fb7df91d2a00cb2ff0ca9cdd852
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068226"
---
# <a name="validate-all-subscriptions"></a>Convalida tutte le sottoscrizioni
  Utilizzare la finestra di dialogo **Convalida tutte le sottoscrizioni** per specificare che tutte le sottoscrizioni di una pubblicazione di tipo merge devono essere convalidate all'esecuzione successiva dell'agente di merge per ogni sottoscrizione. I risultati della convalida vengono visualizzati in Monitoraggio replica. Per altre informazioni, vedere [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).  
  
 È inoltre possibile convalidare una singola sottoscrizione facendo clic con il pulsante destro del mouse su una sottoscrizione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , quindi scegliendo **Convalida sottoscrizione**.  
  
## <a name="options"></a>Opzioni  
 **Verifica solo il conteggio delle righe**  
 Consente di verificare che la tabella nel Sottoscrittore abbia lo stesso numero di righe della tabella nel server di pubblicazione. Questa opzione non convalida la corrispondenza del contenuto delle righe. La convalida del conteggio delle righe è un controllo non approfondito che consente comunque di evidenziare eventuali problemi dei dati.  
  
 **Verifica il conteggio delle righe e confronta i valori di checksum per la verifica dei dati delle righe**  
 Oltre al conteggio delle righe nel server di pubblicazione e nel Sottoscrittore, viene calcolato un checksum di tutti i dati utilizzando l'algoritmo di checksum binario. In caso di esito negativo durante il conteggio delle righe il checksum non viene eseguito. Questa opzione non è valida per [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Convalidare i dati replicati](validate-replicated-data.md)  
  
  