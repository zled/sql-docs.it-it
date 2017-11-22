---
title: Architettura | Documenti Microsoft
ms.custom: 
ms.date: 11/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 1dcde96872f391d1be312c5b8ff9bd8c2dd7a479
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="architecture-overview-for-machine-learning-services-with-python"></a>Panoramica dell'architettura per i servizi di Machine Learning con Python

In questo argomento viene fornita una panoramica di come Python è integrato con SQL Server, tra cui il modello di sicurezza, i componenti motore di database che supportano l'esecuzione dello script esterno e nuovi componenti che consentono l'interoperabilità di Python con SQL Server. Per informazioni dettagliate, vedere gli argomenti collegati.

> [!IMPORTANT]
> Supporto per Python è disponibile a partire da SQL Server 2017 CTP 2.0. Questa funzionalità non definitiva è soggetta a modifiche.

## <a name="python-interoperability"></a>Interoperabilità di Python

Consente di installare SQL Server Machine Learning Services (In-Database) la distribuzione Anaconda di Python e il runtime di Python 3.5 e l'interprete. In questo modo quasi completa compatibilità con le soluzioni di Python standard. Python viene eseguito in un processo separato dal Server SQL, per garantire che le operazioni di database non vengano compromesse.

Per ulteriori informazioni sull'interazione di SQL Server con Python, vedere [interoperabilità Python](../../advanced-analytics/python/python-interoperability.md)

## <a name="components-that-support-python-integration"></a>Componenti che supportano l'integrazione di Python

Il framework di estendibilità introdotto in SQL Server 2016 ora supporta l'esecuzione di uno script Python, mediante l'aggiunta di nuovi componenti linguistici. Questi componenti migliorare la velocità di scambio di dati e la compressione, fornendo una piattaforma sicura e ad alte prestazioni per l'esecuzione di script esterni.

Per una descrizione dettagliata dei componenti che supportano Python, ad esempio il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] e PythonLauncher, vedere [nuovi componenti](../../advanced-analytics/python/new-components-in-sql-server-to-support-python-integration.md).

## <a name="security"></a>Security

Le attività di Python vengono eseguite all'esterno del processo di SQL Server, per fornire sicurezza e maggiore facilità di gestione.

Tutte le attività sono protette mediante gli oggetti processo di Windows o di sicurezza di SQL Server. Dati viene mantenuti all'interno del limite di conformità per l'imposizione della sicurezza di SQL Server a livello di istanza, database e tabella. L'amministratore del database è possibile controllare chi ha la possibilità di eseguire i processi di Python, monitorare l'utilizzo di script Python da parte degli utenti e visualizzare le risorse utilizzate.

Per informazioni dettagliate, vedere [sicurezza per Python](../../advanced-analytics/python/security-overview-sql-server-python-services.md)

## <a name="resource-governance"></a>Governance delle risorse

In SQL Server Enterprise Edition, è possibile utilizzare Resource Governor per gestire e monitorare l'utilizzo delle risorse di operazioni di script esterni, inclusi script di R e gli script Python.

Per ulteriori informazioni, vedere [governance delle risorse per R](../../advanced-analytics/r/resource-governance-for-r-services.md).

## <a name="next-steps"></a>Passaggi successivi

[Eseguire Python con T-SQL](../tutorials/run-python-using-t-sql.md)
