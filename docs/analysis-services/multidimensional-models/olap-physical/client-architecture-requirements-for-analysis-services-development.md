---
title: Requisiti di architettura client per l'analisi di sviluppo di servizi | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- local mining models [Analysis Services]
- Analysis Services, architecture
- providers [Analysis Services]
- data pumps [Analysis Services]
- client architecture [Analysis Services]
- local cubes [Analysis Services]
ms.assetid: 03a8eb6b-159f-4a0a-afbe-06a2424b6090
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b15bbb83f989f53ef8e8b959771f5bd7fa568a12
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="client-architecture-requirements-for-analysis-services-development"></a>Requisiti di architettura client per sviluppo Analysis Services
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta un'architettura thin client. Il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] il motore di calcolo è interamente basato su server, pertanto tutte le query vengono risolte nel server. Per ogni query è quindi necessario un solo round trip tra il client e il server, il che significa che le prestazioni sono scalabili a mano a mano che le query diventano più complesse.  
  
 Il protocollo nativo per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] è XML for Analysis (XML/Un). In [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sono disponibili svariate interfacce di accesso ai dati per le applicazioni client, ma tutti questi componenti comunicano con un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] tramite XML for Analysis.  
  
 Con [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] vengono forniti svariati provider per il supporto di diversi linguaggi di programmazione. Un provider comunica con un server [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mediante l'invio e la ricezione di XML for Analysis in pacchetti SOAP attraverso il protocollo TCP/IP oppure HTTP tramite Internet Information Services (IIS). Una connessione HTTP utilizza un oggetto COM, di cui viene creata un'istanza da IIS e denominato data pump, che funge da conduttura per i dati di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Il data pump non esamina in alcun modo i dati sottostanti contenuti nel flusso HTTP e le strutture dei dati sottostanti non sono disponibili al codice nella libreria di dati stessa.  
  
 ![Architettura client logica per Analysis Services](../../../analysis-services/multidimensional-models/olap-physical/media/as-clientarch9.gif "architettura client logica per Analysis Services")  
  
 Le applicazioni client Win32 possono connettersi a un server [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] tramite interfacce OLE DB per OLAP oppure tramite il modello a oggetti Microsoft® ActiveX® Data Objects (ADO) per linguaggi di automazione COM (Component Object Model), ad esempio Microsoft Visual Basic®. Le applicazioni scritte in linguaggi .NET possono connettersi a un server [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizzando ADOMD.NET.  
  
 Le applicazioni esistenti possono comunicare con [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] senza richiedere alcuna modifica, semplicemente tramite uno dei provider di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Linguaggio di programmazione|Interfaccia di accesso ai dati|  
|--------------------------|---------------------------|  
|C++|OLE DB per OLAP|  
|Visual Basic 6|ADO MD|  
|Linguaggi .NET|ADO MD.NET|  
|Qualsiasi linguaggio che supporta SOAP|XML for Analysis|  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] è dotato di un'architettura Web con un livello intermedio pienamente scalabile che ne consente la distribuzione in organizzazioni sia di piccole che di grandi dimensioni. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] fornisce supporto del livello intermedio largo per i servizi Web. Le applicazioni ASP sono supportate tramite OLE DB per OLAP e ADO MD, applicazioni ASP.NET sono supportate tramite ADOMD.NET. Il livello intermedio, illustrato nella figura seguente, è scalabile per un numero elevato di utenti simultanei.  
  
 ![Diagramma logico per l'architettura di livello intermedio](../../../analysis-services/multidimensional-models/olap-physical/media/as-midtierarch9.gif "diagramma logico per l'architettura di livello intermedio")  
  
 Le applicazioni sia client che di livello intermedio possono comunicare direttamente con [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] senza l'intervento di un provider. Le applicazioni client e di livello intermedio possono inviare XML for Analysis in pacchetti SOAP attraverso il protocollo TCP/IP, HTTP o HTTPS. Il client può essere codificato in qualsiasi linguaggio che supporta SOAP. In tal caso, per semplificare la gestione delle comunicazioni è consigliabile utilizzare Internet Information Services (IIS) con HTTP, ma è anche possibile ricorrere a una connessione diretta al server tramite TCP/IP. Questa è la massima soluzione thin client supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="analysis-services-in-tabular-or-sharepoint-mode"></a>Analysis Services in modalità tabulare o SharePoint  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], il server può essere avviato in modalità del motore (VertiPaq) analitica in memoria xVelocity per i database tabulari e per [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] le cartelle di lavoro sono stati pubblicati in un sito di SharePoint.  
  
 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] e [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] sono gli unici ambienti client supportati per la creazione e l'esecuzione di query su database in memoria in cui viene utilizzata rispettivamente la modalità SharePoint o tabulare. L'oggetto incorporato [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] database creato tramite Excel e [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] strumenti è contenuto all'interno della cartella di lavoro di Excel e viene salvato come parte del file con estensione xlsx di Excel.  
  
 Tuttavia, una cartella di lavoro [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] può utilizzare dati archiviati in un cubo tradizionale se si importano i dati del cubo nella cartella di lavoro. È possibile importare anche dati da un'altra cartella di lavoro di [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] se è stata pubblicata in un sito di SharePoint.  
  
> [!NOTE]  
>  Quando si utilizza un cubo come origine dati per la cartella di lavoro di [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)], i dati che si ottengono dal cubo vengono definiti come query MDX. Tuttavia, i dati vengono importati come snapshot bidimensionale. Non è possibile operare in modo interattivo con i dati o aggiornare i dati dal cubo.  
  
 Per ulteriori informazioni sull'utilizzo di un cubo SSAS come origine dati, vedere il [Power Pivot per Excel](http://go.microsoft.com/fwlink/?LinkId=164234).  
  
### <a name="interfaces-for-power-pivot-client"></a>Interfacce per i Client di Power Pivot  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]interagisce con il motore di archiviazione motore (VertiPaq) analitica in memoria xVelocity all'interno della cartella di lavoro tramite le interfacce e stabiliti lingue per Analysis Services: AMO e ADOMD.NET, MDX e XMLA. All'interno del componente aggiuntivo, le misure vengono definite tramite un linguaggio delle formule simile a Excel, Data Analysis Expressions (DAX). Le espressioni DAX sono incorporate all'interno dei messaggi XMLA inviati al server in-process.  
  
### <a name="providers"></a>Provider  
 Le comunicazioni tra [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ed Excel utilizzano il provider MSOLAP OLEDB (versione 11.0). All'interno del provider MSOLAP sono contenuti quattro diversi moduli, o trasporti, che possono essere utilizzati per l'invio di messaggi tra il client e il server.  
  
 **TCP/IP** utilizzato per le connessioni client-server normale.  
  
 **HTTP** utilizzato per le connessioni HTTP tramite il servizio di data pump SSAS o da una chiamata a SharePoint [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] componente servizio Web (WS).  
  
 **INPROC** utilizzato per le connessioni al motore in-process.  
  
 **CANALE** riservato per le comunicazioni con il [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] servizio di sistema nella farm di SharePoint.  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del server del motore OLAP](../../../analysis-services/multidimensional-models/olap-physical/olap-engine-server-components.md)  
  
  
