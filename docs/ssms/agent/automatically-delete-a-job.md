---
title: Eliminare automaticamente un processo | Microsoft Docs
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
- dropping jobs
- SQL Server Agent jobs, removing
- automatic job removal
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 92dbb6da-5919-4bde-9354-d454e9ea3da0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a8f3813b1a04cde1ce2d48d1859292f97519aabf
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="automatically-delete-a-job"></a>Automatically Delete a Job
In questo argomento viene illustrato come configurare [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] per eliminare automaticamente i processi quando hanno esito positivo, negativo o vengono completati tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o SQL Server Management Objects.  
  
Tramite le risposte ai processi gli amministratori del database vengono informati in merito al completamento e alla frequenza di esecuzione dei processi. Le risposte ai processi tipiche includono:  
  
-   Notifica all'operatore tramite posta elettronica, trasmissione di messaggi su cercapersone o messaggi **Net Send** .  
  
    Usare uno di questi metodi di risposta al processo se l'operatore dovrà eseguire operazioni basate sull'esito. Ad esempio, se un processo di backup viene completato, l'operatore dovrà ricevere una notifica per rimuovere il nastro di backup e riporlo in un luogo sicuro.  
  
-   Scrittura di un messaggio di evento nel registro delle applicazioni di Windows.  
  
    Questa risposta può essere usata esclusivamente per i processi non riusciti.  
  
-   Eliminazione automatica del processo.  
  
    Usare la risposta soltanto se si è certi che non sarà necessario rieseguire il processo.  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per specificare le risposte ai processi utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-automatically-delete-a-job"></a>Per eliminare automaticamente un processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**, espandere **Processi**, fare clic con il pulsante destro del mouse sul processo da modificare e quindi scegliere **Proprietà**.  
  
3.  Scegliere la pagina **Notifiche** .  
  
4.  Selezionare **Elimina il processo automaticamente**e quindi eseguire una delle operazioni seguenti:  
  
    -   Selezionare **In caso di esito positivo processo** per eliminare lo stato del processo quando questo viene completato con esito positivo.  
  
    -   Selezionare **In caso di esito negativo processo** per eliminare il processo quando questo viene completato con esito negativo.  
  
    -   Selezionare **Al termine del processo** per eliminare il processo indipendentemente dall'esito con cui viene completato.  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per eliminare automaticamente un processo**  
  
Usare la proprietà **DeleteLevel** della classe **Job** tramite un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  

