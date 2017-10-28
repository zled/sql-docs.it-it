---
title: Impostare un operatore alternativo | Microsoft Docs
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
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f5dd000cda03eaac79a198ba5103652db2bf892d
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="designate-a-fail-safe-operator"></a>Designate a Fail-Safe Operator
Un operatore alternativo è un utente che riceve l'avviso nel caso in cui l'operatore designato non sia raggiungibile. In questo argomento viene descritto come impostare un operatore alternativo per la ricezione di notifiche di avvisi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per impostare un operatore alternativo utilizzando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
  
-   Le opzioni Cercapersone e **net send** verranno rimosse da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in una versione futura di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Evitare pertanto di utilizzarle in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui sono state implementate.  
  
-   Si noti che per inviare notifiche tramite posta elettronica e cercapersone agli operatori, è necessario configurare SQL Server Agent per l'utilizzo di Posta elettronica database. Per ulteriori informazioni, vedere [Procedura: Assegnazione di avvisi a un operatore (SQL Server Management Studio)](http://msdn.microsoft.com/library/ms190038.aspx).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] è incluso un semplice strumento grafico per la gestione dei processi, che è lo strumento consigliato per la creazione e la gestione dell'infrastruttura dei processi.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Solo i membri del ruolo predefinito del server **sysadmin** possono definire operatori alternativi.  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-designate-a-fail-safe-operator"></a>Per impostare un operatore alternativo  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server che contiene l'operatore di SQL Server Agent che si vuole definire come alternativo.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent** e scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà di SQL Server Agent -***nome_server* fare clic su **Sistema avvisi**in **Selezione pagina**.  
  
4.  In **Operatore alternativo**selezionare **Abilita operatore alternativo**.  
  
5.  Nell'elenco **Operatore** selezionare l'operatore che si vuole rendere alternativo.  
  
6.  Selezionare tutte le caselle di controllo necessarie a specificare come l'operatore riceverà la notifica: **Posta elettronica**, **Cercapersone**o **Net Send**.  
  
7.  Al termine, fare clic su **OK**.  
  

