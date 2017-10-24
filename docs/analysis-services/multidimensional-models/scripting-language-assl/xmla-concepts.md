---
title: Concetti XMLA | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XMLA, concepts
ms.assetid: 816183a7-d2f7-4e14-8e5b-2a4c1798fbc1
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c8df1713f3015e9319f7a1323b43f697bebb625
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xmla-concepts"></a>Concetti XMLA
  Lo standard aperto XMLA (XML for Analysis) supporta l’accesso a origini dati che risiedono sul World Wide Web. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implementa XMLA per la specifica XMLA 1.1.  
  
 XML for Analysis (XMLA) è protocollo XML basato su SOAP (Simple Object Access Protocol), progettato in modo specifico per accedere a tutti i dati di qualsiasi origine dati multidimensionale standard disponibile sul Web. XMLA elimina inoltre l'esigenza di distribuire un componente client che espone modello COM (Component Object) o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] interfacce di .NET Framework. XMLA è ottimizzato per Internet, dove i round trip al server sono costosi in termini di tempo e risorse e quando le connessioni con stato a un'origine dati possono limitare le connessioni utente nel server.  
  
 XMLA è il protocollo nativo per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], utilizzato per tutte le interazioni tra un'applicazione client e un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta completamente XML for Analysis 1.1 e fornisce anche estensioni per supportare la gestione di metadati, la gestione della sessione e le funzionalità di blocco. Sia la libreria AMO (Analysis Management Objects) che ADOMD.NET utilizzano il protocollo XMLA quando comunicando con un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="handling-xmla-communications"></a>Gestione di comunicazioni XMLA  
 Lo standard aperto XMLA descrive due metodi generalmente accessibili: **Discover** e **Execute**. Tali metodi utilizzano l'architettura client-server a regime di controllo libero supportata da XML per gestire informazioni in ingresso e in uscita in un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Il **Discover** metodo ottiene le informazioni e i metadati da un servizio Web. Tali informazioni possono includere un elenco di origini dati disponibili nonché informazioni su alcuni dei provider dell'origine dati. Le proprietà definiscono i dati ottenuti da un'origine dati. Il **Discover** è un metodo comune per la definizione di molti tipi di informazioni di un'applicazione client può richiedere dalle origini dati su [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanze. Le proprietà e l'interfaccia generica forniscono estensibilità senza che sia necessario riscrivere funzioni esistenti in un'applicazione client.  
  
 Il **Execute** metodo consente alle applicazioni di eseguire comandi specifici del provider di origini dati XMLA.  
  
 Sebbene il protocollo XMLA sia ottimizzato per le applicazioni Web, può essere inoltre utilizzato per applicazioni su reti LAN. Le applicazioni seguenti possono sfruttare i vantaggi di tale API basata su XML:  
  
-   Applicazioni client/server per cui è necessaria tecnologia flessibile tra il client e il server  
  
-   Applicazioni client/server destinate a più sistemi operativi  
  
-   Client per cui non è necessario uno stato significativo per aumentare la capacità del server  
  
## <a name="xmla-and-the-unified-dimensional-model"></a>XMLA e modello UDM (Unified Dimensional Model)  
 XMLA è il protocollo utilizzato da applicazioni di Business Intelligence che utilizzano la metodologia del modello UDM (Unified Dimensional Model).  
  
  

