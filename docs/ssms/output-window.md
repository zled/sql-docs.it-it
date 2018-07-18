---
title: Finestra di output di SSMS | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Output Window [SQL Server Management Studio]
- Activity Monitor [SQL Server Management Studio]
- Object Explorer [SQL Server Management Studio]
ms.assetid: a2ce1a07-b4e2-471c-87d2-b8de5e6c6864
caps.latest.revision: 1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eb4b9425edb8ba72ee56e98f8f028d8f44b1b7ff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33042018"
---
# <a name="output-window-in-sql-server-management-studio"></a>Finestra di output in SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
La finestra di output può essere aperta dal menu Visualizza o tramite la combinazione di tasti CTRL+ALT+O. Sono disponibili più canali di output.

La tabella seguente fornisce una panoramica dei tipi di messaggi associati a ogni canale di output.

|Channel|Description|
|-----------|---------------|  
|**Telemetria**|La telemetria è il flusso di [dati di utilizzo delle funzionalità anonimi](sql-server-management-studio-ssms.md) raccolti da Microsoft. Questi eventi possono risultare utili per tenere traccia dell'utilizzo di SSMS. Possono consentire di identificare i nodi di Esplora oggetti espansi e i comandi eseguiti durante la sessione di SSMS con la finestra di output aperta.|
|**Visualizza**|Questo canale restituisce il testo delle query e il tempo trascorso per le query SQL necessarie per espandere nodi in Esplora oggetti. Ogni query registra un evento Inizio query e Fine query. Ogni evento ha un timestamp e un URN associato all'entità sottoposta a query. Il valore [URN](https://technet.microsoft.com/library/microsoft.sqlserver.management.smo.urn(v=sql.90).aspx) fa riferimento all'oggetto SQL Management sottostante ed è costituito da una gerarchia di tipo XPath. Il valore URN per una tabella denominata "Table1" nel database "Db" in server "MyServer", ad esempio, sarà "Server[@Name='MyServer']/Database[@Name='Db']/Table[/@Name='Table1']".  L'espansione di un nodo in Esplora oggetti può consentire di eseguire più query di questo tipo con parametri diversi. L'evento Fine query conterrà il tempo trascorso della query e il testo TSQL. I dati relativi alle query possono essere utili per l'analisi delle prestazioni dei server nei casi in cui l'espansione di un nodo specifico in Esplora oggetti risulta insolitamente lenta. **Nota**: non tutti i nodi in Esplora oggetti forniscono questo livello di dettaglio di query in caso di espansione.|
|**Monitoraggio attività**|Questo canale viene attivato all'[apertura del Monitoraggio attività](https://docs.microsoft.com/en-us/sql/relational-databases/performance-monitor/activity-monitor) per un server. Questo flusso contiene eventi che mostrano una parte del testo della query e del timestamp di ogni query, messaggi di errore e notifiche relative alla sospensione del monitoraggio a causa di problemi di connettività. Se Monitoraggio attività risulta inattivo o non si aggiorna, controllare questo canale di output per ottenere altre informazioni.|





