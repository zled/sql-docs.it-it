---
title: Load
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: È possibile caricare o inserire dati in SQL Server Parallel Data Warehouse (PDW) con Integration Services, utilità bcp, dwloader o l'istruzione SQL INSERT.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: c7292108-4a48-409e-b0f4-e4ba84dce26f
caps.latest.revision: 22
ms.openlocfilehash: 77bb7e3ba6a3377fe63decf06a872872eaa4ee61
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="load-sql-server-pdw"></a>Caricare (SQL Server PDW)
È possibile caricare o inserire dati in SQL Server Parallel Data Warehouse (PDW) con Integration Services, [utilità bcp](../tools/bcp-utility.md), **dwloader** caricatore della riga di comando o l'istruzione SQL INSERT.  

## <a name="loading-environment"></a>Il caricamento di ambiente  
Per caricare i dati, è necessario uno o più server di caricamento. È possibile utilizzare la propria ETL esistenti o ad altri server o è possibile acquistare nuovi server. Per ulteriori informazioni, vedere [acquisire e configurare un Server durante il caricamento](acquire-and-configure-loading-server.md). Queste istruzioni includono un [caricamento capacità pianificazione foglio di lavoro Server](loading-server-capacity-planning-worksheet.md) per pianificare la soluzione ideale per il caricamento.  
  
## <a name="load-with-dwloader"></a>Caricare con dwloader  
Utilizzo di [dwloader caricatore della riga di comando](dwloader.md) è il modo più rapido per caricare dati in PDW.  
  
![Processo di caricamento](media/loading-process.png "processo di caricamento")  
  
dwloader carica i dati direttamente ai nodi di calcolo senza passare i dati tramite il nodo di controllo. Per caricare i dati, dwloader comunica con il nodo di controllo per ottenere informazioni di contatto per i nodi di calcolo. dwloader configura un canale di comunicazione a ogni nodo di calcolo e quindi invia i blocchi di 256KB di dati per i nodi di calcolo in modo round robin.  
  
In ogni nodo di calcolo, servizio lo spostamento dei dati (DMS) riceve ed elabora blocchi di dati. L'elaborazione dei dati include la conversione di ogni riga in formato nativo di SQL Server e il calcolo dell'hash di distribuzione per determinare il nodo di calcolo a cui appartiene ogni riga.  
  
Dopo l'elaborazione delle righe, DMS usa uno spostamento casuale per il trasferimento di ogni riga per il corretto del nodo di calcolo e l'istanza di SQL Server. Come SQL Server riceve le righe, li inserisce in batch in base al **– b** imposta il parametro batch size in dwloader e quindi il caricamento bulk il batch.  

## <a name="load-with-prepared-statements"></a>Caricamento con le istruzioni preparate

È possibile utilizzare le istruzioni preparate per caricare dati in tabelle replicate e distribuite. Quando i dati di input non corrisponde al tipo di dati di destinazione, viene eseguita una conversione implicita. Le conversioni implicite supportate da PDW istruzioni preparate sono un subset delle conversioni supportate da SQL Server. Vale a dire, sono supportati solo un subset di conversioni, ma le conversioni supportate corrispondano le conversioni implicite di SQL Server. Indipendentemente dal fatto che la tabella di destinazione deve essere caricata è definita come una tabella replicata o distribuita, le conversioni implicite vengono applicate a tutte le colonne esistenti nella tabella di destinazione (se necessario). 

<!-- MISSING LINK
For more information, see [Prepared statements](prepared-statements.md).
-->
  
## <a name="related-tasks"></a>Attività correlate  
  
|Attività|Description|  
|--------|---------------|  
|Creare il database di gestione temporanea.|[Creare il database di gestione temporanea](staging-database.md)|  
|Caricamento con Integration Services.|[Caricare con Integration Services](load-with-ssis.md)|  
|Comprendere le conversioni di tipo per dwloader.|[Regole di conversione del tipo di dati per dwloader](dwloader-data-type-conversion-rules.md)|  
|Caricare i dati con dwloader.|[dwloader caricatore della riga di comando](dwloader.md)|  
|Comprendere le conversioni di tipi per l'inserimento.|[Caricare i dati con INSERT](load-with-insert.md)|  
 
<!-- MISSING LINKS
## See Also  
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Common metadata query examles](metadata-query-examples.md)  
  
-->
