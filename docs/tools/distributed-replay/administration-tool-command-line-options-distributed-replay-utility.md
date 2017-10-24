---
title: Opzioni della riga di comando (Distributed Replay Utility) dello strumento di amministrazione | Documenti Microsoft
ms.custom: 
ms.date: 08/12/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 652600de9d777f13332509fcaae3985daf9c26fc
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>Opzioni della riga di comando dello strumento di amministrazione (Distributed Replay Utility)
  Lo strumento di amministrazione Riesecuzione distribuita di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , **DReplay.exe**, è uno strumento da riga di comando per comunicare con il controller di Riesecuzione distribuita. Usare lo strumento di amministrazione per avviare, monitorare e annullare operazioni nel controller.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") per ulteriori informazioni sulle convenzioni di sintassi utilizzate con la sintassi dello strumento di amministrazione, vedere [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## <a name="remarks"></a>Osservazioni  
 Con **DReplay.exe**è possibile eseguire le seguenti opzioni della riga di comando:  
  
 **preprocess**  
 Avvia la fase di pre-elaborazione. Il controller prepara i dati di traccia di input, acquisiti dall'ambiente di produzione, per la riproduzione sul server di destinazione.  
  
 **replay**  
 Avvia la fase di riproduzione dell'evento. Il controller recapita i dati di riproduzione ai client specificati, avvia la riproduzione distribuita e sincronizza i client. Ogni client selezionato può eventualmente registrare l'attività di riproduzione e salvare in locale i file di traccia dei risultati.  
  
 **status**  
 Viene eseguita una query sul controller e viene visualizzato lo stato corrente.  
  
 **cancel**  
 Viene annullata l'operazione corrente eseguita nel controller.  
  
 Per informazioni dettagliate sulla sintassi, inclusi gli argomenti dei comandi e gli esempi, vedere gli argomenti seguenti:  
  
-   [Pre-elaborazione opzione &#40; strumento di amministrazione Distributed Replay &#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Opzione Replay &#40; strumento di amministrazione Distributed Replay &#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [Opzione Status &#40; strumento di amministrazione Distributed Replay &#41;](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [Opzione Cancel &#40; strumento di amministrazione Distributed Replay &#41;](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 Le chiamate RPC vengono riprodotte come RPC e non come eventi di linguaggio.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessario eseguire lo strumento di amministrazione come utente interattivo, scegliendo tra utente locale e account utente di dominio. Per utilizzare un account utente locale, lo strumento di amministrazione e il controller devono essere eseguiti nello stesso computer.  
  
 Per altre informazioni, vedere [Sicurezza di Riesecuzione distribuita](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  

