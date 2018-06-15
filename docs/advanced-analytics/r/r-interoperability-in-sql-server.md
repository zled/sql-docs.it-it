---
title: Interoperabilità di R in SQL Server R Services | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 59196e0569ac9cc683b3affa68fc17f068e74994
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203173"
---
# <a name="r-interoperability-in-sql-server"></a>Interoperabilità di R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo argomento descrive il meccanismo per l'esecuzione di R in SQL Server e vengono descritte le differenze tra Microsoft R e open source R.

Si applica a: R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

Per informazioni sui componenti aggiuntivi, vedere [nuovi componenti di SQL Server](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md).

### <a name="open-source-r-components"></a>Componenti di R open source

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] include una distribuzione completa degli strumenti e dei pacchetti R di base. Per altre informazioni sui componenti inclusi nella distribuzione base, vedere la documentazione installata durante l'installazione nel percorso predefinito seguente: `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

Nell'ambito dell'installazione di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], è necessario accettare i termini della licenza GNU Public License. Successivamente, è possibile eseguire i pacchetti R standard senza ulteriori modifiche, esattamente come per qualsiasi altra distribuzione open source di R.

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] non modifica in alcun modo il runtime di R. Il runtime di R viene eseguito all'esterno del processo di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e può essere eseguito in modo indipendente da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Tuttavia, è consigliabile non eseguire questi strumenti mentre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] usa R, per evitare conflitti di risorse.

La distribuzione base dei pacchetti R associata a una specifica istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] è disponibile nella cartella associata all'istanza. Ad esempio, se è installato R Services nell'istanza predefinita, le librerie R si trovano in questa cartella per impostazione predefinita:

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library

Analogamente, gli strumenti di R associati con l'istanza predefinita sono posizionati nella cartella parola per impostazione predefinita:

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin

Per ulteriori informazioni sul modo in cui Microsoft R è diverso da una distribuzione di basa di R che si potrebbero ottenere da cran r, vedere [interoperabilità con prodotti di Microsoft R e linguaggio R e funzionalità](https://docs.microsoft.com/en-us/r-server/what-is-r-server-interoperability)

### <a name="additional-r-packages-from-microsoft-r"></a>Pacchetti R aggiuntivi da Microsoft R

Oltre alla distribuzione di base R, [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] include alcuni pacchetti R proprietarie, nonché un framework per l'esecuzione parallela di R che supporta inoltre l'esecuzione di R in contesti di calcolo remoto.

Questo set combinato di funzionalità R (distribuzione base di R e funzionalità e pacchetti avanzati di R) è denominato **Microsoft R**. Se si installa Microsoft R Server (Standalone), si ottiene esattamente lo stesso set di pacchetti che viene installato con SQL Server R Services (In-Database) ma in una cartella diversa.

Microsoft R include una distribuzione della libreria del kernel matematico di Intel, che viene usata quando possibile per velocizzare l'elaborazione matematica. Ad esempio, la libreria dell'algebra lineare di base (BLAS, Basic Linear Algebra) viene usata per molti dei pacchetti aggiuntivi, oltre che per R stesso. Per altre informazioni, vedere gli articoli seguenti:

+ [How the Intel Math Kernel Speeds up R](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html) (In che modo il kernel matematico di Intel velocizza R)
+ [Performance benefits of linking R to multithreaded math libraries](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html) (Vantaggi per le prestazioni del collegamento di R alle librerie matematiche multithread)

Tra le aggiunte più importanti a Microsoft R rientrano i pacchetti **RevoScaleR** e **RevoPemaR**. Si tratta di pacchetti R scritti principalmente in C o C++ per ottenere prestazioni migliori.

+ **RevoScaleR.** Include una vasta gamma di API per l'analisi e la manipolazione dei dati. Le API sono state ottimizzate per l'analisi dei set di dati troppo grandi per essere contenuti in memoria e per l'esecuzione di calcoli distribuiti su più core o processori.

   Le API RevoScaleR supportano inoltre l'uso di subset di dati per una maggiore scalabilità. In altre parole, la maggior parte delle funzioni RevoScaleR può operare su blocchi di dati e usare algoritmi di aggiornamento per aggregare i risultati. Pertanto, le soluzioni R basate sulle funzioni RevoScaleR possono essere usate con set di dati molto grandi e non sono vincolate dalla memoria locale.

  Il pacchetto RevoScaleR supporta anche il formato di file XDF per una maggiore rapidità di spostamento e archiviazione dei dati usati per l'analisi. Il formato XDF usa l'archiviazione a colonne, è portabile e può essere usato per caricare e quindi manipolare i dati da diverse origini, tra cui testo, SPSS o una connessione ODBC. 

+ **RevoPemaR.** PEMA è l'acronimo di Parallel External Memory Algorithm (algoritmo di memoria esterna parallelo). Il pacchetto **RevoPemaR** fornisce API utilizzabili per sviluppare algoritmi paralleli personalizzati. Per altre informazioni, vedere [RevoPemaR Getting Started Guide](https://docs.microsoft.com/r-server/r/how-to-developer-pemar) (Guida introduttiva a RevoPemaR).

Inoltre, è consigliabile provare [MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package), un nuovo pacchetto da Microsoft R che supporta l'esecuzione remota di codice R e scalabile, elaborazione, distribuita mediante migliorati algoritmi di machine learning sviluppato da Microsoft Research.

## <a name="next-steps"></a>Passaggi successivi

[Panoramica dell'architettura](../../advanced-analytics/r/architecture-overview-sql-server-r.md)

[Componenti di SQL Server per il supporto di R](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md)

[Panoramica della sicurezza](../../advanced-analytics/r/security-overview-sql-server-r.md)

