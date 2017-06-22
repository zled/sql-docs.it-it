---
title: SQL Server PowerShell | Microsoft Docs
ms.custom: 
ms.date: 08/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89b70725-bbe7-4ffe-a27d-2a40005a97e7
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c7181877fcc1fa7553b5e11508bc1c9425166ccd
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-powershell"></a>SQL Server PowerShell
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supporta Windows PowerShell, ovvero una potente shell di scripting che consente agli amministratori e agli sviluppatori di automatizzare l'amministrazione del server e la distribuzione delle applicazioni. Il linguaggio di Windows PowerShell supporta una logica più complessa rispetto agli script [!INCLUDE[tsql](../../includes/tsql-md.md)] , consentendo agli amministratori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di compilare script di amministrazione affidabili. Gli script di Windows PowerShell possono anche essere utilizzati per amministrare altri prodotti server di [!INCLUDE[msCoName](../../includes/msconame-md.md)] , Ciò fornisce agli amministratori un linguaggio di scripting comune in tutti i server.  
  
## <a name="sql-server-powershell-components"></a>Componenti di PowerShell di SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre fornisce un modulo di Windows PowerShell denominato **sqlps** che viene usato per importare i componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un ambiente o script di Windows PowerShell. Il modulo **sqlps** carica due snap-in di Windows PowerShell che implementano:  
  
-   Un provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , che abilita un semplice meccanismo di navigazione simile ai percorsi del file system. È possibile compilare percorsi simili a quelli del file system, in cui l'unità è associata a un modello a oggetti di gestione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i nodi sono basati sulle classi del modello a oggetti. È quindi possibile usare comandi comuni come **cd** e **dir** per un'esplorazione dei percorsi simile all'esplorazione delle cartelle in una finestra del prompt dei comandi. È possibile usare altri comandi, ad esempio **ren** o **del**, per eseguire azioni sui nodi nel percorso.  
  
-   Un set di cmdlet, ovvero di comandi utilizzati negli script di Windows PowerShell per specificare un'azione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . I cmdlet di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supportano azioni come l'esecuzione di uno script **sqlcmd** che contiene istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] o XQuery.  
  
 Per informazioni su Windows PowerShell, vedere la [Guida introduttiva a Windows PowerShell](https://msdn.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell).  
  
## <a name="sql-server-versions"></a>Versioni di SQL Server  
 I componenti di PowerShell [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] possono essere utilizzati per gestire istanze di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] o versione successiva. Le istanze di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] devono eseguire la versione SP2 o successiva. Le istanze di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] devono eseguire la versione SP4 o successiva. Quando i componenti di PowerShell per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vengono utilizzati con versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sono limitati alla funzionalità disponibile in tali versioni.  
     
## <a name="sql-server-powershell-tasks"></a>Attività di SQL Server PowerShell  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------| 
|Installazione delle estensioni Microsoft® Windows PowerShell per Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  I moduli di PowerShell vengono installati per impostazione predefinita quando si installa [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  È possibile installare manualmente le estensioni PowerShell per SQL Server 2016 installando i componenti seguenti dal Feature Pack di Microsoft® SQL Server® 2016:<br/>     Microsoft® System CLR Types per Microsoft SQL Server® 2016 (SQLSysClrTypes.msi)<br/>Oggetti di gestione condivisa di Microsoft® SQL Server® 2016 (SharedManagementObjects.msi)<br/> Estensioni Microsoft® Windows PowerShell per Microsoft SQL Server® 2016 (PowerShellTools.msi)|[Microsoft® SQL Server® 2016 Feature Pack](https://www.microsoft.com/en-us/download/details.aspx?id=52676).   | 
|Descrive il meccanismo preferito per l'esecuzione dei componenti PowerShell per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; aprire una sessione di PowerShell e caricare il modulo **sqlps** . Il modulo di **sqlps** viene caricato nel provider e nei cmdlet di PowerShell di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i gruppi SQL Server Management Object (SMO) vengono usati dal provider e dai cmdlets.|[Importare il modulo SQLPS](../../relational-databases/scripting/import-the-sqlps-module.md)|  
|Descrive come caricare solo i gruppi SMO senza il provider o i cmdlet.|[Caricare gli assembly SMO in Windows PowerShell](../../relational-databases/scripting/load-the-smo-assemblies-in-windows-powershell.md)|  
|Descrive la modalità di esecuzione della sessione di Windows PowerShell facendo clic con il pulsante destro del mouse su un nodo in **Esplora oggetti**. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] avvia una sessione di Windows PowerShell, carica il modulo **sqlps** e imposta il percorso del provider SQL Server sull'oggetto selezionato.|[Esecuzione di Windows PowerShell da SQL Server Management Studio](../../relational-databases/scripting/run-windows-powershell-from-sql-server-management-studio.md)|  
|Descrive come creare passaggi di processo SQL Server Agent che eseguano uno script di Windows PowerShell. I processi possono quindi essere programmati per l'esecuzione a ore specifiche o al verificarsi di eventi.|[Esecuzione di passaggi di Windows PowerShell in SQL Server Agent](../../relational-databases/scripting/run-windows-powershell-steps-in-sql-server-agent.md)|  
|Descrive la modalità di utilizzo del provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per spostarsi nella gerarchia degli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)|  
|Descrive come utilizzare i cmdlet di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che specificano le azioni [!INCLUDE[ssDE](../../includes/ssde-md.md)] come ad esempio l'esecuzione di uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] .|[Utilizzo di cmdlet del motore di database](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)|  
|Descrive come specificare identificatori delimitati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che contengono caratteri non supportati da Windows PowerShell.|[Identificatori di SQL Server in PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)|  
|Descrive come effettuare connessioni di autenticazione di SQL Server. Per impostazione predefinita, i componenti PowerShell di SQL Server utilizzano connessioni di autenticazione di Windows mediante le credenziali di Windows del processo che esegue Windows PowerShell.|[Gestire l'autenticazione in motore di database PowerShell](../../relational-databases/scripting/manage-authentication-in-database-engine-powershell.md)|  
|Descrive come utilizzare variabili implementate dal provider PowerShell di SQL Server per controllare quanti oggetti vengono elencati oggetti nel caso di utilizzo del completamento della scheda di Windows PowerShell. Questo è particolarmente utile lavorando su database che contengono grandi numeri di oggetti.|[Gestire il completamento alla pressione del tasto TAB &#40;SQL Server PowerShell&#41;](../../relational-databases/scripting/manage-tab-completion-sql-server-powershell.md)|  
|Descrive come utilizzare Get-Help per ottenere informazioni sui componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nell'ambiente di Windows PowerShell.|[Visualizzazione della Guida di SQL Server PowerShell](../../relational-databases/scripting/get-help-sql-server-powershell.md)|  
  
  

