---
title: Database OLAP WideWorldImporters - utilizzo di SQL Server | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 92b842b24bc04117dad93ed1991689a1e781e828
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>WideWorldImportersDW utilizzo delle funzionalità di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
WideWorldImportersDW è progettato per illustrare molte delle funzionalità chiave di SQL Server che sono adatte per analitica e di data warehousing. Di seguito è riportato un elenco di funzionalità di SQL Server e funzionalità e una descrizione di come vengono usati in WideWorldImportersDW.

## <a name="polybase"></a>PolyBase

[Si applica a SQL Server (2016 e versioni successive)]

PolyBase è usato per combinare le informazioni di vendita da WideWorldImportersDW con un set di dati pubblico su dati demografici per capire quali città potrebbe essere di interesse per l'ulteriore espansione delle vendite.

Per abilitare l'utilizzo di PolyBase nel database di esempio, verificare che sia installato ed eseguire la stored procedure seguente nel database:

    EXEC [Application].[Configuration_ApplyPolybase]

Verrà creata una tabella esterna `dbo.CityPopulationStatistics` che fa riferimento a un set di dati pubblico che contiene i dati della popolazione per città degli Stati Uniti, ospitato nel servizio di archiviazione blob di Azure. Sono invitati a esaminare il codice della stored procedure per comprendere il processo di configurazione. Se si desidera ospitare i propri dati nell'archiviazione blob di Azure e garantirne la sicurezza dall'accesso pubblico generale, è necessario intraprendere ulteriori passaggi di configurazione. La query seguente restituisce i dati dal set di dati esterni:

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

Per comprendere quali città potrebbe essere di interesse per l'ulteriore espansione, la query seguente esamina il tasso di crescita di città e restituisce il più grandi città primi 100 con crescita significativa, e in Wide World Importers non dispone di una presenza delle vendite. La query implica un join tra la tabella remota `dbo.CityPopulationStatistics` e la tabella locale `Dimension.City`e un filtro che interessano la tabella locale `Fact.Sales`.

    WITH PotentialCities
    AS
    (
        SELECT cps.CityName,
               cps.StateProvinceCode,
               MAX(cps.LatestRecordedPopulation) AS PopulationIn2016,
               (MAX(cps.LatestRecordedPopulation) - MIN(cps.LatestRecordedPopulation)) * 100.0
                   / MIN(cps.LatestRecordedPopulation) AS GrowthRate
        FROM dbo.CityPopulationStatistics AS cps
        WHERE cps.LatestRecordedPopulation IS NOT NULL
        AND cps.LatestRecordedPopulation <> 0
        GROUP BY cps.CityName, cps.StateProvinceCode
    ),
    InterestingCities
    AS
    (
        SELECT DISTINCT pc.CityName,
                        pc.StateProvinceCode,
                        pc.PopulationIn2016,
                        FLOOR(pc.GrowthRate) AS GrowthRate
        FROM PotentialCities AS pc
        INNER JOIN Dimension.City AS c
        ON pc.CityName = c.City
        WHERE GrowthRate > 2.0
        AND NOT EXISTS (SELECT 1 FROM Fact.Sale AS s WHERE s.[City Key] = c.[City Key])
    )
    SELECT TOP(100) CityName, StateProvinceCode, PopulationIn2016, GrowthRate
    FROM InterestingCities
    ORDER BY PopulationIn2016 DESC;

## <a name="clustered-columnstore-indexes"></a>Indici columnstore cluster

(Versione completa dell'esempio)

Gli indici di Columnstore cluster (CCI) vengono utilizzati con tutte le tabelle dei fatti per ridurre il footprint di memoria e migliorare le prestazioni delle query. Con l'utilizzo dell'indice ColumnStore cluster, l'archiviazione di base per le tabelle dei fatti Usa la compressione della colonna.

Gli indici non cluster vengono utilizzati nella parte superiore dell'indice columnstore cluster, per facilitare la chiave primaria e vincoli di chiave esterna. Questi vincoli sono stati aggiunti da una varietà di attenzione: il processo ETL origini dati dal database WideWorldImporters, che presenta vincoli di integrità. Rimozione di vincoli di chiavi primarie ed esterne e i relativi indici di supporto, consentirebbe di ridurre il footprint di memoria delle tabelle dei fatti.

**Dimensioni dei dati**

Il database di esempio in modo limitato le dimensioni dei dati, per consentire un facile scaricare e installare l'esempio. Tuttavia, per visualizzare i vantaggi reali prestazioni degli indici columnstore, si desidera utilizzare un set di dati più grande.

È possibile eseguire l'istruzione seguente per aumentare le dimensioni del `Fact.Sales` tabella tramite l'inserimento di un altro 12 milioni di righe di dati di esempio. Queste sono tutte inserite righe per l'anno 2012, tali da non interferire con il processo ETL.

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

Questa istruzione richiederà circa 5 minuti per l'esecuzione. Per inserire più di 12 milioni di righe, passare il numero desiderato di righe da inserire come parametro per questa stored procedure.

Per confrontare le prestazioni delle query con e senza columnstore, è possibile eliminare e/o ricreare l'indice columnstore cluster.

Per eliminare l'indice:

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

Per ricreare:

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>Partizionamento

(Versione completa dell'esempio)

Dimensioni dei dati in un Data Warehouse possono diventare molto grande. È pertanto consigliabile utilizzare il partizionamento per gestire l'archiviazione delle tabelle nel database di grandi dimensioni.

Tutte le tabelle dei fatti più grandi vengono partizionate per anno. L'unica eccezione è `Fact.Stock Holdings`, che non è basato su data e l'ha dimensioni di dati limitati confrontato con le altre tabelle dei fatti.

La funzione di partizione utilizzata per le tabelle partizionate tutti `PF_Date`, e viene utilizzato lo schema di partizione è `PS_Date`.

## <a name="in-memory-oltp"></a>OLTP in memoria

(Versione completa dell'esempio)

WideWorldImportersDW utilizza le tabelle con ottimizzazione per la memoria SCHEMA_ONLY per le tabelle di gestione temporanea. Tutti `Integration.` * `_Staging` sono tabelle con ottimizzazione per la memoria SCHEMA_ONLY.

Il vantaggio di tabelle SCHEMA_ONLY è che non vengono registrate e non richiedono alcun accesso al disco. Ciò migliora le prestazioni del processo ETL. Poiché queste tabelle non vengono registrate, i relativi contenuti vengono perduti se si è verificato un errore. Tuttavia, l'origine dati è ancora disponibile, quindi è possibile riavviare il processo ETL semplicemente se si verifica un errore.
