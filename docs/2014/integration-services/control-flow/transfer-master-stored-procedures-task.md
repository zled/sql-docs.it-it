---
title: Attività Trasferisci stored procedure master | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfermasterspstask.f1
helpviewer_keywords:
- Transfer Master Stored Procedures task [Integration Services]
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b89788698662245d69cb8b209286e1e5dd2f93a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235321"
---
# <a name="transfer-master-stored-procedures-task"></a>Attività Trasferisci stored procedure master
  L'attività Trasferisci stored procedure master trasferisce una o più stored procedure definite dall'utente tra i database **master** di istanze diverse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per trasferire una stored procedure dal database **master** , è necessario che il proprietario stored della procedure sia un dbo.  
  
 È possibile configurare l'attività Trasferisci stored procedure master per il trasferimento di tutte le stored procedure o delle stored procedure specificate. Questa attività non esegue la copia delle stored procedure di sistema.  
  
 È possibile che le stored procedure master da trasferire siano già presenti nella destinazione. È tuttavia possibile configurare l'attività Trasferisci stored procedure master per la gestione di eventuali stored procedure esistenti nei modi seguenti:  
  
-   Le stored procedure esistenti vengono sovrascritte.  
  
-   In presenza di stored procedure duplicate l'attività ha esito positivo.  
  
-   Le stored procedure duplicate vengono ignorate.  
  
 In fase di esecuzione l'attività Trasferisci stored procedure master si connette al server di origine e al server di destinazione utilizzando due gestioni connessioni SMO. Le gestioni connessioni SMO vengono configurate separatamente dall'attività Trasferisci stored procedure master, che tuttavia vi fa riferimento. Le gestioni connessioni SMO specificano il server e la modalità di autenticazione da utilizzare per l'accesso al server. Per altre informazioni, vedere [Gestione connessione SMO](../connection-manager/smo-connection-manager.md).  
  
## <a name="transferring-stored-procedures-between-instances-of-sql-server"></a>Trasferimento di stored procedure tra istanze di SQL Server  
 L'attività Trasferisci stored procedure master supporta un'origine e una destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="events"></a>Eventi  
 L'attività genera un evento informativo in cui è indicato il numero di stored procedure trasferite. Genera inoltre un evento di avviso quando una stored procedure viene sovrascritta.  
  
 Non viene riportato lo stato incrementale del trasferimento, ma solo il completamento 0% e 100%.  
  
## <a name="execution-value"></a>Valore di esecuzione  
 Il valore di esecuzione, definito nel `ExecutionValue` proprietà dell'attività, restituisce il numero di stored procedure trasferite. Tramite l'assegnazione di una variabile definita dall'utente per il `ExecValueVariable` proprietà dell'attività Trasferisci Stored procedure Master, informazioni sul trasferimento di stored procedure possono essere rese disponibili ad altri oggetti nel pacchetto. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) e [Utilizzo di variabili nei pacchetti](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Voci di log  
 L'attività Trasferisci stored procedure master include le voci di log personalizzate seguenti:  
  
-   TransferStoredProceduresTaskStartTransferringObjects  Indica che il trasferimento è iniziato. La voce di log include l'ora di inizio.  
  
-   TransferSStoredProceduresTaskFinishedTransferringObjects  Indica che il trasferimento è stato completato. La voce di log include l'ora di fine.  
  
 Inoltre, una voce di log per il `OnInformation` indica il numero di stored procedure che sono state trasferite e una voce di log per il `OnWarning` viene scritto l'evento per ogni stored procedure nella destinazione viene sovrascritto.  
  
## <a name="security-and-permissions"></a>Sicurezza e autorizzazioni  
 L'utente deve disporre dell'autorizzazione per la visualizzazione dell'elenco di stored procedure nel database **master** dell'origine ed essere un membro del ruolo del server amministratore di sistema o disporre dell'autorizzazione per la creazione di stored procedure nel database **master** del server di destinazione.  
  
## <a name="configuration-of-the-transfer-master-stored-procedures-task"></a>Configurazione dell'attività Trasferisci stored procedure master  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Le Stored procedure Editor attività Trasferisci Master &#40;pagina Generale&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Le Stored procedure Editor attività Trasferisci Master &#40;Stored procedure&#41&#41;](../transfer-master-stored-procedures-task-editor-stored-procedures-page.md)  
  
-   [Pagina Espressioni](../expressions/expressions-page.md)  
  
 Per informazioni sull'impostazione di queste proprietà a livello di codice, fare clic sull'argomento seguente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### <a name="configuring-the-transfer-master-stored-procedures-task-programmatically"></a>Configurazione dell'attività Trasferisci stored procedure master a livello di codice  
  
## <a name="related-tasks"></a>Related Tasks  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostare le proprietà di un'attività o di un contenitore](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server attività Trasferisci oggetti di](transfer-sql-server-objects-task.md)   
 [Attività di Integration Services](integration-services-tasks.md)   
 [Flusso di controllo](control-flow.md)  
  
  
