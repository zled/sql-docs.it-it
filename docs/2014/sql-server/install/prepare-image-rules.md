---
title: Regole di preparazione immagine | Documenti Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 609a7c06-9527-4ef5-8e75-0c44e1958c5a
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd8fa80133722d895ca851ba9554951f9437697e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069750"
---
# <a name="prepare-image-rules"></a>Regole di preparazione immagine
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Programma di installazione convalida la configurazione del computer prima di concludere l'installazione. Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguita l'analisi del computer in cui verrà installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite Controllo configurazione sistema. Questo strumento consente di verificare le condizioni che impediscono la corretta operazione di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Prima dell'avvio dell'installazione guidata, lo strumento recupera le informazioni sullo stato di ciascun elemento. Il risultato viene confrontato con i requisiti, quindi vengono fornite indicazioni per la rimozione di eventuali problemi che impediscono di proseguire.  
  
 Con il controllo della configurazione di sistema viene generato un report con una breve descrizione di ogni regola eseguita, nonché lo stato dell'esecuzione. Il report controllo configurazione sistema si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
 Prima di eseguire l'operazione di installazione, esaminare i seguenti argomenti:  
  
1.  [Requisiti hardware e Software per l'installazione di SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Funzionalità supportate dalle edizioni di SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Versioni in lingua locale di SQL Server](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Altri riferimenti:  
  
1.  [Aggiornamenti di versione ed edizione supportati](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Operazioni preliminari all'installazione del clustering di failover](../failover-clusters/install/before-installing-failover-clustering.md)  
  
  