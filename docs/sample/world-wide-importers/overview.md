---
title: Panoramica | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 01/30/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4dcb00-b93e-44db-9d67-061702bba41a
caps.latest.revision: 3
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: f4d22aada117e3230e36aa52e911f31eea53439e
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2018
---
# <a name="wide-world-importers-overview"></a>Panoramica di Wide World Importers
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Questa è una panoramica della società fittizia Wide World Importers e i flussi di lavoro che vengono affrontati nel database di esempio WideWorldImporters per SQL Server e Database SQL di Azure.  

Wide World Importers (WWI) è un importatore di merci originalità all'ingrosso e operativo dall'area di San Francisco alloggiamenti server di distribuzione.

Come un ingrosso, i clienti del WWI sono principalmente le aziende che rivendono per utenti singoli. WWI vende ai clienti di vendita al dettaglio degli Stati Uniti inclusi archivi di specializzazione, supermercati, calcolo negozi, negozi attrazione turistica e alcune persone. WWI vende anche per altri grossisti tramite una rete di agenti che i prodotti per conto del WWI alzare di livello. Mentre tutti i clienti del WWI attualmente si basano negli Stati Uniti, la società non sia progettata per eseguire il push per l'espansione in altri paesi.

WWI acquista prodotti da fornitori inclusi originalità e produttori giocattoli e altri grossisti originalità. Le merci nella loro WWI warehouse e il riordino di fornitori sono predefinite in base alle esigenze per soddisfare gli ordini dei clienti. Sono anche acquistare volumi elevati di creazione del pacchetto materiali e vendere in piccole quantità per maggiore praticità dei clienti.

Recentemente WWI avviato per la vendita di un'ampia gamma di commestibili novità, ad esempio derivati cioccolatini.  La società in precedenza non conteneva gestire gli elementi raffreddati. A questo punto, per soddisfare trattamento requisiti di prodotti alimentari, devono monitorare la temperatura in loro spazio Scambiatore refrigerante e le loro Van contenenti sezioni Scambiatore refrigerante.

## <a name="workflow-for-warehouse-stock-items"></a>Flusso di lavoro per articoli di scorte di magazzino

Il flusso tipico di elementi sono immagazzinati e distribuiti è il seguente:
- WWI crea gli ordini di acquisto e invia gli ordini per i fornitori.
- Gli elementi di trasmissione fornitori, WWI li riceve e li titoli nel loro warehouse.
- I clienti ordinano gli elementi da WWI
- WWI viene compilato l'ordine del cliente con le voci del warehouse e quando non hanno scorte sufficienti, le azioni aggiuntive vengono ordinati da fornitori.
- Alcuni clienti non desidera attendere che gli elementi che non sono in magazzino. Se vengono ordinati ad esempio cinque diverse e quattro le voci sono disponibili, che desiderano ricevere ordini arretrati rimanenti articolo le quattro elementi. L'elemento viene loro inviati più avanti in una spedizione separata.
- I clienti per gli elementi predefiniti, le fatture in genere WWI convertendo l'ordine in una fattura.
- I clienti potrebbero ordinare gli elementi che non sono in magazzino. Questi elementi sono inevasa.
- WWI forniscono le voci ai clienti tramite i propri furgoni o tramite altri mezzi di trasporto o i metodi di trasporto.
- I clienti pagano le fatture per WWI.
- Periodicamente, WWI paga fornitori per gli elementi presenti negli ordini di acquisto. Ciò è spesso un po' dopo avere ricevuto le merci.

## <a name="data-warehouse-and-analysis-workflow"></a>Flusso di lavoro Data Warehouse e analisi

Mentre il team WWI utilizza SQL Server Reporting Services per generare i report operativi dal database WideWorldImporters, anche dovranno eseguire analitica dei dati e per generare report strategica. Il team di aver creato un modello di dati multidimensionali in un database WideWorldImportersDW. Questo database viene popolato da un pacchetto di Integration Services.

SQL Server Analysis Services viene utilizzato per creare modelli di dati analitici da dati nel modello di dati multidimensionali. SQL Server Reporting Services viene utilizzato per generare report strategico direttamente dal modello di dati multidimensionali, nonché dal modello analitico. Power BI è possibile creare dashboard con gli stessi dati. I dashboard vengono utilizzati nei siti Web e ai telefoni e Tablet. *Nota: questi modelli di dati e i report non sono ancora disponibili*

## <a name="additional-workflows"></a>Flussi di lavoro aggiuntivi

Questi sono flussi di lavoro aggiuntive.
- Note sulla carta di credito problemi WWI quando un cliente non riceve il bene per qualche motivo, o quando le merci sono difettosi. Questi sono considerati fatture negativo.
- WWI conta periodicamente le quantità di scorte di articoli predefinite per assicurarsi che la quantità di scorte indicata come disponibile nel sistema siano corretti. (Il processo di questa operazione è detta un stocktake).
- Fredde temperature chat. Prodotti deperibili vengono archiviati nella chat room gas. Nel database per scopi di monitoraggio e analitica vengono acquisiti i dati del sensore da tali locali.
- Rilevamento del percorso Vehicle. Veicoli che trasportano le merci per WWI includono che tiene traccia del percorso. Questo percorso verrà acquisito nuovamente nel database per il monitoraggio e ulteriormente analitica.

## <a name="fiscal-year"></a>Anno fiscale

L'azienda opera con un esercizio che inizia il 1 ° novembre.

## <a name="terms-of-use"></a>Condizioni di utilizzo

La licenza per il database di esempio e il codice di esempio descritto di seguito: [License. txt](https://github.com/Microsoft/sql-server-samples/blob/master/license.txt)

Il database di esempio include dati pubblici che sono stati caricati dal data.gov ed EarthData naturale. In questa sezione sono riportate le condizioni di utilizzo: [http://www.naturalearthdata.com/about/terms-of-use/](http://www.naturalearthdata.com/about/terms-of-use/)
