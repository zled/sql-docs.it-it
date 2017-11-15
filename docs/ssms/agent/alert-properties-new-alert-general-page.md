---
title: "Proprietà avviso - Nuovo avviso (pagina Generale) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30a648ec7ee810656007bd1371236e2687338a7f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="alert-properties---new-alert-general-page"></a>Proprietà avviso - Nuovo avviso (pagina Generale)
Usare questa pagina per visualizzare e modificare le proprietà generali degli avvisi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Nome**  
Consente di modificare il nome dell'avviso.  
  
**Abilita**  
Consente di abilitare l'avviso. Se l'avviso non è abilitato, le azioni specificate nell'avviso non verranno eseguite.  
  
**Tipo**  
Consente di selezionare il tipo di avviso:  
  
-   **Avviso per evento di SQL Server** risponde ai messaggi nel registro degli eventi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows.  
  
-   **Avviso relativo alle prestazioni di SQL Server** risponde a una specifica condizione in un contatore delle prestazioni.  
  
-   **Avviso per evento WMI** risponde a un evento del servizio Strumentazione gestione Windows (WMI, Windows Management Instrumentation).  
  
## <a name="sql-server-event-alert-options"></a>Opzioni di Avviso per evento di SQL Server  
**Nome database**  
Consente di specificare un database per l'evento o **tutti i database** per rispondere a un messaggio indipendentemente dal database in cui si verifica l'evento.  
  
**Numero di errore**  
Consente di specificare che l'evento risponde a un errore e di indicare il numero dell'errore.  
  
**Severity**  
Consente di specificare che l'evento risponde a tutti messaggi con uno specifico livello di gravità e di indicare tale livello.  
  
**Genera avviso quando il messaggio contiene**  
Consente di applicare un filtro agli eventi in base a una stringa specifica. Se questa opzione è selezionata, l'avviso risponde solo agli eventi contenenti la stringa specificata.  
  
**Testo del messaggio**  
Consente di specificare la stringa da utilizzare come filtro per gli eventi.  
  
## <a name="sql-server-performance-condition-alerts"></a>Opzioni di Avviso relativo alle prestazioni di SQL Server  
**Oggetto**  
Consente di specificare l'oggetto prestazioni da monitorare.  
  
**Contatore**  
Consente di specificare il contatore all'interno dell'oggetto prestazioni da monitorare.  
  
**Istanza**  
Consente di specificare l'istanza del contatore da monitorare.  
  
**Avvisa se il contatore**  
Consente di specificare il comportamento del contatore a cui risponde l'evento. È ad esempio possibile impostare questa opzione in modo che l'avviso risponda a una condizione in cui il valore del contatore **Spazio disponibile in tempdb (KB)** scende al di sotto di un determinata soglia o il valore di **Compilazioni SQL/sec** supera un determinato livello.  
  
**Valore**  
Consente di specificare un valore per il contatore.  
  
## <a name="wmi-event-alert-options"></a>Opzioni di Avviso per evento WMI  
**Spazio dei nomi**  
Consente di specificare lo spazio dei nomi da utilizzare per l'istruzione WQL (WMI Query Language). Sono supportati solo gli spazi dei nomi sul computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Query**  
Consente di specificare l'istruzione WQL che identifica l'evento al quale risponde l'avviso.  
  
## <a name="see-also"></a>Vedere anche  
[Avvisi](../../ssms/agent/alerts.md)  
[Utilizzo di WQL con il provider WMI per eventi del server](http://msdn.microsoft.com/en-us/58b67426-1e66-4445-8e2c-03182e94c4be)  
[Creazione di un avviso utilizzando un numero di errore](../../ssms/agent/create-an-alert-using-an-error-number.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
