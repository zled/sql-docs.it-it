---
title: "Bilanciamento del carico dei pacchetti su server remoti tramite SQL Server Agent | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bilanciamento del carico [Integration Services]"
  - "pacchetti padre [Integration Services]"
  - "SQL Server Agent [Integration Services]"
ms.assetid: 9281c5f8-8da3-4ae8-8142-53c5919a4cfe
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Bilanciamento del carico dei pacchetti su server remoti tramite SQL Server Agent
  Quando è necessario eseguire numerosi pacchetti, è preferibile utilizzare altri server eventualmente disponibili. L'utilizzo di altri server per l'esecuzione di più pacchetti controllati da un unico pacchetto padre è detto bilanciamento del carico. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]il bilanciamento del carico è una procedura manuale che deve essere definita dai proprietari dei pacchetti. Il bilanciamento del carico non viene infatti eseguito automaticamente dai server. Inoltre, sui server remoti è possibile eseguire esclusivamente pacchetti interi, non singole attività in altri pacchetti.  
  
 Il bilanciamento del carico risulta utile negli scenari seguenti:  
  
-   I pacchetti possono essere eseguiti contemporaneamente.  
  
-   I pacchetti sono di grandi dimensioni e, se eseguiti sequenzialmente, richiedere un tempo di esecuzione superiore al tempo massimo consentito per l'elaborazione.  
  
 Amministratori e architetti possono stabilire se l'utilizzo di server aggiuntivi per l'elaborazione può costituire un vantaggio per i processi.  
  
## Illustrazione del bilanciamento del carico  
 Nella figura seguente viene illustrato un pacchetto padre in un server. Il pacchetto padre contiene più attività Esegui processo di SQL Server Agent e ogni attività nel pacchetto padre chiama un processo di SQL Server Agent su un server remoto. Ogni server remoto contiene un processo di SQL Server Agent che include un passaggio in cui viene chiamato un pacchetto su tale server.  
  
 ![Panoramica dell'architettura di bilanciamento del carico di SSIS](../../integration-services/packages/media/loadbalancingoverview.gif "Panoramica dell'architettura di bilanciamento del carico di SSIS")  
  
 I passaggi necessari per il bilanciamento del carico in questa architettura non sono concetti nuovi. Il bilanciamento del carico viene infatti ottenuto utilizzando in modo nuovo concetti esistenti e oggetti SSIS comuni.  
  
## Esecuzione di pacchetti in un'istanza remota tramite SQL Server Agent  
 Nell'architettura di base per l'esecuzione di pacchetti remoti è presente un pacchetto centrale che risiede nell'istanza di SQL Server che controlla gli altri pacchetti remoti. Tale pacchetto è illustrato nella figura, con il nome Pacchetto SSIS padre. L'istanza in cui risiede tale pacchetto controlla l'esecuzione dei processi di SQL Server Agent che eseguono i pacchetti figlio. I pacchetti figlio non vengono eseguiti in base a una pianificazione fissa controllata da SQL Server Agent sul server remoto, ma vengono avviati da SQL Server Agent quando quest'ultimo viene chiamato dal pacchetto padre e vengono eseguiti nella stessa istanza di SQL Server in cui risiede SQL Server Agent.  
  
 Per poter eseguire un pacchetto remoto tramite SQL Server Agent, è necessario configurare i pacchetti padre e figlio, quindi configurare i processi di SQL Server Agent che controllano i pacchetti figlio. Nelle sezioni seguenti vengono fornite ulteriori informazioni sulle procedure per la creazione, la configurazione, l'esecuzione e la manutenzione di pacchetti eseguiti su server remoti. Il processo include numerosi passaggi:  
  
-   Creazione dei pacchetti figlio e installazione di questi ultimi nei server remoti.  
  
-   Creazione dei processi di SQL Server Agent sulle istanze remote in cui verranno eseguiti i pacchetti.  
  
-   Creazione del pacchetto padre.  
  
-   Determinazione dello scenario di registrazione per i pacchetti figlio.  
  
 Nella tabella seguente vengono forniti i collegamenti agli argomenti che illustrano i passaggi del processo.  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Implementazione di pacchetti figlio](../../integration-services/packages/implementation-of-child-packages.md)|Vengono descritte l'installazione dei pacchetti e la creazione dei processi di SQL Server Agent per l'esecuzione di tali pacchetti.|  
|[Implementazione del pacchetto padre](../../integration-services/packages/implementation-of-the-parent-package.md)|Viene descritta la creazione di un pacchetto padre contenente più attività Esegui processo di SQL Server Agent. Ogni attività esegue uno dei pacchetti figlio.|  
|[Registrazione per pacchetti con bilanciamento del carico in server remoti](../../integration-services/packages/logging-for-load-balanced-packages-on-remote-servers.md)|Viene descritto lo scenario di registrazione per i pacchetti remoti.|  
  
## Attività correlate  
 [Pianificare un pacchetto tramite SQL Server Agent](../../integration-services/packages/schedule-a-package-by-using-sql-server-agent.md)  
  
  