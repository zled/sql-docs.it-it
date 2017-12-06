---
title: Utilizzando i dati di cubi OLAP in R | Documenti Microsoft
ms.custom: 
ms.prod: sql-non-specified
ms.date: 11/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: r-services
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 60e95f4c101a4afe2a8161ba40df7b27bd85f602
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="using-data-from-olap-cubes-in-r"></a>Utilizzando i dati di cubi OLAP in R

Il **olapR** pacchetto è un pacchetto R, fornito da Microsoft per l'utilizzo con Machine Learning Server e SQL Server, che consente di eseguire query MDX per ottenere dati dai cubi OLAP. Con questo pacchetto, è necessario creare server collegati o pulire i set di righe bidimensionali; è possibile utilizzare dati OLAP direttamente in R.

In questo articolo viene descritta l'API, insieme a una panoramica di OLAP e MDX per gli utenti di R che potrebbero essere nuovi per database di cubi multidimensionali.

> [!IMPORTANT]
> Un'istanza di Analysis Services può supportare convenzionali cubi multidimensionali e modelli tabulari, ma un'istanza non è in grado di supportare entrambi i tipi di modelli. Pertanto, prima di creare una query su un database di Analysis Services, verificare che contenga i modelli multidimensionali.
> 
> Sebbene un modello tabulare è possibile eseguire query tramite MDX, il **olapR** pacchetto non supporta le connessioni a istanze di modello tabulare. Se si desidera ottenere dati da una modalità tabulare, un'opzione migliore consiste nell'abilitazione [DirectQuery](https://docs.microsoft.com/sql/analysis-services/tabular-models/directquery-mode-ssas-tabular) sul modello e crea l'istanza disponibile come server collegato in SQL Server. 

## <a name="what-is-an-olap-cube"></a>Che cos'è un cubo OLAP?

OLAP è l'abbreviazione di elaborazione analitica in linea. Soluzioni OLAP vengono ampiamente utilizzate per l'acquisizione e l'archiviazione di dati aziendali critici nel tempo. I dati OLAP vengono utilizzati per l'analisi aziendale da un'ampia gamma di strumenti, dashboard e visualizzazioni. Per ulteriori informazioni, vedere [elaborazione analitica in linea](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft fornisce [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services), che consente di progettare, distribuire e query dei dati OLAP sotto forma di _cubi_ o _modelli tabulari_. Un cubo è un database multidimensionale. _Dimensioni_ equivalgono facet dei dati, o fattori di r: utilizzare le dimensioni per identificare un sottoinsieme specifico di dati che si desidera riepilogare o analizzare. Ad esempio, ora è una dimensione importante, tanta in modo che molte soluzioni OLAP includono più calendari definiti per impostazione predefinita, da utilizzare durante il sezionamento e riepilogare i dati. 

Per motivi di prestazioni, un database OLAP calcola spesso riepiloghi (o _aggregazioni_) in anticipo e quindi li archivia per il recupero veloce. Si basano *misure*, che rappresentano le formule che possono essere applicate ai dati numerici. Utilizzare le dimensioni per definire un subset di dati e quindi calcolare la misura i dati. Ad esempio, utilizzare una misura per calcolare le vendite totali per una determinata riga prodotto più trimestri meno imposte per segnalare i costi di spedizione medio per un particolare fornitore, year-to-date cumulativo Salari a pagamento e così via.

MDX, abbreviazione di espressioni MDX, è il linguaggio utilizzato per eseguire query sui cubi. Una query MDX in genere contiene una definizione di dati che include una o più dimensioni e almeno una misura, anche se le query MDX possono ottenere notevolmente più complesse e può includere windows mobile, cumulative medie, somme, classificazioni o percentili. 

Ecco alcuni altri termini che potrebbero essere utili quando si avvia la creazione di query MDX:

+ *Il sezionamento* accetta un subset del cubo utilizzando i valori da una singola dimensione.

+ *Estrazione* crea un sottocubo specificando un intervallo di valori in più dimensioni.

+ *Drill-down* passa da un riepilogo alle informazioni dettagliate.

+ *Drill-up* passa dalle informazioni dettagliate a un livello superiore di aggregazione.

+ *Rollup* riepiloga i dati in una dimensione.

+ *Pivot* ruota il cubo o la selezione di dati.

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>Come utilizzare olapR per creare query MDX

Il seguente articolo fornisce esempi dettagliati di sintassi per la creazione o l'esecuzione di query su un cubo:

+ [Come creare query MDX con R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapR API

Il pacchetto **olapR** supporta due metodi per la creazione di query MDX:

- **Utilizzare il Generatore MDX.** Utilizzare le funzioni R nel pacchetto per generare una semplice query MDX, scegliendo un cubo, e quindi impostando gli assi e i filtri dei dati. Questo è un modo semplice per compilare una query MDX valida se non si dispone dell'accesso agli strumenti OLAP tradizionali o non dispone di una profonda conoscenza del linguaggio MDX.

    Non tutte le query MDX possono essere create utilizzando questo metodo, poiché MDX può essere complessa. Tuttavia, questa API supporta la maggior parte delle operazioni più comuni e utili, incluso dimensioni N sezione dice, drill-down, rollup e pivot.

+ **Copiare e incollare il MDX ben formato.** Creare manualmente e quindi incollare in qualsiasi query MDX. Questa opzione è la migliore se sono presenti query MDX esistente che si desidera riutilizzare o se si desidera compilare query è troppo complessa per **olapR** di gestire. 

    Compilare il codice MDX tramite le utilità client, ad esempio SQL Server Management Studio o Excel e quindi salvare la stringa che definisce la query MDX. Questa stringa MDX è fornire come argomento per il *gestore query SSAS* nel **olapR** pacchetto. La funzione Invia la query al server Analysis Services specificato e passa nuovamente i risultati a R, presupponendo che si dispone delle autorizzazioni necessarie per eseguire query sul cubo naturalmente.

Per esempi di come compilare un MDX query oppure eseguire una query MDX esistente, vedere [come creare query MDX utilizzando R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Problemi noti

Questa sezione sono elencati alcuni problemi noti e domande frequenti sul **olapR** pacchetto.

### <a name="tabular-models-are-not-supported"></a>Non sono supportati i modelli tabulari

Se ci si connette a un'istanza di Analysis Services che contiene un modello tabulare, il `explore` funzione segnala l'esito positivo con valore restituito true. Tuttavia, gli oggetti del modello tabulare non sono un tipo compatibile e non possono essere esplorati.

Inoltre, se si progetta una query MDX valida su un modello tabulare (utilizzando uno strumento esterno) e quindi incollarla la query in questa API, la query restituisce un risultato NULL e non segnala un errore.

Se è necessario estrarre i dati da un modello tabulare per l'utilizzo in R, prendere in considerazione queste opzioni:

+ Abilitare DirectQuery nel modello e aggiungere il server come server collegato in SQL Server. 
+ Se il modello tabulare è stato creato in un data mart relazionale, è possibile ottenere i dati direttamente dall'origine.

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>Come determinare se un'istanza contiene modelli tabulari o multidimensionali

Esistono differenze fondamentali tra modelli tabulari e i modelli multidimensionali che influisce sui dati di modalità è archiviati ed elaborati. Ad esempio, i modelli tabulari vengono archiviati in memoria e sfruttano gli indici columnstore consentono di eseguire calcoli molto veloci. Nei modelli multidimensionali, i dati vengono archiviati su disco e le aggregazioni vengono definite in precedenza e recuperate tramite query MDX.

Per questo motivo, una singola istanza di Analysis Services può contenere un solo tipo di modello. Vedere l'articolo seguente per altri suggerimenti su come distinguere i due tipi di modelli:

+ [Il confronto di modelli multidimensionale e tabulare](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

Se ci si connette ad Analysis Services utilizzando un client, ad esempio SQL Server Management Studio, è possibile determinare immediatamente il tipo di modello supportato, esaminando l'icona per il database.

È inoltre possibile visualizzare le proprietà del server. Il **modalità Server** proprietà supporta due valori: _multidimensionali_ o _tabulare_.

Per ulteriori informazioni su come verificare il tipo di server tramite la proprietà del server, vedere [OLE DB per OLAP i rowset dello Schema](https://docs.microsoft.com/sql/analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>Writeback non è supportato.

Non è possibile eseguire il writeback i risultati dei calcoli R personalizzati per il cubo.

In generale, anche quando un cubo è abilitato per il writeback, sono supportate solo le operazioni limitate e potrebbe essere necessaria configurazione aggiuntiva. È consigliabile utilizzare MDX per queste operazioni.

+ [Dimensioni abilitate per scrittura](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [Partizioni abilitate per scrittura](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [Impostare l'accesso personalizzato ai dati delle celle](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

## <a name="resources"></a>Risorse

Se si usa per OLAP o per le query MDX, vedere gli articoli di Wikipedia: 

+ [Cubi OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
+ [Query MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
