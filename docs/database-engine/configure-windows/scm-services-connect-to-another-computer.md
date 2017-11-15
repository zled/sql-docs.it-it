---
title: Connettersi a un altro computer (Gestione configurazione SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 35642ebdc9f5d7c59eee5b34993d6def70b4e048
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="scm-services---connect-to-another-computer"></a>Connettersi a un altro computer (Gestione configurazione SQL Server)
  In questo argomento viene illustrato come connettersi a un altro computer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Attenersi alla prima procedura per aprire Gestione computer di Windows, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC), connettersi al computer ed espandere l'albero Servizi e applicazioni. Seguire la seconda procedura per creare un file con un collegamento a Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un computer remoto.  
  
> [!NOTE]  
>  Alcune azioni non possono essere eseguite da Configuration Manager quando si effettua la connessione in remoto.  
  
 Per avviare, arrestare, sospendere o riprendere i servizi in un altro computer, è inoltre possibile connettersi al server tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], fare clic con il pulsante destro del mouse sul server o su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e quindi scegliere l'operazione desiderata.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-connect-to-another-computer-with-windows-computer-management"></a>Per connettersi a un altro computer utilizzando Gestione computer di Windows  
  
1.  Nel menu **Start** fare clic con il pulsante destro del mouse su **Risorse del computer**e quindi scegliere **Gestione**.  
  
2.  In **Gestione computer**fare clic con il pulsante destro del mouse su **Gestione computer (locale)**e quindi scegliere **Connetti a un altro computer**.  
  
3.  Nella finestra di dialogo **Seleziona computer** digitare il nome del computer che si vuole gestire nella casella di testo **Altro computer** quindi fare clic su **OK**.  
  
     Gestione computer visualizza i servizi in esecuzione nel computer remoto. Il nodo di primo livello diventa **Gestione computer**\<*computerremoto*>.  
  
4.  Nell'albero della console espandere **Servizi e applicazioni**e quindi espandere **Gestione configurazione SQL Server** per gestire i servizi del computer remoto.  
  
#### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a>Per salvare un collegamento a Gestione configurazione SQL Server da un altro computer  
  
1.  Fare clic sul menu **Start** e scegliere **Esegui**.  
  
2.  Nella casella **Apri** digitare **mmc -a** per aprire [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console in modalità di modifica.  
  
3.  Scegliere **Aggiungi/Rimuovi snap-in** dal menu **File**.  
  
4.  Nella finestra **Aggiungi/Rimuovi snap-in** fare clic su **Aggiungi**.  
  
5.  Nella finestra **Aggiungi snap-in autonomo** fare clic su **Gestione computer** e quindi su **Aggiungi**.  
  
6.  Nella finestra **Gestione computer** fare clic su **Altro computer**, digitare il nome del computer remoto da gestire e quindi fare clic su **Fine**.  
  
7.  Nella finestra **Aggiungi snap-in autonomo** fare clic su **Chiudi**.  
  
8.  Nella finestra **Aggiungi/Rimuovi snap-in** fare clic su **OK**.  
  
9. Espandere **Gestione computer (***\<nome computer>***)** e **Servizi e applicazioni**.  
  
10. Fare clic con il pulsante destro del mouse su **Gestione configurazione SQL Server**e quindi scegliere **Nuova finestra da qui**.  
  
11. Scegliere **Radice console** dal menu **Finestra**per tornare alla prima finestra ed eliminare la finestra aperta.  
  
12. Scegliere **Salva con nome** dal menu **File**e salvare il file nella cartella desiderata con un nome appropriato e l'estensione di file **msc** . Chiudere [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.  
  
13. Per aprire Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer di destinazione, fare doppio clic sul file. È possibile salvare un collegamento al file sul desktop o nel menu **Start** .  
  
> [!CAUTION]  
>  Quando si utilizza Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un computer remoto, il nome del computer non è facilmente individuabile ed è possibile che venga arrestato o configurato il computer errato. Nella scheda **Servizio** selezionare la casella **Nome host** per verificare il nome del computer prima di modificare un servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di WMI per mostrare lo stato del server in Strumenti SQL Server](http://msdn.microsoft.com/library/7e97197b-ed4d-40d1-9a52-9ab1d92401d7)  
  
  
