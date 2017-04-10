---
title: "Gestione di un dominio | Microsoft Docs"
ms.custom: ""
ms.date: "07/31/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5ab71a3-0dac-45b1-be8e-93bf7e0e03ce
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Gestione di un dominio
  In questo argomento viene descritto l'utilizzo dei domini in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Un dominio contiene una rappresentazione semantica dei dati in un campo specifico nell'origine dati che deve essere analizzata. Un dominio fa parte della Knowledge Base che si crea per un'origine dati e le informazioni che si accumulano analizzando un'origine dati di esempio, o importando dati, vengono aggiunte ai domini definiti nella Knowledge Base. Le informazioni in tali domini verranno in seguito utilizzate per eseguire attività di pulizia e di individuazione delle corrispondenze in un progetto Data Quality. I domini sono al centro di tutte le attività in Data Quality Services.  
  
 Si esegue il mapping di un dominio a un campo dell'origine dati e viene popolato nel corso delle attività di individuazione delle informazioni, gestione del dominio e individuazione delle corrispondenze. Le modalità di caricamento dei dati dall'origine e l'output dei dati in un report vengono definite nelle proprietà di dominio. Quando si utilizza un provider di dati di riferimento per la pulizia dei dati, si collega un servizio dati di riferimento a un dominio singolo o composito. Si creano regole da applicare ai dati in un dominio ed è possibile creare relazioni basate sui termini per un dominio. È possibile visualizzare e correggere i dati nel dominio.  
  
 È inoltre possibile creare un dominio composito che comprende due o più domini singoli, ciascuno contenente informazioni sui dati comuni. Per ulteriori informazioni, vedere [la gestione di un dominio composito](../data-quality-services/managing-a-composite-domain.md).  
  
## Proprietà dominio  
 Quando si crea un dominio, sono disponibili le opzioni seguenti sul popolamento del dominio con i dati di origine e sull'output dei valori del dominio. Per ulteriori informazioni, vedere [Imposta proprietà dominio](../data-quality-services/set-domain-properties.md).  
  
-   Selezionare il tipo di dati con cui popolare il dominio. Per informazioni sui tipi di dati supportati per ogni tipo di dati di dominio, vedere [SQL Server supportate e i tipi di dati SSIS per i domini DQS](../data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).  
  
-   Specificare che dal dominio verranno inviati all'output solo i valori principali e non i relativi sinonimi.  
  
-   Specificare che i valori del dominio verranno restituiti in un formato determinato, a seconda del tipo di dati.  
  
-   Se il tipo di dati è una stringa, è possibile normalizzare la stringa rimuovendo i caratteri speciali al momento del caricamento dall'origine dati nel dominio.  
  
-   Se il tipo di dati è una stringa, è possibile eseguire il correttore ortografico DQS per controllare la sintassi, l'ortografia e struttura della frase della stringa e indicare eventuali errori potenziali durante il **i valori di dominio** pagina di **Gestione dominio**. Ciò include la specifica della lingua per cui viene eseguito il correttore ortografico.  
  
-   Se il tipo di dati è una stringa, è possibile specificare che DQS non identifichi errori di sintassi quando si è certi che le stringhe non contengono tali errori.  
  
## Argomenti della sezione  
 L'utilizzo di un dominio consente di effettuare le operazioni seguenti:  
  
|||  
|-|-|  
|Creare una rappresentazione semantica per un campo dati con un tipo di dati specifico, specificare come viene popolato il dominio, e formattare l'output del dominio|[Creazione di un dominio](../data-quality-services/create-a-domain.md)|  
|Collegare un dominio a un altro dominio, consentendone la condivisione delle impostazioni e dei valori|[Creazione di un dominio collegato](../data-quality-services/create-a-linked-domain.md)|  
|Collegare un servizio dati di riferimento a un dominio singolo o composto|[Collegare un dominio o un dominio composito ai dati di riferimento](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)|  
|Modificare o evidenziare i valori in una Knowledge Base.|[Modificare i valori di dominio](../data-quality-services/change-domain-values.md)|  
|Utilizzare regole di convalida e di standardizzazione|[Create a Domain Rule](../data-quality-services/create-a-domain-rule.md)|  
|Utilizzare relazioni per correggere un termine che forma parte di un valore in un dominio|[Create Term-Based Relations](../data-quality-services/create-term-based-relations.md)|  
|Completare, chiudere o annullare l'attività di gestione del dominio|[Sospensione dell'attività di gestione del dominio](../Topic/End%20the%20Domain%20Management%20Activity.md)|  
  
## Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Compilazione di una Knowledge Base eseguendo l'individuazione delle informazioni e gestendo queste ultime in modo interattivo|[Compilazione di una Knowledge Base](../data-quality-services/building-a-knowledge-base.md)|  
|Importazione o esportazione di informazioni da una Knowledge Base.|[Importazione ed esportazione delle informazioni](../data-quality-services/importing-and-exporting-knowledge.md)|  
|Creazione di un dominio composito e aggiunta di informazioni al dominio.|[Gestione di un dominio composito](../data-quality-services/managing-a-composite-domain.md)|  
  
  