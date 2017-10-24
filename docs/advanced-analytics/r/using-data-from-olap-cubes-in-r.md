---
title: Uso dei dati dai cubi OLAP in R | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: bdd86896b43d79b5d7cd00383476700735accff4
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="using-data-from-olap-cubes-in-r"></a>Uso dei dati dai cubi OLAP in R

Il pacchetto **olapR** è un nuovo pacchetto R, disponibile in Microsoft R Server ed SQL Server R Services, che consente di eseguire query MDX e usare i dati dai cubi OLAP nella soluzione R.

Con questo pacchetto, non è necessario creare server collegati o eliminare set di righe bidimensionali; è possibile usare i dati OLAP direttamente in R.

## <a name="overview"></a>Panoramica

Un cubo OLAP è un database multidimensionale che contiene aggregazioni precalcolate in base a *misure*che in genere acquisiscono importanti metriche aziendali, ad esempio l'importo delle vendite, il numero di vendite o altri valori numerici. I cubi OLAP vengono ampiamente usati per l'acquisizione e l'archiviazione dei dati aziendali critici nel tempo. I dati OLAP vengono utilizzati per l'analisi aziendale da un'ampia gamma di strumenti, dashboard e visualizzazioni. Per altre informazioni, vedere [Online analytical processing](https://en.wikipedia.org/wiki/Online_analytical_processing)(Elaborazione analitica online).

Il pacchetto **olapR** supporta due metodi per la creazione di query MDX: 

- È possibile generare una semplice query MDX usando un'API di tipo R per scegliere cubo, assi e filtri dei dati. Con questa funzione, è possibile creare query MDX valide anche se non si dispone dell'accesso agli strumenti OLAP tradizionali o non si ha una profonda conoscenza del linguaggio MDX.

  Si noti che non tutte le query MDX possono essere create con questo metodo nel pacchetto **olapR** , in quanto MDX può essere molto complesso. Tuttavia, supporta tutte le operazioni più comuni e utili, tra cui sezionamento, estrazione, drill-down, rollup e pivot nelle dimensioni N.

+ È possibile creare manualmente e quindi incollare una query MDX. Questa operazione è utile se sono disponibili query MDX esistenti che si vuole riutilizzare o se la query che si vuole creare è troppo complessa per la gestione con **olapR** . 

  Questo approccio consente di creare una query MDX con qualsiasi utilità client, ad esempio SSMS o Excel, e quindi usarla come argomento stringa per il *gestore di query SSAS* fornito dal pacchetto. La funzione **olapR** invierà la query al server di Analysis Services specificato e restituirà i risultati a R.

Per esempi su come creare una query MDX o eseguire una query MDX esistente, vedere [Come creare query MDX con R](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md).


## <a name="mdx-basics"></a>Nozioni fondamentali su MDX

I dati in un cubo possono essere recuperati tramite il linguaggio di query MDX (MultiDimensional Expression). Poiché i dati in un cubo OLAP (o database di Analysis Services) sono multidimensionali, anziché in formato tabulare, MDX supporta una sintassi complessa e una serie di operazioni di filtro e sezionamento dei dati:

+ *Sezionamento* considera un subset del cubo, scegliendo un valore per una dimensione, e ottiene un cubo più piccolo di una dimensione. 

+ *Estrazione* crea un sottocubo specificando un intervallo di valori in più dimensioni.

+ *Drill-down* passa da un riepilogo alle informazioni dettagliate.

+ *Drill-up* passa dalle informazioni dettagliate a un livello superiore di aggregazione.

+ *Rollup* riepiloga i dati in una dimensione.

+ *Pivot* ruota il cubo o la selezione di dati.

Questo argomento fornisce altri esempi che illustrano la sintassi di base per eseguire una query su un cubo.
[Come creare query MDX con R](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)


## <a name="known-issues"></a>Problemi noti

### <a name="tabular-models-not-supported-currently"></a>Modelli tabulari attualmente non supportati

È possibile connettersi a un'istanza tabulare di Analysis Services e la funzione `explore` segnalerà l'esito positivo con un valore TRUE, ma gli oggetti del modello tabulare non sono un tipo compatibile e non possono essere esaminati. 

I modelli tabulari supportano le query MDX, ma una query MDX valida per un modello tabulare restituirà NULL e non segnalerà un errore.

## <a name="resources"></a>Risorse

Se non si ha familiarità con OLAP o le query MDX, vedere questi articoli di Wikipedia: [Cubo OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
[Query MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)

### <a name="samples"></a>Esempi

Per altre informazioni sui cubi, è possibile creare il cubo usato in questi esempi seguendo l'esercitazione di Analysis Services fino alla lezione 4 sulla [creazione di un cubo OLAP](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md).

È inoltre possibile scaricare un cubo esistente come backup e ripristinarlo in un'istanza di Analysis Services. Ad esempio, è possibile scaricare un cubo elaborato completamente per [Adventure Works Multidimensional Model SQL 2014](http://msftdbprodsamples.codeplex.com/downloads/get/882334)in formato compresso e ripristinarlo all'istanza di SSAS. Per altre informazioni, vedere [Backup e ripristino](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)o [Cmdlet Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).

## <a name="see-also"></a>Vedere anche
[Come creare query MDX con R](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)

[MDX Query Designer for Analysis Services](http://msdn.microsoft.com/library/7e288eee-2d37-485e-a6a0-dbba5e041e26)



