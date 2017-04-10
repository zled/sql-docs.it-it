---
title: "Accesso ai file utilizzati dai pacchetti | Microsoft Docs"
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
  - "pacchetti SSIS, sicurezza"
  - "pacchetti [Integration Services], sicurezza"
  - "file di configurazione [Integration Services]"
  - "file del checkpoint"
  - "pacchetti di Integration Services, sicurezza"
  - "log [Integration Services], sicurezza"
  - "file [Integration Services], sicurezza"
  - "pacchetti di SQL Server Integration Services, sicurezza"
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Accesso ai file utilizzati dai pacchetti
  Il livello di protezione del pacchetto non protegge i file archiviati al di fuori del pacchetto. ovvero i file seguenti:  
  
-   File di configurazione  
  
-   File del checkpoint  
  
-   File di log  
  
 Questi file devono essere protetti separatamente, soprattutto se includono informazioni riservate.  
  
## File di configurazione  
 Se un file di configurazione contiene dati riservati, come informazioni su account di accesso e password, è consigliabile salvare tale configurazione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure usare un elenco di controllo di accesso (ACL) per limitare l'accesso al percorso o alla cartella in cui sono archiviati i file e consentire l'accesso solo a determinati account. L'accesso viene in genere concesso agli account autorizzati all'esecuzione dei pacchetti e agli account utilizzati per la gestione e la risoluzione dei problemi dei pacchetti, che possono comportare la revisione dei contenuti dei file di configurazione, del checkpoint e di log. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dispone di un'archiviazione più sicura perché la protezione viene garantita ai livelli del server e del database. Per salvare le configurazioni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario usare il tipo di configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mentre per salvarle nel file system è necessario utilizzare il tipo di configurazione XML.  
  
 Per altre informazioni, vedere [Configurazioni di pacchetto](../../integration-services/packages/package-configurations.md), [Creazione di configurazioni dei pacchetti](../../integration-services/packages/create-package-configurations.md) e [Considerazioni sulla sicurezza per un'installazione SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
## File del checkpoint  
 In modo analogo, è consigliabile utilizzare un elenco di controllo di accesso del sistema operativo per la sicurezza del percorso o della cartella se il file del checkpoint utilizzato dal pacchetto contiene informazioni riservate. Nei file del checkpoint vengono salvate informazioni aggiornate sullo stato del pacchetto e sui valori correnti delle variabili. Il pacchetto potrebbe includere, ad esempio, una variabile personalizzata per la memorizzazione di un numero di telefono. Per ulteriori informazioni, vedere [Restart Packages by Using Checkpoints](../../integration-services/packages/restart-packages-by-using-checkpoints.md).  
  
## File di log  
 Anche le voci di log scritte nel file system dovrebbero essere protette tramite un elenco di controllo di accesso. È inoltre possibile archiviare le voci di log nelle tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e proteggerle con gli strumenti di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le voci di log possono infatti includere informazioni riservate. Se ad esempio il pacchetto contiene un'attività Esegui SQL che genera un'istruzione SQL che fa riferimento a un numero di telefono, la voce di log per l'istruzione SQL conterrà tale numero di telefono. L'istruzione SQL potrebbe inoltre esporre informazioni private sui nomi di tabelle e colonne nei database. Per altre informazioni, vedere [Registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md).  
  
  