---
title: "Impostare il tempo e l'intervallo di inattività della CPU (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 96c5e3d4a011b83cc9d0fff0edfbd740a5b34fd1
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a>Impostazione del tempo e della durata di inattività della CPU (SQL Server Management Studio)
In questo argomento viene illustrato come definire la condizione di inattività della CPU per il server in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. La definizione del tempo di inattività della CPU influisce sulla modalità di risposta agli eventi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Si supponga, ad esempio, di considerare la CPU inattiva quando l'utilizzo medio scende sotto il 10% e rimane tale per 10 minuti. Se sono stati definiti processi da eseguire quando la CPU del server raggiunge una condizione di inattività, questi verranno avviati quando l'utilizzo della CPU scende sotto il 10% e rimane tale per 10 minuti. Se si tratta di processi che influiscono significativamente sulle prestazioni del server, la corretta definizione della condizione di inattività della CPU è particolarmente importante.  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>Per impostare il tempo e l'intervallo di inattività della CPU  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, scegliere **Proprietà**e selezionare la pagina **Avanzate** .  
  
3.  In **Condizione di inattività CPU**eseguire le operazioni seguenti:  
  
    -   Selezionare la casella di controllo **Imposta condizione di inattività CPU**.  
  
    -   Specificare una percentuale nella casella **L'uso medio della CPU è inferiore al** (per tutte le CPU). In questo modo verrà impostato il livello di utilizzo al di sotto del quale la CPU viene considerata inattiva.  
  
    -   Specificare un numero di secondi nella casella **per almeno** . In questo modo verrà impostato l'intervallo relativo all'utilizzo minimo trascorso il quale la CPU viene considerata inattiva.  
  

