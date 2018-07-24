---
title: Guida a PolyBase | Microsoft Docs
ms.date: 05/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: get-started-article
f1_keywords:
- PolyBase
- PolyBase, guide
helpviewer_keywords:
- PolyBase
- PolyBase, overview
- Hadoop import ×
- Hadoop export
- Hadoop export, PolyBase overview
- Hadoop import, PolyBase overview
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b94cc6a8a906721c43f1da66867d954fa8f9b50b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37970573"
---
# <a name="polybase-guide"></a>Guida a PolyBase
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
  PolyBase è una tecnologia che accede ai dati all'esterno del database tramite il linguaggio T-SQL.  In SQL Server 2016 questa tecnologia consente di eseguire query sui dati esterni in Hadoop o di importare/esportare dati da Archiviazione BLOB di Azure. Le query vengono ottimizzate per eseguire il push del calcolo in Hadoop. In Azure SQL Data Warehouse è possibile importare/esportare dati da Archiviazione BLOB di Azure e Azure Data Lake Store.
  
  
 Per usare PolyBase, vedere [Get started with PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)(Introduzione a PolyBase).  
  
 ![Logica PolyBase](../../relational-databases/polybase/media/polybase-logical.png "Logica PolyBase")  
  
## <a name="why-use-polybase"></a>Perché usare PolyBase  
Per prendere decisioni valide, è necessario analizzare sia i dati relazionali che altri dati non strutturati in tabelle, in particolare in Hadoop, ma è difficile farlo se non è possibile trasferire i dati tra i diversi tipi di archivi dati. PolyBase risolve il problema operando sui dati esterni a SQL Server.  
  
In sostanza, PolyBase non richiede di installare software aggiuntivo nell'ambiente Hadoop. Le query dei dati esterni usano la stessa sintassi della query di una tabella di database in modo trasparente. PolyBase gestisce tutti i dettagli in background e, per eseguire query sulle tabelle esterne, non è necessario che l'utente finale conosca Hadoop. 
  
 PolyBase può:  
  
-   **Eseguire query sui dati archiviati in Hadoop da SQL Server o PDW.** Gli utenti scelgono di archiviare i dati in sistemi distribuiti e scalabili convenienti, come Hadoop. PolyBase semplifica la query dei dati con T-SQL.  
  
-   **Eseguire query sui dati archiviati in Archiviazione BLOB di Azure.** Nell'archivio BLOB di Azure è possibile salvare i dati da usare con i servizi di Azure.  PolyBase semplifica l'accesso ai dati con T-SQL.  
  
-   **Importare dati da Hadoop, Archiviazione BLOB di Azure o Azure Data Lake Store.** Sfruttare la velocità della tecnologia columnstore e delle funzionalità di analisi di Microsoft SQL importando i dati da Hadoop, Archiviazione BLOB di Azure o Azure Data Lake Store in tabelle relazionali. Non è necessario uno strumento di importazione o ETL separato.  

-   **Esportare i dati in Hadoop, nell'archivio BLOB di Azure o in Azure Data Lake Store.** Archiviare i dati in Hadoop, nell'archivio BLOB di Azure o in Azure Data Lake Store per un'archiviazione conveniente e mantenerli online per accedervi facilmente.  
  
-   **Integrarsi con strumenti BI.** Usare PolyBase con la business intelligence e lo stack di analisi di Microsoft o usare strumenti di terze parti compatibili con SQL Server.  
  
## <a name="performance"></a>restazioni  
  
-   **Eseguire il push del calcolo in Hadoop.** Query Optimizer prende una decisione basata sui costi di eseguire il push del calcolo in Hadoop se in questo modo migliorano le prestazioni della query.  Per prendere la decisione basata sui costi, usa le statistiche sulle tabelle esterne. Il push del calcolo crea processi MapReduce e sfrutta le risorse di calcolo distribuite di Hadoop.  
  
-   **Ridimensionare le risorse di calcolo.** Per migliorare le prestazioni delle query, è possibile usare i [gruppi con scalabilità orizzontale di PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)per SQL Server. In questo modo viene abilitato il trasferimento dei dati paralleli tra le istanze di SQL Server e i nodi di Hadoop e vengono aggiunte le risorse di calcolo per operare sui dati esterni.  
  
## <a name="polybase-guide-topics"></a>Argomenti della guida di PolyBase  
 Questa guida include argomenti che illustrano come usare PolyBase in modo efficiente ed efficace.  
  
|||  
|-|-|  
|**Argomento**|**Descrizione**|  
|[Get started with PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)|Passaggi di base per installare e configurar PolyBase. Illustra come creare oggetti esterni che fanno riferimento ai dati in Hadoop o nell'archivio BLOB di Azure e include esempi di query.|  
|[PolyBase Versioned Feature Summary (Riepilogo delle funzionalità con controllo delle versioni di PolyBase)](../../relational-databases/polybase/polybase-versioned-feature-summary.md)|Descrive le funzionalità di PolyBase supportate in SQL Server, nel database SQL e in SQL Data Warehouse.|  
|[gruppi con scalabilità orizzontale di PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md)|Parallelismo con scalabilità orizzontale tra SQL Server e Hadoop con i gruppi con scalabilità orizzontale di SQL Server.|  
|[Installazione di PolyBase](../../relational-databases/polybase/polybase-installation.md)|Informazioni di riferimento e passaggi per l'installazione di PolyBase con l'installazione guidata o con uno strumento da riga di comando.|  
|[Configurazione di PolyBase](../../relational-databases/polybase/polybase-configuration.md)|Configurare le impostazioni di SQL Server per PolyBase.  Ad esempio, configurare la distribuzione del calcolo e la sicurezza Kerberos.|  
|[Oggetti T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md)|Creare gli oggetti T-SQL usati da PolyBase per definire e accedere ai dati esterni.|  
|[PolyBase Queries](../../relational-databases/polybase/polybase-queries.md)|Usare le istruzioni T-SQL per eseguire una query, importare o esportare i dati esterni.|  
|[Risoluzione dei problemi di PolyBase](../../relational-databases/polybase/polybase-troubleshooting.md)|Tecniche per gestire le query di PolyBase. Usare le viste DMV per monitorare le query di PolyBase e imparare a leggere un piano di query di PolyBase per trovare i colli di bottiglia delle prestazioni.|  
  
  
