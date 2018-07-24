---
title: Scaricare SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 07/02/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology: ssdt
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- installare ssdt, scaricare ssdt, versione più recente di ssdt
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 78eb769a8f37ca055628a89aeebe7dd444673434
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37988223"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Scaricare e installare SQL Server Data Tools (SSDT) per Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
**SQL Server Data Tools** è uno strumento di sviluppo moderno che consente di compilare database relazionali SQL Server, database SQL di Azure, modelli di dati di Analysis Services (AS), pacchetti di Integration Services (IS) e report di Reporting Services (RS). Con SSDT è possibile progettare e distribuire qualsiasi tipo di contenuto SQL Server con la stessa facilità con la quale si sviluppa un'applicazione in Visual Studio.

*Per la maggior parte degli utenti, SQL Server Data Tools (SSDT) viene installato durante l'installazione di Visual Studio. Se si installa SSDT usando il programma di installazione di Visual Studio, vengono aggiunte le funzionalità SSDT di base. È pertanto necessario eseguire il [programma di installazione di SSDT autonomo](#ssdt-for-vs-2017-standalone-installer) per ottenere AS, IS ed RS.*

## <a name="install-ssdt-with-visual-studio-2017"></a>Installare SSDT con Visual Studio 2017

Per installare SSDT durante l'[installazione di Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio), selezionare il carico di lavoro **Elaborazione ed archiviazione dati** e quindi selezionare **SQL Server Data Tools**. Se Visual Studio è già installato, è possibile [modificare l'elenco dei carichi di lavoro](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) per includere SSDT: ![Carico di lavoro Elaborazione ed archiviazione dati](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)



## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Installare Analysis Services, Integration Services e Reporting Services
Per installare AS, IS ed RS come supporto per i progetti, eseguire il [programma di installazione di SSDT autonomo](#ssdt-for-vs-2017-standalone-installer). 

Il programma di installazione elenca le istanze di Visual Studio disponibili per l'aggiunta degli strumenti di SSDT. Se Visual Studio non è installato, selezionando **Install a new SQL Server Data Tools instance** (Installa una nuova istanza di SQL Server Data Tools) è possibile installare SSDT con una versione minima di Visual Studio. Per un'esperienza ottimale, tuttavia, è consigliabile usare SSDT con [la versione più recente di Visual Studio](https://www.visualstudio.com/downloads). 

![Selezionare AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT per Visual Studio 2017 (programma di installazione autonomo)

[![download](../ssdt/media/download.png) Download di SSDT per Visual Studio 2017 (15.7.1) ](https://go.microsoft.com/fwlink/?linkid=875613) 

> [!IMPORTANT]
> - Prima di installare SSDT per Visual Studio 2017 (15.7.1), disinstallare le estensioni *Progetti di Analysis Services* e *Progetti di Reporting Services*, se già installate, e chiudere tutte le istanze di Visual Studio.
> - Quando si installa SSDT in Windows 10 e si sceglie **Installare la nuova istanza di Microsoft SQL Server Data Tools per Visual Studio 2017**, prima deselezionare tutte le caselle di controllo e installare la nuova istanza. Dopo aver installato la nuova istanza, riavviare il computer e aprire di nuovo il programma di installazione di SSDT per continuare l'installazione.  



**Informazioni sulla versione**  
  
Numero di versione: 15.7.1  
Numero di build: 14.0.16167.0  
Data di rilascio: 02 luglio 2018  

Per un elenco completo delle modifiche, vedere il [log delle modifiche](changelog-for-sql-server-data-tools-ssdt.md).

SSDT per Visual Studio 2017 ha gli stessi [requisiti di sistema](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs) di Visual Studio.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Lingue disponibili - SSDT per VS 2017

Questa versione di **SSDT per VS 2017** può essere installata nelle lingue seguenti:  

[Cinese (Repubblica popolare cinese)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x804) | 
[Cinese (Taiwan)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x404) | 
[Inglese (Stati Uniti)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x409) | 
[Francese]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x40c)  
[Tedesco]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x407) | 
[Italiano]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x410) | 
[Giapponese]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x411) | 
[Coreano]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x412) | 
[Portoghese (Brasile)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x416) | 
[Russo]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x419) | 
[Spagnolo]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x40a)  



## <a name="ssdt-for-vs-2015-standalone-installer"></a>SSDT per Visual Studio 2015 (programma di installazione autonomo)

[![download](../ssdt/media/download.png) Download di SSDT per Visual Studio 2015 (17.4)](https://go.microsoft.com/fwlink/?linkid=863440)

**Informazioni sulla versione**  
  
Numero di versione: 17.4

Numero di build per questa versione: 14.0.61712.050
  
Per un elenco completo delle modifiche, vedere il [log delle modifiche](changelog-for-sql-server-data-tools-ssdt.md).

### <a name="available-languages---ssdt-for-vs-2015"></a>Lingue disponibili - SSDT per VS 2015
  
Questa versione di **SSDT per VS 2015** può essere installata nelle lingue seguenti:  

[Cinese (Repubblica popolare cinese)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x804) | 
[Cinese (Taiwan)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x404) | 
[Inglese (Stati Uniti)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x409) | 
[Francese]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x40c)  
[Tedesco]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x407) | 
[Italiano]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x410) | 
[Giapponese]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x411) | 
[Coreano]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x412) | 
[Portoghese (Brasile)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x416) | 
[Russo]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x419) | 
[Spagnolo]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x40a)  

### <a name="iso-images---ssdt-for-vs-2015"></a>Immagini ISO - SSDT per VS 2015

Un'immagine ISO di SSDT può essere utilizzata come metodo alternativo per installare SSDT o configurare un punto di installazione amministrativa. L'immagine ISO è un file autonomo che contiene tutti i componenti richiesti da SSDT e può essere scaricata mediante un gestore download ripristinabile, utile nei casi di larghezza di banda della rete limitata o meno affidabile. Una volta scaricata, l'immagine ISO può essere montata come unità o masterizzata su un DVD.

> [!NOTE]
> Le immagini ISO di SSDT per VS 2015 17.4 sono ora disponibili.

[Cinese (Repubblica popolare cinese)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x804) |
[Cinese (Taiwan)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x404) |
[Inglese (Stati Uniti)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x409) |
[Francese]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x40c)  
[Tedesco]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x407) |
[Italiano]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x410) |
[Giapponese]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x411) |
[Coreano]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x412) |
[Portoghese (Brasile)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x416) |
[Russo]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x419) |
[Spagnolo]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x40a)



## <a name="supported-sql-versions"></a>Versioni di SQL supportate
  
|Modelli di progetto|Piattaforme SQL supportate|  
|-------------------|--------------------|  
Database relazionali|  SQL Server 2005* - SQL Server 2017<br> (usare SSDT 17.x o SSDT per Visual Studio 2017 per la connessione a [SQL Server in Linux](../linux/sql-server-linux-overview.md))<br /><br />Database SQL di Azure<br /><br />Azure SQL Data Warehouse (supporta solo query, i progetti di database non sono ancora supportati)<br /><br />  * Il supporto per SQL Server 2005 è deprecato<br /><br /> e si consiglia di passare a una versione di SQL supportata ufficialmente|
  |Modelli di Analysis Services<br /><br />Report di Reporting Services | SQL Server 2008 - SQL Server 2017|
  |pacchetti di Integration Services| SQL Server 2012 - SQL Server 2017    |
  
## <a name="dacfx"></a>DacFx
SSDT per Visual Studio 2015 e SSDT per Visual Studio 2017 usano entrambi DacFx 17.4.1: [scaricare Data-Tier Application Framework (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).


## <a name="next-steps"></a>Passaggi successivi  
Dopo l'installazione di SSDT, consultare queste esercitazioni per imparare a creare database, pacchetti, modelli di dati e report mediante SSDT:  

- [Sviluppo di database offline orientato ai progetti](project-oriented-offline-database-development.md)  
- [Esercitazione SSIS: Creare un pacchetto ETL semplice](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Esercitazioni su Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
- [Creare un report tabella semplice (esercitazione su SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]


## <a name="see-also"></a>Vedere anche  
[Forum MSDN di SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog del Team di SSDT](http://blogs.msdn.com/b/ssdt/)  
[Riferimento all'API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  