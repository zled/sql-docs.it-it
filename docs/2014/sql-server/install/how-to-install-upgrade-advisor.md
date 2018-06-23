---
title: 'Procedura: installare Upgrade Advisor | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b98a4b134025d22ad9d13ce9fa38a7e4f2605e0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169143"
---
# <a name="how-to-install-upgrade-advisor"></a>Procedura: Installazione di Preparazione aggiornamento
  Preparazione aggiornamento supporta l'analisi remota di tutti i componenti supportati, ad eccezione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Se non si prevede di analizzare le istanze di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è possibile installare Preparazione aggiornamento in qualsiasi computer in grado di connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e che soddisfi i prerequisiti di Preparazione aggiornamento. Se si prevede di analizzare le istanze di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è necessario installare Preparazione aggiornamento nel server di report.  
  
 Per altre informazioni, vedere [installazione di Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
### <a name="to-install-upgrade-advisor"></a>Per installare Preparazione aggiornamento  
  
1.  Avviare l'installazione utilizzando uno dei metodi seguenti:  
  
    -   Se si sta installando dal [!INCLUDE[msCoName](../../includes/msconame-md.md)] sito Web, fare clic sul **scaricare** collegamento e scegliere il **eseguire** pulsante per avviare l'installazione.  
  
    -   Se si installa da supporto del prodotto, aprire il **redist** cartella, aprire il **Upgrade Advisor** cartella e quindi fare doppio clic **sqlua. msi**.  
  
    > [!NOTE]  
    >  Preparazione aggiornamento richiede [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4. Se non è installato, o se si dispone di una versione non definitiva, verrà visualizzato un messaggio di errore. Disinstallare qualsiasi versione precedente di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], quindi installare la versione più recente di .NET Framework 4.  
    >   
    >  Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom è un prerequisito per l'installazione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Preparazione aggiornamento e non viene installato dall'installazione di preparazione aggiornamento. Il programma di installazione è necessario scaricare e installare il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom dal [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.  
  
2.  Nel **iniziale per il [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installazione di preparazione aggiornamento** fare clic su **Avanti**.  
  
3.  Nel **contratto di licenza** pagina, leggere il contratto di licenza. Se si accettano, selezionare **accetto il contratto di licenza** e quindi fare clic su **successivo**.  
  
4.  Nel **le informazioni di registrazione** pagina, immettere il nome e la società.  
  
5.  Nel **Selezione funzionalità** pagina, esaminare i **percorso di installazione** valore. Se necessario, utilizzare il **Sfoglia** pulsante per modificare il percorso. Scegliere **Avanti**.  
  
6.  Nel **pronto per l'installazione del programma** fare clic su **installare** per installare Preparazione aggiornamento.  
  
7.  Scegliere **Fine** per uscire dalla procedura guidata.  
  
## <a name="see-also"></a>Vedere anche  
 [Prerequisiti di preparazione aggiornamento](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  