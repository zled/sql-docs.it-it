---
title: Panoramica dell'architettura di supporto del linguaggio R in SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3784fe62669b3f6d29e94bea799e19f9eadad5f0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="architecture-overview-for-r-in-sql-server"></a>Panoramica dell'architettura di R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa sezione viene fornita una panoramica dell'architettura di SQL Server 2016 R Services e di servizi di SQL Server 2017 Machine Learning.

L'architettura per l'architettura di estendibilità è lo stesso o molto simili per SQL Server 2016 e versioni SQL Server 2017 e lo stesso vale anche per R e Python. Tuttavia, per semplificare la discussione, questo articolo illustra solo i componenti di R, inclusi nuovi componenti aggiunti nel motore di database di SQL Server per supportare l'esecuzione dello script esterno, sicurezza, le librerie di R e interoperabilità con open source di R.

Dettagli aggiuntivi vengono forniti i collegamenti per ogni sezione.

## <a name="r-interoperability"></a>Interoperabilità di R

Sia SQL Server 2016 R Services e SQL Server 2017 Machine Learning Services (In-Database) è possibile installare una distribuzione open source di R, nonché i pacchetti forniti da Microsoft che supportano l'elaborazione distribuita e/o parallela.

L'architettura è progettata in modo che gli script esterni usando R eseguiti in un processo separato da SQL Server. Gli utenti correnti di R devono poter trasferire il proprio codice R ed eseguirlo in T-SQL con modifiche relativamente minime.

Per ridimensionare la soluzione o utilizzare l'elaborazione parallela, è consigliabile utilizzare il [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) pacchetto o [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package) pacchetto. Se non si utilizzano le capacità di elaborazione distribuite fornite da queste librerie, è comunque possibile ottenere alcuni miglioramenti delle prestazioni eseguendo codice R nel contesto di SQL Server.

Per ulteriori informazioni sui componenti script esterni che vengono installati o l'interazione di SQL Server con R, vedere [interoperabilità R](../../advanced-analytics/r/r-interoperability-in-sql-server.md)

## <a name="components-to-support-r-integration"></a>Componenti per supportare l'integrazione di R

Il framework di estendibilità introdotto in SQL Server 2016 continua in SQL Server 2017. I componenti di estendibilità vengono utilizzati da SQL Server per avviare il runtime di R, per passare dati tra R e il motore di database e per coordinare le attività in parallelo necessari per un processo R esterno.

Il ruolo di questi componenti aggiuntivi consiste nel migliorare la velocità di scambio di dati e la compressione, fornendo una piattaforma sicura e ad alte prestazioni per l'esecuzione di script esterni.

Per una descrizione dettagliata dei componenti che supportano R, ad esempio il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] e RLauncher, vedere [nuovi componenti](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md).

## <a name="security"></a>Sicurezza

Quando si esegue codice R con Machine Learning Services o SQL Server R Services, tutti gli script R vengono eseguiti all'esterno del processo di SQL Server, per fornire sicurezza e maggiore facilità di gestione. L'isolamento dei processi vale indipendentemente dal fatto se è eseguire lo script R come parte di una stored procedure, o connettersi al processo di computer SQL Server da un computer remoto e avviare un processo che utilizza il server come contesto di calcolo.

SQL Server intercetta tutte le richieste di processo, protegge l'attività e i relativi dati tramite gli oggetti processo Windows e garantisce la sicurezza dei dati con gli account utente di SQL Server e ruoli del database.

Dati viene mantenuti all'interno del limite di conformità per l'imposizione della sicurezza di SQL Server a livello di istanza, database e tabella. L'amministratore del database è possibile controllare chi ha la possibilità di eseguire processi R e chi ha la possibilità di installare o condividere i pacchetti R. L'amministratore può inoltre monitorare l'utilizzo di script R da parte degli utenti remoti o locali e monitorare e gestire le risorse utilizzate.

## <a name="next-steps"></a>Passaggi successivi

[Componenti che supportano l'integrazione di R](new-components-in-sql-server-to-support-r.md)

[Interoperabilità di R](r-interoperability-in-sql-server.md)

[Panoramica della sicurezza](security-overview-sql-server-r.md)
