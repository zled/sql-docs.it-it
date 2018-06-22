---
title: Stato Preparazione aggiornamento | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Upgrade Advisor [SQL Server], analysis progress status
- analyzing system [Upgrade Advisor], progress information
- SQL Server Upgrade Advisor, analysis progress status
- monitoring analysis progress
- progress information [Upgrade Advisor]
- status information [Upgrade Advisor]
ms.assetid: a9e3d1c8-d492-4beb-93c7-f1bc40d4a910
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e1b867360b773253ae22d24a76ce00b35c589d96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069751"
---
# <a name="upgrade-advisor-progress"></a>Stato Preparazione aggiornamento
  L'analisi di Preparazione aggiornamento inizia con un analizzatore dedicato che esegue un'analisi di ogni componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selezionato. Come i componenti vengono analizzati, lo stato viene segnalato nel **lo stato di avanzamento** finestra di dialogo.  
  
## <a name="options"></a>Opzioni  
 **Azione**  
 Specifica il componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selezionato per l'analisi.  
  
 **Stato**  
 Visualizza il valore relativo allo stato restituito dall'interfaccia di avanzamento dei componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Message**  
 Visualizza i messaggi di errore oppure quelli relativi a esito positivo o negativo restituiti dal singolo analizzatore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Se l'analisi risulta troppo lenta, è possibile arrestarla, chiudere l'Analisi guidata di Preparazione aggiornamento e quindi eseguire nuovamente la procedura guidata. Per ridurre i tempi di analisi, selezionare un numero minore di componenti da analizzare.  
  
 Al termine dell'analisi, il report viene scritto in un file. È possibile visualizzare il report facendo clic **avvia Report** per avviare il Visualizzatore di report da questa pagina. Se si desidera visualizzare il report in un secondo momento, è possibile aprire il **Visualizzatore Report di preparazione aggiornamento** dalla pagina iniziale di preparazione aggiornamento.  
  
> [!NOTE]  
>  I report precedenti vengono salvati ogni volta che si analizza un server. I report vengono salvati utilizzando il valore timestamp come nome del file. Nel visualizzatore di report vengono visualizzati gli ultimi cinque report salvati.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: avvio di preparazione aggiornamento](../../../2014/sql-server/install/how-to-launch-upgrade-advisor.md)   
 [Procedura: eseguire l'analisi guidata di preparazione aggiornamento](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Componenti di SQL Server](../../../2014/sql-server/install/sql-server-components.md)   
 [Riferimento all'interfaccia utente di preparazione aggiornamento](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Utilizzo di preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  