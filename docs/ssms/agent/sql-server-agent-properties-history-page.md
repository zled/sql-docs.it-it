---
title: "Proprietà SQL Server Agent (pagina Cronologia) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 51839ab3d459e2350c582810fe003fc5086de3eb
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-agent-properties-history-page"></a>Proprietà SQL Server Agent (pagina Cronologia)
Usare questa pagina per visualizzare e modificare le impostazioni di gestione del log della cronologia del servizio di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Limita dimensioni log cronologia processo**  
Consente di impostare limiti sulla quantità di informazioni sulla cronologia processo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent mantiene nel log.  
  
**Dimensioni massime log cronologia processo (righe)**  
Consente di impostare il numero massimo di righe che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent mantiene nel log. Quando il log raggiunge dimensioni tali da contenere questo numero di righe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent rimuove le righe meno recenti per consentire l'inserimento delle nuove.  
  
**Numero massimo di righe di cronologia per processo**  
Consente di impostare il numero massimo di righe che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent mantiene per ogni processo. Quando la cronologia di un determinato processo si estende fino a contenere questo numero di righe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent consente di rimuovere le righe meno recenti per consentire l'inserimento delle nuove.  
  
**Rimuovi cronologia dell'agente**  
Viene indicato che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent consentirà di rimuovere le voci presenti nel log da più tempo rispetto a quanto specificato. Si tratta di un'esecuzione singola che consente di rimuovere la cronologia. Se è necessario un processo ricorrente, creare e pianificare un piano di manutenzione con un processo di pulizia.  
  
**Più vecchia di**  
Consente di impostare il periodo di tempo per cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent manterrà le voci.  
  
## <a name="see-also"></a>Vedere anche  
[Log degli errori di SQL Server Agent](../../ssms/agent/sql-server-agent-error-log.md)  
  

