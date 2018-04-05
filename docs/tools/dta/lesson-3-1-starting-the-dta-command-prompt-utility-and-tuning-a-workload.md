---
title: Avvio dell'utilità del prompt dei comandi dta e ottimizzazione di un carico di lavoro | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- Database Engine [SQL Server], tutorials
ms.assetid: f34a5acf-1f3b-4484-a770-6470cb925ab0
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b4adf756444c22146108fead4f607c20c6108dc3
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-3-1---starting-the-dta-command-prompt-utility-and-tuning-a-workload"></a>Lezione 3-1-avvio dell'utilità del prompt dei comandi dta e ottimizzazione di un carico di lavoro
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Questa attività consente di avviare il **dta** utilità, visualizzarne la Guida e quindi utilizzarlo per ottimizzare un carico di lavoro dal prompt dei comandi. Viene usato il carico di lavoro MyScript.sql creato per l'esercitazione sull'interfaccia utente grafica di Ottimizzazione guidata motore di database [Ottimizzazione di un carico di lavoro](../../tools/dta/lesson-1-1-tuning-a-workload.md).  
  
In questa esercitazione viene utilizzato il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Per motivi di sicurezza, i database di esempio non vengono installati per impostazione predefinita. Per installare i database di esempio, vedere [Installazione degli esempi e dei database di esempio di SQL Server](http://sqlserversamples.codeplex.com).  
  
Le attività seguenti consentono di aprire un prompt dei comandi, avviare l'utilità della riga di comando **dta** , visualizzare la Guida relativa alla sintassi e ottimizzare un carico di lavoro semplice, ovvero MyScript.sql, creato in [Ottimizzazione di un carico di lavoro](../../tools/dta/lesson-1-1-tuning-a-workload.md).  
  
### <a name="to-start-the-dta-command-prompt-utility-and-view-help"></a>Per avviare l'utilità del prompt dei comandi dta e visualizzare la Guida  
  
1.  Fare clic sul pulsante **Start** , scegliere **Tutti i programmi**, **Accessori**e quindi **Prompt dei comandi**.  
  
2.  Al prompt dei comandi digitare quanto segue e premere INVIO:  
  
    ```  
    dta -? | more  
    ```  
  
    La sezione `| more` di questo comando è facoltativa. Tuttavia utilizzandola è possibile scorrere le pagine della Guida dell'utilità relative alla sintassi. Premere INVIO per visualizzare il testo della Guida riga per riga oppure premere la BARRA SPAZIATRICE per scorrere le pagine.  
  
### <a name="to-tune-a-simple-workload-by-using-the-dta-command-prompt-utility"></a>Per ottimizzare un carico di lavoro semplice utilizzando l'utilità del prompt dei comandi dta  
  
1.  Al prompt dei comandi, passare alla directory contenente il file MyScript.sql.  
  
2.  Al prompt dei comandi, digitare quanto segue e premere INVIO per eseguire il comando e avviare la sessione di ottimizzazione (si noti che l'utilità distingue tra maiuscole e minuscole quando viene eseguita l'analisi dei comandi):  
  
    ```  
    dta -S YourServerName\YourSQLServerInstanceName -E -D AdventureWorks2012 -if MyScript.sql -s MySession2 -of MySession2OutputScript.sql -ox MySession2Output.xml -fa IDX_IV -fp NONE -fk NONE  
    ```  
  
    dove `-S` indica il nome del server e l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui è installato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . L'impostazione `-E` indica l'utilizzo di una connessione trusted all'istanza che risulta appropriata nel caso di una connessione con un account di dominio di Windows. L'impostazione `-D` specifica il database da ottimizzare, `-if` il file del carico di lavoro, `-s` il nome della sessione, `-of` il file sul quale verrà creato lo script delle indicazioni [!INCLUDE[tsql](../../includes/tsql-md.md)] e `-ox` il file sul quale verranno scritte le indicazioni in formato XML. Gli ultimi tre parametri definiscono le opzioni di ottimizzazione nel modo seguente: `-fa IDX_IV` indica che in Ottimizzazione guidata motore di database devono essere aggiunti solo gli indici (cluster e non cluster) e le viste indicizzate; `-fp NONE` indica che durante l'analisi non devono essere considerate le strategie di partizionamento e `-fk NONE` indica che quando vengono generate le indicazioni in Ottimizzazione guidata motore di database non devono essere mantenute nel database le strutture di progettazione fisica esistenti.  
  
3.  Al termine dell'ottimizzazione del carico di lavoro, in Ottimizzazione guidata motore di database viene visualizzato un messaggio che indica che la sessione di ottimizzazione è stata completata correttamente. È possibile visualizzare i risultati dell'ottimizzazione utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per aprire i file MySession2OutputScript.sql e MySession2Output.xml. In alternativa è possibile aprire la sessione di ottimizzazione MySession2 nell'interfaccia utente grafica di Ottimizzazione guidata motore di database e visualizzare le indicazioni e i report come descritto in [Visualizzazione delle indicazioni di ottimizzazione](../../tools/dta/lesson-1-2-viewing-tuning-recommendations.md) e [Visualizzazione dei report di ottimizzazione](../../tools/dta/lesson-1-3-viewing-tuning-reports.md).  
  
## <a name="summary"></a>Riepilogo  
In questo modo è stata completata l'ottimizzazione di un carico di lavoro semplice dal prompt dei comandi tramite l'utilità **dta** . Questo strumento offre numerose altre opzioni di ottimizzazione. Per altre informazioni, consultare la Guida (**dta -?**) e l'argomento [Utilità dta](../../tools/dta/dta-utility.md) .  
  
## <a name="after-you-finish-this-tutorial"></a>Al termine di questa esercitazione  
Al termine di questa esercitazione, per ulteriori informazioni sullo strumento Ottimizzazione guidata motore di database, è possibile consultare gli argomenti seguenti:  
  
-   [Ottimizzazione guidata motore di database](../../relational-databases/performance/database-engine-tuning-advisor.md) per le descrizioni sull'uso di questo strumento in determinate attività.  
  
-   [Utilità dta](../../tools/dta/dta-utility.md) per materiale di riferimento sull'utilità del prompt dei comandi e sul file XML facoltativo disponibile per usare l'utilità.  
  
Per tornare all'inizio dell'esercitazione, vedere [Esercitazione: Strumento Ottimizzazione guidata motore di database](../../tools/dta/tutorial-database-engine-tuning-advisor.md).  
  
## <a name="see-also"></a>Vedere anche  
[Esercitazioni del motore di database](../../relational-databases/database-engine-tutorials.md)  
  
  
  
