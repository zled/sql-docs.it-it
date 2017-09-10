---
title: Istanza di Analysis Services Management | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0455fa4f-b92d-4a8b-a8f0-f2a268a5c84e
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 15aeda3b7b6ecb758aa2a0c0f3b8b2b85368dbf0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-instance-management"></a>Gestione di un'istanza di Analysis Services
  Un'istanza di Analysis Services è una copia del file eseguibile **msmdsrv.exe** che viene eseguita come un servizio del sistema operativo. Ogni istanza è completamente indipendente dalle altre istanze nello stesso server, disponendo di impostazioni proprie di configurazione, autorizzazioni, porte, account di avvio, archiviazione di file e proprietà della modalità server.  
  
 Ogni istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene eseguita come servizio Windows, Msmdsrv.exe, nel contesto di sicurezza di un account di accesso definito.  
  
-   Il nome del servizio dell'istanza predefinita di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è MSSQLServerOLAPService.  
  
-   Il nome del servizio di ogni istanza denominata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è MSOLAP$InstanceName.  
  
> [!NOTE]  
>  Se vengono installate più istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , tramite il programma di installazione viene inoltre installato un servizio redirector, integrato nel servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser. Il servizio redirector è responsabile dell'indirizzamento dei client all'istanza denominata appropriata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser viene sempre eseguito nel contesto di sicurezza dell'account Servizio locale, un account utente limitato utilizzato da Windows per servizi che non accedono a risorse esterne al computer locale.  
  
 L'espressione a più istanze indica la possibilità di scalabilità verticale mediante l'installazione di più istanze del server nello stesso hardware. Per Analysis Services in particolare, indica inoltre la possibilità di supportare modalità server diverse disponendo di più istanze nello stesso server, ciascuna configurata per l'esecuzione in una modalità specifica.  
  
 La modalità server è una proprietà del server che determina quale architettura di archiviazione e memoria viene utilizzata per tale istanza. Un server in esecuzione in modalità multidimensionale utilizza il livello di gestione delle risorse compilato per database di cubi multidimensionali e modelli di data mining. Al contrario, la modalità server tabulare usa il motore di analisi in memoria VertiPaq e la compressione dati per aggregare i dati quando richiesti.  
  
 Le differenze nell'architettura di archiviazione e memoria significano che una sola istanza di Analysis Services eseguirà database tabulari o database multidimensionali, ma non entrambi. La proprietà della modalità server determina quale tipo di database viene eseguito nell'istanza.  
  
 La modalità server viene impostata durante l'installazione quando si specifica il tipo di database che verrà eseguito nel server. Per supportare tutte le modalità disponibili, è possibile installare più istanze di Analysis Services, ciascuna distribuita in una modalità server corrispondente ai progetti che vengono compilati.  
  
 In generale, la maggior parte delle attività amministrative da eseguire non variano a seconda della modalità. Un amministratore di sistema di Analysis Services può utilizzare le stesse routine e gli stessi script per gestire qualsiasi istanza di Analysis Services nella rete, indipendentemente dalla modalità di installazione.  
  
> [!NOTE]  
>  L'eccezione è [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. L'amministrazione server di una distribuzione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] è sempre all'interno del contesto di una farm SharePoint. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] si differenzia dalle altre modalità server perché è sempre a istanza singola ed è sempre gestito da Amministrazione centrale SharePoint o dallo strumento di configurazione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Benché sia possibile, non è consigliabile connettersi a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint in SQL Server Management Studio o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. In una farm SharePoint è presente un'infrastruttura mediante la quale viene sincronizzato lo stato del server e controllata la disponibilità del server. L'utilizzo di altri strumenti può interferire con queste operazioni. Per altre informazioni sull'amministrazione server di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], vedere [Power Pivot per SharePoint &#40;SSAS&#41;](../../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Collegamento|Descrizione dell'attività|  
|----------|----------------------|  
|[Configurazione successiva all'installazione &#40;Analysis Services&#41;](../../analysis-services/instances/post-install-configuration-analysis-services.md)|Descrive le attività necessarie e facoltative per completare o modificare un'installazione di Analysis Services.|  
|[Connetti ad Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)|Descrive le proprietà delle stringhe di connessione, le librerie client, le metodologie di autenticazione e le procedure per stabilire o cancellare le connessioni.|  
|[Monitorare un'istanza di Analysis Services](../../analysis-services/instances/monitor-an-analysis-services-instance.md)|Vengono descritti strumenti e tecniche per monitorare un'istanza del server, incluso il modo di utilizzare Performance Monitor e SQL Server Profiler.|  
|[Disponibilità elevata e scalabilità](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)|Descrive le tecniche usate più di frequente per garantire ai database di Analysis Services disponibilità elevata e scalabilità. |  
|[Scenari di globalizzazione per Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md)|Illustra il supporto per la lingua e le regole di confronto, i passaggi per modificare entrambe le proprietà e i suggerimenti per l'impostazione e il test dei comportamenti della lingua e delle regole di confronto.|  
|[Registrare le operazioni in Analysis Services](../../analysis-services/instances/log-operations-in-analysis-services.md)|Descrive i log e illustra come configurarli.|  
  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto tra soluzioni tabulari e multidimensionali &#40;SSAS&#41;](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Strumenti di configurazione Power Pivot](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)   
 [Amministrazione e configurazione del server PowerPivot in Amministrazione centrale](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
