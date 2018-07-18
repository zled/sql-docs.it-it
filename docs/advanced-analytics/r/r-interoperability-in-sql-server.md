---
title: Interoperabilità di R in SQL Server R Services | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: da739700cabb6a9d691d5f284cd6f0532898393f
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979023"
---
# <a name="r-interoperability-in-sql-server"></a>Interoperabilità di R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo argomento illustra il meccanismo per l'esecuzione di R in SQL Server e vengono descritte le differenze tra Microsoft R e r open source.

Si applica a: SQL Server 2016 R Services, SQL Server 2017 Machine Learning Services

Per informazioni sui componenti aggiuntivi, vedere [nuovi componenti di SQL Server](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md).

### <a name="open-source-r-components"></a>Componenti R open source

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] include una distribuzione completa degli strumenti e dei pacchetti R di base. Per altre informazioni sui componenti inclusi nella distribuzione base, vedere la documentazione installata durante l'installazione nel percorso predefinito seguente: `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES\doc\manual`

Nell'ambito dell'installazione di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], è necessario accettare i termini della licenza GNU Public License. Successivamente, è possibile eseguire i pacchetti R standard senza ulteriori modifiche, esattamente come per qualsiasi altra distribuzione open source di R.

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] non modifica in alcun modo il runtime di R. Il runtime di R viene eseguito all'esterno del processo di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e può essere eseguito in modo indipendente da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Tuttavia, è consigliabile non eseguire questi strumenti mentre [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] usa R, per evitare conflitti di risorse.

La distribuzione base dei pacchetti R associata a una specifica istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] è disponibile nella cartella associata all'istanza. Ad esempio, se è installato R Services sull'istanza predefinita, le librerie R si trovano in questa cartella per impostazione predefinita:

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library

Analogamente, gli strumenti R associati all'istanza predefinita sono posizionati nella cartella corrente per impostazione predefinita:

    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin

Per altre informazioni sul modo in cui Microsoft R è diverso da una distribuzione di base di R che si potrebbero ottenere da CRAN, vedere [l'interoperabilità con linguaggio R e i prodotti Microsoft R e funzionalità](https://docs.microsoft.com/r-server/what-is-r-server-interoperability)

### <a name="additional-r-packages-from-microsoft-r"></a>Altri pacchetti R da R Microsoft

Oltre alla distribuzione base di R, [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] include alcuni pacchetti R proprietari, nonché un framework per l'esecuzione parallela di R che supporta anche l'esecuzione di R in contesti di calcolo remoti.

Questo set combinato di funzionalità R (distribuzione base di R e funzionalità e pacchetti avanzati di R) è denominato **Microsoft R**. Se si installa Microsoft R Server (Standalone), si ottiene esattamente lo stesso set di pacchetti che viene installato con SQL Server R Services (In-Database) ma in una cartella diversa.

Microsoft R include una distribuzione della libreria del kernel matematico di Intel, che viene usata quando possibile per velocizzare l'elaborazione matematica. Ad esempio, la libreria dell'algebra lineare di base (BLAS, Basic Linear Algebra) viene usata per molti dei pacchetti aggiuntivi, oltre che per R stesso. Per altre informazioni, vedere gli articoli seguenti:

+ [How the Intel Math Kernel Speeds up R](http://blog.revolutionanalytics.com/2014/10/revolution-r-open-mkl.html) (In che modo il kernel matematico di Intel velocizza R)
+ [Performance benefits of linking R to multithreaded math libraries](http://blog.revolutionanalytics.com/2010/06/performance-benefits-of-multithreaded-r.html) (Vantaggi per le prestazioni del collegamento di R alle librerie matematiche multithread)

Tra le aggiunte più importanti a Microsoft R rientrano i pacchetti **RevoScaleR** e **RevoPemaR**. Si tratta di pacchetti R scritti principalmente in C o C++ per ottenere prestazioni migliori.

+ **RevoScaleR.** Include una vasta gamma di API per l'analisi e la manipolazione dei dati. Le API sono state ottimizzate per l'analisi dei set di dati troppo grandi per essere contenuti in memoria e per l'esecuzione di calcoli distribuiti su più core o processori.

   Le API RevoScaleR supportano inoltre l'uso di subset di dati per una maggiore scalabilità. In altre parole, la maggior parte delle funzioni RevoScaleR può operare su blocchi di dati e usare algoritmi di aggiornamento per aggregare i risultati. Pertanto, le soluzioni R basate sulle funzioni RevoScaleR possono essere usate con set di dati molto grandi e non sono vincolate dalla memoria locale.

  Il pacchetto RevoScaleR supporta anche il formato di file XDF per una maggiore rapidità di spostamento e archiviazione dei dati usati per l'analisi. Il formato XDF usa l'archiviazione a colonne, è portabile e può essere usato per caricare e quindi manipolare i dati da diverse origini, tra cui testo, SPSS o una connessione ODBC. 

+ **RevoPemaR.** PEMA è l'acronimo di Parallel External Memory Algorithm (algoritmo di memoria esterna parallelo). Il pacchetto **RevoPemaR** fornisce API utilizzabili per sviluppare algoritmi paralleli personalizzati. Per altre informazioni, vedere [RevoPemaR Getting Started Guide](https://docs.microsoft.com/r-server/r/how-to-developer-pemar) (Guida introduttiva a RevoPemaR).

È consigliabile anche provare [MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package), un nuovo pacchetto di Microsoft R che supporta l'esecuzione remota del codice R, scalabile e di elaborazione, distribuita usando algoritmi di apprendimento migliorato sviluppato da Microsoft Research.

## <a name="next-steps"></a>Passaggi successivi

[Panoramica dell'architettura](../../advanced-analytics/r/architecture-overview-sql-server-r.md)

[Componenti di SQL Server per il supporto di R](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md)

[Panoramica della sicurezza](../../advanced-analytics/r/security-overview-sql-server-r.md)

