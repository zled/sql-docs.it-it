---
title: Definire le opzioni del passaggio di processo Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4b014c06b4a19d6c710ab7fb60c90dcfbe5bf130
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301687"
---
# <a name="define-transact-sql-job-step-options"></a>Define Transact-SQL Job Step Options
  In questo argomento viene descritto come definire le opzioni per i passaggi del processo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  [!INCLUDE[tsql](../../includes/tsql-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o SQL Server Management Objects.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per definire le opzioni del passaggio di processo Transact-SQL con** ,  
  
     [SQL Server Management Studio](#SSMS)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-define-transact-sql-job-step-options"></a>Per definire le opzioni del passaggio di processo Transact-SQL  
  
1.  In **Esplora oggetti**espandere **SQL Server Agent**e **Processi**, fare clic con il pulsante destro del mouse sul processo da modificare e quindi selezionare **Proprietà**.  
  
2.  Selezionare la pagina **Passaggi** , fare clic su un passaggio processo e quindi su **Modifica**.  
  
3.  Nella finestra di dialogo **Proprietà passaggio processo** verificare che il tipo di processo è **Transact-SQL Script (TSQL)** e quindi selezionare la pagina **Avanzate** .  
  
4.  Specificare un'operazione da eseguire se il processo ha esito positivo dall'elenco **Azione in caso di esito positivo** .  
  
5.  Specificare un numero di tentativi digitando un numero compreso tra 0 e 9999 nella casella **Numero tentativi** .  
  
6.  Specificare un intervallo di tentativi digitando un numero di minuti compreso tra 0 e 9999 nella casella **Intervallo tentativi** .  
  
7.  Specificare un'operazione da eseguire se il processo ha esito negativo dall'elenco **Azione in caso di esito negativo** .  
  
8.  Se il processo è uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] , è possibile scegliere una delle opzioni seguenti:  
  
    -   Immettere il nome di un **File di output**. Per impostazione predefinita il file viene sovrascritto a ogni esecuzione del passaggio processo. Per evitarlo, selezionare **Accoda output a file esistente**. L'opzione è disponibile solo ai membri del ruolo predefinito del server **sysadmin** . Si noti che [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] non consente agli utenti di visualizzare file arbitrari nel file system, quindi non è possibile utilizzare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per visualizzare i log dei passaggi scritti nel file system.  
  
    -   Selezionare **Registra nella tabella** per registrare il passaggio processo in una tabella di database. Per impostazione predefinita il contenuto della tabella viene sovrascritto a ogni esecuzione del passaggio processo. Per evitarlo, selezionare **Accoda output a voce esistente nella tabella**. Dopo l'esecuzione del passaggio processo, è possibile visualizzare il contenuto della tabella facendo clic su **Visualizza**.  
  
    -   Selezionare **Includi output passaggio nella cronologia** se si desidera includere l'output nella cronologia dei passaggi. L'output verrà visualizzato solo se non si sono verificati errori. È inoltre possibile che l'output sia troncato.  
  
9. Se l'utente è membro del ruolo predefinito del server **sysadmin** e intende eseguire questo passaggio di processo con un diverso account di accesso SQL, selezionare l'account di accesso SQL dall'elenco **Esegui come utente** .  
  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 **Per definire le opzioni del passaggio di processo Transact-SQL**  
  
 Usare il `JobStep` classe utilizzando un linguaggio di programmazione desiderato, ad esempio Visual Basic, Visual c# o PowerShell.  
  
  
