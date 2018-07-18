---
title: Guida di riferimento ai file di input XML (Ottimizzazione guidata motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7ca9a22a2f6f4732a97387778484aae261fc0848
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183488"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Guida di riferimento ai file di input XML (Ottimizzazione guidata motore di database)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] Ottimizzazione guidata può usare un file di input XML per ottimizzare un database. In questo file XML sono specificati i database, le tabelle, i file o le tabelle del carico di lavoro e le opzioni di ottimizzazione da utilizzare per la sessione di ottimizzazione. È inoltre possibile utilizzare questo file per definire una configurazione specificata dall'utente per eseguire un'analisi di simulazione.  
  
 Un file di input XML di Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] contiene una gerarchia di elementi XML, ognuno dei quali include testo o altri elementi che specificano le impostazioni della sessione di ottimizzazione. È necessario che il file di input XML di Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] sia conforme agli standard di correttezza del formato XML. Per tutti i nomi degli elementi viene pertanto fatta distinzione tra maiuscole e minuscole. Gli elementi vengono specificati mediante l'uso della distinzione tra maiuscole e minuscole Pascal, in base alla quale il primo carattere e la prima lettera della parola successiva concatenata sono in maiuscolo.  
  
 Tutti i valori degli elementi devono essere conformi alle convenzioni di denominazione XML. Per altre informazioni su queste convenzioni, vedere [Contenuto testuale XML](http://go.microsoft.com/fwlink/?LinkId=7614) in MSDN Library.  
  
 Si noti che questa Guida di riferimento non è completa. Per informazioni su tutti gli elementi che è possibile utilizzare per definire l'input XML, fare riferimento all'XML Schema DTASchema.xsd di Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="xml-declaration"></a>Dichiarazione XML  
  
-   [Dati XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Elemento radice DTAXML  
  
-   [Elemento DTAXML &#40;DTA&#41;](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Elementi DTAInput  
  
-   [Elemento DTAInput &#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [Elemento server &#40;DTA&#41;](server-element-dta.md)  
  
-   [Elemento Workload &#40;DTA&#41;](workload-element-dta.md)  
  
-   [Elemento TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [Elemento di configurazione &#40;DTA&#41;](configuration-element-dta.md)  
  
## <a name="server-elements"></a>Elementi server  
  
-   [Nome di elemento per il Server &#40;DTA&#41;](name-element-for-server-dta.md)  
  
-   [Elemento database per Server &#40;DTA&#41;](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Elementi del carico di lavoro  
  
-   [File di elemento &#40;DTA&#41;](file-element-dta.md)  
  
-   [Elemento database per il carico di lavoro &#40;DTA&#41;](database-element-for-workload-dta.md)  
  
-   [Elemento EventString &#40;DTA&#41;](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Elementi delle opzioni di ottimizzazione  
  
-   [Elemento TuningTimeInMin &#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [Elemento StorageBoundInMB &#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [Elemento TestServer &#40;DTA&#41;](testserver-element-dta.md)  
  
-   [Elemento FeatureSet &#40;DTA&#41;](featureset-element-dta.md)  
  
-   [Elemento Partitioning &#40;DTA&#41;](partitioning-element-dta.md)  
  
-   [Elemento DropOnlyMode &#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [Elemento KeepExisting &#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [Elemento OnlineIndexOperation &#40;DTA&#41;](onlineindexoperation-element-dta.md)  
  
-   [Elemento DatabaseToConnect &#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Elementi di configurazione  
  
-   [Elemento server per la configurazione &#40;DTA&#41;](server-element-for-configuration-dta.md)  
  
-   [Elemento database per la configurazione &#40;DTA&#41;](database-element-for-configuration-dta.md)  
  
-   [Elemento Recommendation &#40;DTA&#41;](recommendation-element-dta.md)  
  
-   [Creare l'elemento &#40;DTA&#41;](create-element-dta.md)  
  
-   [Indice elemento &#40;DTA&#41;](index-element-dta.md)  
  
-   [Nome di elemento per l'indice &#40;DTA&#41;](name-element-for-index-dta.md)  
  
-   [Elemento Column per Index &#40;DTA&#41;](column-element-for-index-dta.md)  
  
-   [Nome di elemento per la colonna &#40;DTA&#41;](name-element-for-column-dta.md)  
  
-   [Elemento filegroup per Index &#40;DTA&#41;](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Elementi di database  
  
-   [Nome di elemento per il Database &#40;DTA&#41;](name-element-for-database-dta.md)  
  
-   [Elemento schema per il Database &#40;DTA&#41;](schema-element-for-database-dta.md)  
  
-   [Nome di elemento per lo Schema &#40;DTA&#41;](name-element-for-schema-dta.md)  
  
-   [Elemento di tabella per lo Schema &#40;DTA&#41;](table-element-for-schema-dta.md)  
  
-   [Nome di elemento per la tabella &#40;DTA&#41;](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Ottimizzazione guidata motore di database](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
