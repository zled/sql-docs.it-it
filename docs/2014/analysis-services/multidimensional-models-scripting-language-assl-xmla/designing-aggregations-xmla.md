---
title: Progettazione di aggregazioni (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statistical information [XML for Analysis]
- batches [XML for Analysis]
- aggregations [Analysis Services], XML for Analysis
- XMLA, aggregations
- queries [XMLA]
- XML for Analysis, aggregations
- iterative aggregation process [XMLA]
ms.assetid: 4dd27afa-10c7-408d-bc24-ca74217ddbcb
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 773187385538a70ed145e330eb60c648cf8f0511
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161332"
---
# <a name="designing-aggregations-xmla"></a>Progettazione di aggregazioni (XMLA)
  Le progettazioni delle aggregazioni sono associate alle partizioni di un gruppo di misure specifico per garantire che utilizzino la stessa struttura nell'archiviazione delle aggregazioni. Usando la stessa struttura di archiviazione per le partizioni consente di definire in modo semplice partizioni che possono essere unite in un secondo momento usando il [MergePartitions](../xmla/xml-elements-commands/mergepartitions-element-xmla.md) comando. Per altre informazioni sulle progettazioni delle aggregazioni, vedere [aggregazioni e progettazione di aggregazioni](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
 Per definire le aggregazioni per una progettazione delle aggregazioni, è possibile usare la [DesignAggregations](../xmla/xml-elements-commands/designaggregations-element-xmla.md) comando XML for Analysis (XMLA). Al comando `DesignAggregations` sono associate proprietà che identificano quale progettazione delle aggregazioni utilizzare come riferimento e il modo in cui controllare il processo di progettazione in base a tale riferimento. L'utilizzo del comando `DesignAggregations` e delle proprietà relative consente di progettare le aggregazioni in modo iterativo oppure in batch e di visualizzare successivamente le statistiche relative alla progettazione risultanti per valutare il processo di progettazione.  
  
## <a name="specifying-an-aggregation-design"></a>Specifica di una progettazione delle aggregazioni  
 Il [oggetti](../xmla/xml-elements-properties/object-element-xmla.md) proprietà del `DesignAggregations` comando deve contenere un riferimento a una progettazione delle aggregazioni esistente. Il riferimento all'oggetto contiene un identificatore di database, un identificatore di cubo, un identificatore del gruppo di misure e un identificatore della progettazione delle aggregazioni. Se la progettazione delle aggregazioni non esiste, si verifica un errore.  
  
## <a name="controlling-the-design-process"></a>Controllo del processo di progettazione  
 Per controllare l'algoritmo utilizzato per definire le aggregazioni per la relativa progettazione, è possibile utilizzare le proprietà del comando `DesignAggregations` seguenti:  
  
-   Il [passaggi](../xmla/xml-elements-properties/steps-element-xmla.md) proprietà determina il numero di iterazioni di `DesignAggregations` comando da eseguire prima che restituisca il controllo all'applicazione client.  
  
-   Il [tempo](../xmla/xml-elements-properties/time-element-xmla.md) proprietà determina quanti millisecondi il `DesignAggregations` comando da eseguire prima che restituisca il controllo all'applicazione client.  
  
-   Il [Optimization](../xmla/xml-elements-properties/optimization-element-xmla.md) proprietà determina la percentuale stimata di miglioramento delle prestazioni di `DesignAggregations` comando deve provare a raggiungere. Se si progettano le aggregazioni in modo iterativo, è necessario inviare questa proprietà solo al primo comando.  
  
-   Il [memorizzazione](../xmla/xml-elements-properties/storage-element-xmla.md) proprietà determina la quantità stimata di archiviazione su disco, in byte usata dal `DesignAggregations` comando. Se si progettano le aggregazioni in modo iterativo, è necessario inviare questa proprietà solo al primo comando.  
  
-   Il [Materialize](../xmla/xml-elements-properties/materialize-element-xmla.md) proprietà determina se il `DesignAggregations` comando deve creare le aggregazioni definite durante il processo di progettazione. Se si progettano le aggregazioni in modo iterativo, questa proprietà deve essere impostata su false fino a quando non è possibile salvare le aggregazioni progettate. Quando la proprietà viene impostata su true, il processo di progettazione corrente termina e le aggregazioni definite vengono aggiunte alla progettazione delle aggregazioni specificata.  
  
## <a name="specifying-queries"></a>Specifica di query  
 Il comando DesignAggregations supporta il comando per l'ottimizzazione basata sull'utilizzo includendo uno o più `Query` elementi nel [query](../xmla/xml-elements-properties/queries-element-xmla.md) proprietà. Il `Queries` proprietà può contenere uno o più [Query](../xmla/xml-elements-properties/query-element-xmla.md) elementi. Se la proprietà `Queries` non contiene alcun elemento `Query`, la progettazione delle aggregazioni specificata nell'elemento `Object` utilizza una struttura predefinita che contiene un set generale di aggregazioni appositamente progettato per soddisfare i criteri specificati nelle proprietà `Optimization` e `Storage` del comando `DesignAggregations`.  
  
 Ogni `Query` elemento rappresenta una query di tipo goal utilizzata dal processo di progettazione per definire le aggregazioni destinate alle query utilizzate più di frequente. È possibile specificare query di tipo goal personalizzate oppure è possibile usare le informazioni archiviate da un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nel log di query per recuperare informazioni su più di frequente query utilizzate. Il log di query viene utilizzato dall'Ottimizzazione guidata basata sulle statistiche di utilizzo per recuperare query di tipo goal in base all'ora, all'utilizzo oppure all'utente specificato quando viene inviato un comando `DesignAggregations`. Per altre informazioni, vedere [basata sull'utilizzo della Guida di ottimizzazione guidata F1](../usage-based-optimization-wizard-f1-help.md).  
  
 Se si siano progettando in modo iterativo le aggregazioni, è sufficiente passato query di tipo goal al primo `DesignAggregations` comando perché la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza archivia queste query e le utilizza durante le successive `DesignAggregations` comandi. Dopo avere passato query di tipo goal al primo comando `DesignAggregations` di un processo iterativo, qualsiasi comando `DesignAggregations` successivo che contiene query di tipo goal nella proprietà `Queries` genera un errore.  
  
 L'elemento `Query` contiene un valore delimitato da virgole in cui sono presenti gli argomenti seguenti:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Frequenza*  
 Fattore di ponderazione corrispondente al numero di volte che la query è stata eseguita in precedenza. Se il `Query` elemento rappresenta una nuova query, il *frequenza* valore rappresenta il fattore del ponderazione utilizzato dal processo di progettazione per valutare la query. Con l'aumentare del valore della frequenza, aumenta il peso associato alla query durante il processo di progettazione.  
  
 *Set di dati*  
 Stringa numerica che specifica gli attributi di una dimensione da includere nella query. Questa stringa deve avere un numero di caratteri uguale al numero di attributi della dimensione. Il valore zero (0) indica che l'attributo nella posizione ordinale specificata non è incluso nella query per la dimensione specificata, mentre il valore uno (1) indica che l'attributo nella posizione ordinale specificata è incluso nella query per la dimensione specificata.  
  
 La stringa "011" fa riferimento ad esempio a una query relativa a una dimensione con tre attributi, di cui il secondo e il terzo sono inclusi nella query.  
  
> [!NOTE]  
>  Alcuni attributi non vengono considerati nel set di dati. Per altre informazioni sugli attributi esclusi, vedere [elemento Query &#40;XMLA&#41;](../xmla/xml-elements-properties/query-element-xmla.md).  
  
 Ogni dimensione nel gruppo di misure che contiene la progettazione delle aggregazioni è rappresentata da un *set di dati* valore il `Query` elemento. L'ordine dei valori *Dataset* deve corrispondere all'ordine delle dimensioni incluse nel gruppo di misure.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>Progettazione di aggregazioni tramite processi iterativi o elaborazioni batch  
 È possibile utilizzare il comando `DesignAggregations` come parte di un processo iterativo o di un'elaborazione batch, in base all'interattività richiesta dal processo di progettazione.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>Progettazione di aggregazioni tramite un processo iterativo  
 Per progettare le aggregazioni in modo iterativo, inviare più comandi `DesignAggregations` per fornire un controllo accurato sul processo di progettazione. Questo approccio viene utilizzato anche dalla Progettazione guidata aggregazioni per ottenere lo stesso scopo. Per altre informazioni, vedere [della Guida F1 di aggregazione progettazione guidata](../aggregation-design-wizard-f1-help.md).  
  
> [!NOTE]  
>  Per progettare in modo iterativo le aggregazioni, è necessaria una sessione esplicita. Per altre informazioni sulle sessioni esplicite, vedere [alla gestione delle connessioni e sessioni &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md).  
  
 Per avviare il processo iterativo, inviare innanzitutto un comando `DesignAggregations` che contiene le informazioni seguenti:  
  
-   Valori delle proprietà `Storage` e `Optimization` in base ai quali viene impostato l'intero processo di progettazione.  
  
-   Valori delle proprietà `Steps` e `Time` in base ai quali viene limitato il primo passaggio del processo di progettazione.  
  
-   Proprietà `Queries` che contiene le query di tipo goal in base alle quali viene impostato l'intero processo di progettazione, qualora si desideri l'ottimizzazione basata sulle statistiche di utilizzo.  
  
-   Proprietà `Materialize` impostata su false. L'impostazione di questa proprietà su false indica che durante il processo di progettazione le aggregazioni definite non vengono salvate nella progettazione delle aggregazioni quando il comando è completato.  
  
 Quando termina, il primo comando `DesignAggregations` restituisce un set di righe che contiene le statistiche relative alla progettazione. È possibile valutare tali statistiche per determinare se il processo di progettazione deve continuare o se è completato. Se il processo deve continuare, inviare un altro comando `DesignAggregations` che contiene i valori `Steps` e `Time` con i quali viene limitato questo passaggio del processo di progettazione. È possibile valutare le statistiche risultanti e successivamente determinare se il processo di progettazione deve continuare. Questo processo iterativo costituito dall'invio di comandi `DesignAggregations` e dalla valutazione dei risultati continua fino a quando non si raggiungono gli obiettivi e non si ottiene un set appropriato di aggregazioni definite.  
  
 Dopo avere ottenuto il set di aggregazioni desiderato, inviare un comando `DesignAggregations` finale. Le proprietà `DesignAggregations` e `Steps` di tale comando `Materialize` finale devono essere impostate su 1 e su true rispettivamente. Utilizzando queste impostazioni il comando `DesignAggregations` finale completa il processo di progettazione e salva l'aggregazione definita nella progettazione delle aggregazioni.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>Progettazione di aggregazioni tramite un'elaborazione batch  
 È inoltre possibile progettare le aggregazioni in un'elaborazione batch inviando un unico comando `DesignAggregations` che contiene i valori delle proprietà `Steps`, `Time`, `Storage` e `Optimization` in base ai quali viene impostato e limitato l'intero processo di progettazione. Qualora si desideri l'ottimizzazione basata sulle statistiche di utilizzo, nella proprietà `Queries` devono essere incluse anche le query di tipo goal in base alle quali viene impostato il processo di progettazione. È inoltre necessario verificare che la proprietà `Materialize` sia impostata su true, in modo che durante il processo di progettazione le aggregazioni definite vengano salvate nella progettazione delle aggregazioni quando il comando termina.  
  
 È possibile progettare aggregazioni tramite un'elaborazione batch in una sessione implicita oppure in una esplicita. Per altre informazioni sulle sessioni implicite ed esplicite, vedere [alla gestione delle connessioni e sessioni &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md).  
  
## <a name="returning-design-statistics"></a>Restituzione di statistiche relative alla progettazione  
 Quando il comando `DesignAggregations` restituisce il controllo all'applicazione client, viene restituito anche un set di righe contenente un'unica riga che rappresenta le statistiche relative alla progettazione per il comando. Nel set di righe sono contenute le colonne elencate nella tabella seguente.  
  
|colonna|Tipo di dati|Description|  
|------------|---------------|-----------------|  
|Passaggi|Valore intero|Numero di passaggi eseguiti dal comando prima di restituire il controllo all'applicazione client.|  
|Time|Long integer|Numero di millisecondi necessari al comando prima di restituire il controllo all'applicazione client.|  
|Optimization|Double|Percentuale stimata di miglioramento delle prestazioni ottenuta dal comando prima di restituire il controllo all'applicazione client.|  
|Archiviazione|Long integer|Numero stimato di byte necessari al comando prima di restituire il controllo all'applicazione client.|  
|Aggregations|Long integer|Numero di aggregazioni definite dal comando prima di restituire il controllo all'applicazione client.|  
|LastStep|Boolean|Indica se i dati nel set di righe rappresentano l'ultimo passaggio del processo di progettazione. Se la proprietà `Materialize` del comando è impostata su true, il valore di questa colonna viene impostato su true.|  
  
 È possibile utilizzare le statistiche relative alla progettazione contenute nel set di righe restituito dopo ogni comando `DesignAggregations` sia nella progettazione di tipo iterativo che in quella di tipo batch. Nella progettazione di tipo iterativo è possibile utilizzare le statistiche relative alla progettazione per determinare e visualizzare lo stato di avanzamento. Quando si progettano le aggregazioni in batch, è possibile utilizzare le statistiche relative alla progettazione per determinare il numero di aggregazioni create dal comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
