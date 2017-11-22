---
title: Utilizzando i dati di cubi OLAP in R | Documenti Microsoft
ms.custom: 
ms.date: 11/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 1c55a5b834cd91478a87ded7ebb86884117c7bfb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="using-data-from-olap-cubes-in-r"></a>Utilizzando i dati di cubi OLAP in R

Il **olapR** pacchetto è un pacchetto R, fornito da Microsoft per l'utilizzo con Machine Learning Server e SQL Server R Services, che consente di eseguire query MDX per ottenere dati dai cubi OLAP. Con questo pacchetto, è necessario creare server collegati o pulire i set di righe bidimensionali; è possibile utilizzare dati OLAP direttamente in R.

In questo articolo viene descritta l'API, insieme a una panoramica fo OLAP e MDX per gli utenti di R che potrebbero essere nuovi per database di cubi multidimensionali.

## <a name="what-is-an-olap-cube"></a>Che cos'è un cubo OLAP?

OLAP è l'abbreviazione di elaborazione analitica in linea. Soluzioni OLAP vengono ampiamente utilizzate per l'acquisizione e l'archiviazione di dati aziendali critici nel tempo. I dati OLAP vengono utilizzati per l'analisi aziendale da un'ampia gamma di strumenti, dashboard e visualizzazioni. Per ulteriori informazioni, vedere [elaborazione analitica in linea](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft fornisce [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services), che consente di progettare, distribuire e query dei dati OLAP sotto forma di _cubi_ o _modelli tabulari_. Un cubo è un database multidimensionale. _Dimensioni_ equivalgono facet dei dati, o fattori di r: utilizzare le dimensioni per identificare un sottoinsieme specifico di dati che si desidera riepilogare o analizzare. Ad esempio, ora è una dimensione importante, tanta in modo che molte soluzioni OLAP includono più calendari definiti per impostazione predefinita, da utilizzare durante il sezionamento e riepilogare i dati. 

Per motivi di prestazioni, un database OLAP calcola spesso riepiloghi (o _aggregazioni_) in anticipo e quindi li archivia per il recupero veloce. Si basano *misure*, che rappresentano le formule che possono essere applicate ai dati numerici. Utilizzare le dimensioni per definire un subset di dati e quindi calcolare la misura i dati. Ad esempio, utilizzare una misura per calcolare le vendite totali per una determinata riga prodotto più trimestri meno imposte per segnalare i costi di spedizione medio per un particolare fornitore, year-to-date cumulativo Salari a pagamento e così via.

MDX, abbreviazione di espressioni MDX, è il linguaggio utilizzato per eseguire query sui cubi. Una query MDX in genere contiene una definizione di dati che include una o più dimensioni e almeno una misura, le query MDX thogh possono ottenere notevolmente più complesse e includono windows cumulative medie o somme, percentili in sequenza. 

Ecco alcuni altri termini che potrebbero essere utili quando si avvia la creazione di query MDX:

+ *Il sezionamento* accetta un subset del cubo utilizzando i valori da una singola dimensione.

+ *Estrazione* crea un sottocubo specificando un intervallo di valori in più dimensioni.

+ *Drill-down* passa da un riepilogo alle informazioni dettagliate.

+ *Drill-up* passa dalle informazioni dettagliate a un livello superiore di aggregazione.

+ *Rollup* riepiloga i dati in una dimensione.

+ *Pivot* ruota il cubo o la selezione di dati.

Questo argomento vengono fornite ulteriori esempi di sintassi di base per le query su un cubo: 

+ [Come creare query MDX con R](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapR API

Il pacchetto **olapR** supporta due metodi per la creazione di query MDX:

- **Utilizzare il Generatore MDX.** Utilizzare le funzioni R nel pacchetto per generare una semplice query MDX, scegliendo un cubo e assi di impostazione e i filtri dei dati. Questo è un modo semplice per compilare una query MDX valida se non si dispone dell'accesso agli strumenti OLAP tradizionali o non dispone di una profonda conoscenza del linguaggio MDX.

    Non tutte le query MDX possono essere create utilizzando questo metodo, poiché MDX può essere complessa. Tuttavia, questa API supporta la maggior parte delle operazioni più comuni e utili, incluso dimensioni N sezione dice, drill-down, rollup e pivot.

+ **Copiare e incollare il MDX ben formato.** Creare manualmente e quindi incollare in qualsiasi query MDX. Questa opzione è la migliore se sono presenti query MDX esistente che si desidera riutilizzare o se si desidera compilare query è troppo complessa per **olapR** di gestire. 

    Compilare il codice MDX tramite le utilità client, ad esempio SQL Server Management Studio o Excel e quindi salvare la stringa che definisce la query MDX. Questa stringa MDX è fornire come argomento per il *gestore query SSAS* nel **olapR** pacchetto. La funzione Invia la query al server Analysis Services specificato e passa nuovamente i risultati a R, presupponendo che si dispone delle autorizzazioni necessarie per eseguire query sul cubo naturalmente.

Per esempi di come compilare un MDX query oppure eseguire una query MDX esistente, vedere [come creare query MDX utilizzando R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Problemi noti

### <a name="tabular-models-not-supported"></a>Modelli tabulari non supportati

+ Se ci si connette a un'istanza tabulare di Analysis Services, il `explore` funzione segnala l'esito positivo con valore restituito true. Tuttavia, gli oggetti del modello tabulare non sono un tipo compatibile e non possono essere esplorati.

+ I modelli tabulari possono essere eseguiti utilizzando DAX o MDX. Se si progetta una query MDX valida su un modello tabulare utilizzando uno strumento esterno e quindi incollarla la query in questa API, la query restituisce un risultato NULL e non segnala un errore.

## <a name="resources"></a>Risorse

Se non si ha familiarità con OLAP o le query MDX, vedere questi articoli di Wikipedia: [Cubo OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
[Query MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)

### <a name="samples"></a>Esempi

Per altre informazioni sui cubi, è possibile creare il cubo usato in questi esempi seguendo l'esercitazione di Analysis Services fino alla lezione 4 sulla [creazione di un cubo OLAP](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md).

È inoltre possibile scaricare un cubo esistente come backup e ripristinarlo in un'istanza di Analysis Services. Ad esempio, è possibile scaricare un cubo elaborato completamente per [Adventure Works Multidimensional Model SQL 2014](http://msftdbprodsamples.codeplex.com/downloads/get/882334)in formato compresso e ripristinarlo all'istanza di SSAS. Per altre informazioni, vedere [Backup e ripristino](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)o [Cmdlet Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).
