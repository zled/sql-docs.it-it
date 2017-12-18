---
title: "Proprietà SQL Server Agent (pagina Generale) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 92df2d073ff15d955b3e8ee18c83f4b36065c2b2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-agent-properties-general-page"></a>Proprietà SQL Server Agent (pagina Generale)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Usare questa pagina per visualizzare e modificare le proprietà generali del servizio [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Stato del servizio**  
Visualizza lo stato corrente del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Riavvia automaticamente SQL Server in caso di arresto imprevisto**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent esegue il riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] quando si verifica un arresto imprevisto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Riavvia automaticamente SQL Server Agent in caso di arresto imprevisto**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] esegue il riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent quando si verifica un arresto imprevisto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Filename**  
Consente di specificare il nome del file per il log degli errori.  
  
**...**  
Consente di individuare i file di log degli errori.  
  
**Includi messaggi di traccia esecuzione**  
Consente di includere messaggi di traccia dell'esecuzione nel log degli errori. Nei messaggi di traccia sono incluse informazioni dettagliate sull'operazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Se questa opzione è selezionata, per il file di log sarà necessario ulteriore spazio su disco. È consigliabile selezionare questa opzione solo durante la risoluzione di un problema che potrebbe coinvolgere [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Scrivi file OEM**  
Consente di scrivere il file di log degli errori come file non Unicode. In questo modo, è possibile ridurre la quantità di spazio su disco utilizzata dal file di log. Quando questa opzione è selezionata, è tuttavia possibile che i messaggi contenenti dati Unicode siano più difficili da leggere.  
  
**Destinatario Net Send**  
Consente di digitare il nome dell'operatore destinato a ricevere la notifica Net Send dei messaggi scritti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent nel file di log.  
  
## <a name="see-also"></a>Vedere anche  
[Operatori](../../ssms/agent/operators.md)  
[Log degli errori di SQL Server Agent](../../ssms/agent/sql-server-agent-error-log.md)  
  
