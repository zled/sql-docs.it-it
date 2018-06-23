---
title: Creare una categoria di processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d4ab1a7fdd56bf4586d3009c9c45bb29ecac0497
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067110"
---
# <a name="create-a-job-category"></a>Creare una categoria di processi
  In questo argomento si descrive come creare una categoria di processi in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent offre categorie di processi predefinite a cui possono essere assegnati processi. In alternativa, è possibile creare una nuova categoria e assegnarvi i processi. Le categorie consentono di organizzare i processi per semplificare le operazioni di raggruppamento e filtro. È ad esempio possibile organizzare tutti i processi di backup dei database raggruppandoli nella categoria Manutenzione database. È inoltre possibile creare categorie di processi personalizzate.  
  
 
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Le categorie multiserver sono disponibili solo in un server master. In un server master è disponibile una sola categoria di processi predefinita: [**Senza categoria (multiserver)**]. Quando viene scaricato un processo multiserver, la categoria viene modificata in **Processi dal server MSX** nel server di destinazione.  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  

  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>Per creare una categoria di processi  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera creare una categoria di processi.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Processi** e selezionare **Gestione categorie processi**.  
  
4.  Nella finestra di dialogo **Gestione categorie di processi***nome_server* fare clic su **Aggiungi**.  
  
5.  Nella casella **Nome** della nuova finestra di dialogo immettere un nome per la nuova categoria di processi.  
  
6.  Selezionare la casella di controllo **Mostra tutti i processi** . Selezionare uno o più processi per la nuova categoria selezionando le caselle corrispondenti ai processi.  
  
7.  Fare clic su **OK**.  
  
8.  Nella finestra di dialogo **Gestione categorie di processi***nome_server* fare clic su **Aggiorna** per assicurarsi che la nuova categoria di processi sia attiva. Se l'aspetto è quello previsto, chiudere questa finestra di dialogo.  
  
 Per ulteriori informazioni su queste finestre di dialogo, vedere [categorie di processi: Gestione categorie processi](job-categories-manage-job-categories.md) e [proprietà categorie di processi e nuova categoria di processi](job-categories-properties-new-job-category.md).  
  
 
  
##  <a name="TSQL"></a> Uso di Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>Per creare una categoria di processi  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_add_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).  
  

  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 **Per creare una categoria di processi**  
  
 Chiamare il `JobCategory` classe utilizzando un linguaggio di programmazione scelto, ad esempio Visual Basic, Visual c# o PowerShell. Per un esempio di codice, vedere [Pianificazione delle attività amministrative automatiche in SQL Server Agent](sql-server-agent.md).  
  
 
  
  
