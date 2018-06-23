---
title: Aggiornamento di Monitoraggio attività processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9e31951f2e0bd3c954ae7ee1fb20d1a982005603
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069830"
---
# <a name="job-activity-monitor-refresh"></a>Aggiornamento di Monitoraggio attività processi
  Utilizzare la finestra di dialogo **Impostazioni aggiornamento** per configurare la frequenza di acquisizione di nuove informazioni sull'attività del server da parte di Monitoraggio attività processi. Monitoraggio attività processi deve eseguire query sul server monitorato per ottenere informazioni per la griglia Monitoraggio attività processi. Quando l'intervallo di aggiornamento automatico è impostato su un valore inferiore a 30 secondi, il tempo impiegato per eseguire queste query può ridurre le prestazioni del server.  
  
 Per aprire questa finestra di dialogo fare clic su **Visualizza impostazioni di aggiornamento**nella sezione **Stato** di Monitoraggio attività processi.  
  
## <a name="options"></a>Opzioni  
 **Aggiorna automaticamente ogni**  
 Selezionare questa opzione per iniziare l'aggiornamento automatico delle informazioni di Monitoraggio attività. Questa opzione è deselezionata per impostazione predefinita.  
  
 **secondi**  
 Il numero di secondi che intercorrono tra i tentativi di aggiornamento automatici. Il valore predefinito è 60 secondi. Quando questa opzione è impostata su un valore uguale o inferiore a 5 l'aggiornamento viene eseguito comunque ogni 5 secondi.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio delle attività del processo](../../ssms/agent/monitor-job-activity.md)  
  
  