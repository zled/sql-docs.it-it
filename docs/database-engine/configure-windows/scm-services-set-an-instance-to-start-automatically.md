---
title: Gestione configurazione SQL Server - Impostare un'istanza per l'avvio automatico | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 01/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 63598cfe81abc270430638d9d45a812ab2207815
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="scm-services---set-an-instance-to-start-automatically"></a>Gestione configurazione SQL Server - Impostare un'istanza per l'avvio automatico
  In questo argomento viene illustrato come impostare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'avvio automatico in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando Gestione configurazione SQL Server. Durante l'installazione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene normalmente configurato per l'avvio automatico. In caso contrario, è possibile modificare questa impostazione in qualsiasi momento.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di Gestione configurazione SQL Server  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a>Per impostare un'istanza di SQL Server per l'avvio automatico  
  
1.  Fare clic sul menu **Start** , scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Strumenti di configurazione**e quindi **Gestione configurazione SQL Server**.  
  
    > [!NOTE]  
    >  Poiché Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è uno snap-in per il programma [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console e non un programma autonomo, Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene visualizzato come applicazione nelle nuove versioni di Windows.  
    >   
    >  -   **Windows 10**:  
    >          per aprire Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , nella **pagina iniziale**digitare SQLServerManager13.msc (per [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Per le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sostituire 13 con un numero inferiore. Se si fa clic su SQLServerManager13.msc, viene aperto Gestione configurazione. Per aggiungere Gestione configurazione alla pagina iniziale o alla barra delle applicazioni, fare clic con il pulsante destro del mouse su SQLServerManager13.msc e quindi scegliere **Apri percorso file**. In Esplora file di Windows fare clic con il pulsante destro del mouse su SQLServerManager13.msc e quindi scegliere **Aggiungi a Start** o **Aggiungi alla barra delle applicazioni**.  
    > -   **Windows 8**:  
    >          Per aprire Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nell'accesso alla ricerca**** in **App** digitare **SQLServerManager\<versione>.msc**, ad esempio **SQLServerManager13.msc** e quindi premere **INVIO**.  
  
2.  In **Gestione configurazione SQL Server**espandere **Servizi**e quindi fare clic su **SQL Server**.  
  
3.  Nel riquadro dei dettagli fare clic con il pulsante destro del mouse sul nome dell'istanza per la quale impostare l'avvio automatico, quindi scegliere **Proprietà**.  
  
4.  Nella finestra di dialogo **SQL Server \<***nomeistanza***> Proprietà** impostare **Modalità di avvio** su **Automatica**.  
  
5.  Fare clic su **OK**e chiudere Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Impedire l'avvio automatico di un'istanza di SQL Server &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-prevent-automatic-startup-of-an-instance.md)   
 [Connettersi a un altro computer &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-connect-to-another-computer.md)   
 [Configurare WMI per mostrare lo stato del server in Strumenti SQL Server](http://msdn.microsoft.com/library/7e97197b-ed4d-40d1-9a52-9ab1d92401d7)  
  
  

