---
title: Progettazione di aggregazioni (XMLA) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f020d4b154ecfef556b13be45fced0fa6095f17e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="designing-aggregations-xmla"></a>Progettazione di aggregazioni (XMLA)
  Le progettazioni delle aggregazioni sono associate alle partizioni di un gruppo di misure specifico per garantire che utilizzino la stessa struttura nell'archiviazione delle aggregazioni. Utilizzando la stessa struttura di archiviazione per le partizioni consente di definire in modo semplice partizioni che possono essere unite in un secondo momento utilizzando il [MergePartitions](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md) comando. Per ulteriori informazioni sulle progettazioni delle aggregazioni, vedere [aggregazioni e progettazione di aggregazioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
 Per definire le aggregazioni per una progettazione delle aggregazioni, è possibile utilizzare il [DesignAggregations](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md) comando XML for Analysis (XMLA). Il **DesignAggregations** comando dispone di proprietà che identificano quale progettazione delle aggregazioni da usare come riferimento e il modo controllare il processo di progettazione in base a tale riferimento. Utilizzo di **DesignAggregations** comando e le relative proprietà, è possibile progettare le aggregazioni in modo iterativo o in un batch e quindi visualizzare le statistiche relative alla progettazione risultanti per valutare il processo di progettazione.  
  
## <a name="specifying-an-aggregation-design"></a>Specifica di una progettazione delle aggregazioni  
 Il [oggetto](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) proprietà del **DesignAggregations** comando deve contenere un riferimento a una progettazione delle aggregazioni esistente. Il riferimento all'oggetto contiene un identificatore di database, un identificatore di cubo, un identificatore del gruppo di misure e un identificatore della progettazione delle aggregazioni. Se la progettazione delle aggregazioni non esiste, si verifica un errore.  
  
## <a name="controlling-the-design-process"></a>Controllo del processo di progettazione  
 È possibile utilizzare le seguenti proprietà del **DesignAggregations** comando per controllare l'algoritmo utilizzato per definire aggregazioni per la progettazione delle aggregazioni:  
  
-   Il [passaggi](../../analysis-services/xmla/xml-elements-properties/steps-element-xmla.md) proprietà determina il numero di iterazioni di **DesignAggregations** comando deve trascorrere prima che restituisca il controllo all'applicazione client.  
  
-   Il [ora](../../analysis-services/xmla/xml-elements-properties/time-element-xmla.md) proprietà determina il numero di millisecondi di **DesignAggregations** comando deve trascorrere prima che restituisca il controllo all'applicazione client.  
  
-   Il [ottimizzazione](../../analysis-services/xmla/xml-elements-properties/optimization-element-xmla.md) proprietà determina la percentuale stimata di miglioramento delle prestazioni di **DesignAggregations** comando deve tentare di ottenere. Se si progettano le aggregazioni in modo iterativo, è necessario inviare questa proprietà solo al primo comando.  
  
-   Il [archiviazione](../../analysis-services/xmla/xml-elements-properties/storage-element-xmla.md) proprietà determina la quantità stimata di archiviazione su disco, in byte, utilizzata dal **DesignAggregations** comando. Se si progettano le aggregazioni in modo iterativo, è necessario inviare questa proprietà solo al primo comando.  
  
-   Il [Materialize](../../analysis-services/xmla/xml-elements-properties/materialize-element-xmla.md) proprietà determina se il **DesignAggregations** comando deve creare le aggregazioni definite durante il processo di progettazione. Se si progettano le aggregazioni in modo iterativo, questa proprietà deve essere impostata su false fino a quando non è possibile salvare le aggregazioni progettate. Quando la proprietà viene impostata su true, il processo di progettazione corrente termina e le aggregazioni definite vengono aggiunte alla progettazione delle aggregazioni specificata.  
  
## <a name="specifying-queries"></a>Specifica di query  
 Il comando DesignAggregations supporta il comando di ottimizzazione basata sull'utilizzo includendo uno o più **Query** gli elementi di [query](../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md) proprietà. Il **query** proprietà può contenere uno o più [Query](../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md) elementi. Se il **query** non contiene alcuna proprietà **Query** specifica gli elementi, la progettazione delle aggregazioni di **oggetto** elemento utilizza una struttura predefinita che contiene un set generale di aggregazioni. Questo set generale di aggregazioni è progettato per soddisfare i criteri specificati nel **ottimizzazione** e **archiviazione** le proprietà del **DesignAggregations** comando.  
  
 Ogni elemento **Query** rappresenta una query di tipo goal utilizzata dal processo di progettazione per definire le aggregazioni destinate alle query utilizzate più di frequente. È possibile specificare query di tipo goal personalizzate oppure utilizzare le informazioni archiviate da un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nel log di query per recuperare le informazioni sulle query utilizzate più di frequente. L'ottimizzazione guidata basata sull'utilizzo utilizza il log di query per recuperare query di tipo goal in base all'ora, utilizzo o un utente specificato durante l'invio di un **DesignAggregations** comando. Per ulteriori informazioni, vedere [basata sull'utilizzo della Guida F1 di ottimizzazione guidata](http://msdn.microsoft.com/library/e5f5a938-ae7c-4f4e-9416-a7f94ac82763).  
  
 Se si progettano in modo iterativo le aggregazioni, è necessario solo passare query di tipo goal al primo **DesignAggregations** comando perché la [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza archivia queste query e le utilizza durante i successivi  **DesignAggregations** comandi. Dopo avere passato query di tipo goal al primo comando **DesignAggregations** di un processo iterativo, qualsiasi comando **DesignAggregations** successivo che contiene query di tipo goal nella proprietà **Queries** genera un errore.  
  
 L'elemento **Query** contiene un valore delimitato da virgole in cui sono presenti gli argomenti seguenti:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Frequenza*  
 Fattore di ponderazione corrispondente al numero di volte che la query è stata eseguita in precedenza. Se l'elemento **Query** rappresenta una nuova query, il valore *Frequency* rappresenta il fattore del ponderazione utilizzato dal processo di progettazione per valutare la query. Con l'aumentare del valore della frequenza, aumenta il peso associato alla query durante il processo di progettazione.  
  
 *Set di dati*  
 Stringa numerica che specifica gli attributi di una dimensione da includere nella query. Questa stringa deve avere un numero di caratteri uguale al numero di attributi della dimensione. Il valore zero (0) indica che l'attributo nella posizione ordinale specificata non è incluso nella query per la dimensione specificata, mentre il valore uno (1) indica che l'attributo nella posizione ordinale specificata è incluso nella query per la dimensione specificata.  
  
 La stringa "011" fa riferimento ad esempio a una query relativa a una dimensione con tre attributi, di cui il secondo e il terzo sono inclusi nella query.  
  
> [!NOTE]  
>  Alcuni attributi non vengono considerati nel set di dati. Per ulteriori informazioni sugli attributi esclusi, vedere [elemento di Query &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md).  
  
 Ogni dimensione nel gruppo di misure che contiene la progettazione delle aggregazioni è rappresentata da un valore *Dataset* nell'elemento **Query** . L'ordine dei valori *Dataset* deve corrispondere all'ordine delle dimensioni incluse nel gruppo di misure.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>Progettazione di aggregazioni tramite processi iterativi o elaborazioni batch  
 È possibile utilizzare il **DesignAggregations** comando come parte di un processo iterativo o di un processo batch, in base all'interattività richiesta dal processo di progettazione.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>Progettazione di aggregazioni tramite un processo iterativo  
 Per progettare in modo iterativo le aggregazioni, inviare più **DesignAggregations** comandi per fornire un controllo accurato sul processo di progettazione. Questo approccio viene utilizzato anche dalla Progettazione guidata aggregazioni per ottenere lo stesso scopo. Per ulteriori informazioni, vedere [aggregazione progettazione guidata F1 Guida](http://msdn.microsoft.com/library/39e23cf1-6405-4fb6-bc14-ba103314362d).  
  
> [!NOTE]  
>  Per progettare in modo iterativo le aggregazioni, è necessaria una sessione esplicita. Per ulteriori informazioni sulle sessioni esplicite, vedere [gestione delle connessioni e sessioni &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
 Per avviare il processo iterativo, inviare innanzitutto un **DesignAggregations** comando che contiene le informazioni seguenti:  
  
-   Il **archiviazione** e **ottimizzazione** i valori delle proprietà in cui è destinato l'intero processo di progettazione.  
  
-   Il **passaggi** e **ora** i valori delle proprietà in cui viene limitato il primo passaggio del processo di progettazione.  
  
-   Se si desidera che Ottimizzazione basata sull'utilizzo, il **query** proprietà che contiene l'obiettivo le query sulle quali viene impostato l'intero processo di progettazione.  
  
-   Il **Materialize** proprietà impostata su false. L'impostazione di questa proprietà su false indica che durante il processo di progettazione le aggregazioni definite non vengono salvate nella progettazione delle aggregazioni quando il comando è completato.  
  
 Quando il primo **DesignAggregations** finisce di comando, il comando restituisce un set di righe contenente statistiche relative alla progettazione. È possibile valutare tali statistiche per determinare se il processo di progettazione deve continuare o se è completato. Se il processo deve continuare, quindi inviare un altro **DesignAggregations** comando che contiene il **passaggi** e **ora** valori con cui elaborare questo passaggio della progettazione è limitato. È possibile valutare le statistiche risultanti e successivamente determinare se il processo di progettazione deve continuare. Questo processo iterativo di invio **DesignAggregations** comandi e valutazione dei risultati continua fino a raggiungere gli obiettivi e un set appropriato di aggregazioni definite.  
  
 Dopo aver raggiunto il set di aggregazioni che si desidera, si invia un'ultima **DesignAggregations** comando. Questo finale **DesignAggregations** comando deve avere il **passaggi** impostata su 1 e il relativo **Materialize** proprietà è impostata su true. Utilizzando queste impostazioni, finale **DesignAggregations** comando completa il processo di progettazione e Salva l'aggregazione definita nella progettazione delle aggregazioni.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>Progettazione di aggregazioni tramite un'elaborazione batch  
 È inoltre possibile progettare le aggregazioni in un processo batch inviando un singolo **DesignAggregations** comando che contiene il **passaggi**, **ora**, **archiviazione** , e **ottimizzazione** i valori delle proprietà in cui è destinato e limitato l'intero processo di progettazione. Se si desidera ottimizzazione basata sull'utilizzo, includere anche le query di tipo goal in cui è indirizzato il processo di progettazione nel **query** proprietà. Assicurarsi anche che il **Materialize** proprietà è impostata su true, in modo che il processo di progettazione Salva le aggregazioni definite per la progettazione delle aggregazioni quando il comando termina.  
  
 È possibile progettare aggregazioni tramite un'elaborazione batch in una sessione implicita oppure in una esplicita. Per ulteriori informazioni sulle sessioni implicite ed esplicite, vedere [gestione delle connessioni e sessioni &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
## <a name="returning-design-statistics"></a>Restituzione di statistiche relative alla progettazione  
 Quando il **DesignAggregations** comando restituisce il controllo all'applicazione client, il comando restituisce un set di righe che contiene una singola riga che rappresenta le statistiche relative alla progettazione per il comando. Nel set di righe sono contenute le colonne elencate nella tabella seguente.  
  
|Colonna|Tipo di dati|Description|  
|------------|---------------|-----------------|  
|Passaggi|Integer|Numero di passaggi eseguiti dal comando prima di restituire il controllo all'applicazione client.|  
|Time|Long integer|Numero di millisecondi necessari al comando prima di restituire il controllo all'applicazione client.|  
|Optimization|Double|Percentuale stimata di miglioramento delle prestazioni ottenuta dal comando prima di restituire il controllo all'applicazione client.|  
|Archiviazione|Long integer|Numero stimato di byte necessari al comando prima di restituire il controllo all'applicazione client.|  
|Aggregations|Long integer|Numero di aggregazioni definite dal comando prima di restituire il controllo all'applicazione client.|  
|LastStep|Boolean|Indica se i dati nel set di righe rappresentano l'ultimo passaggio del processo di progettazione. Se il **Materialize** del comando è stata impostata su true, il valore di questa colonna viene impostato su true.|  
  
 È possibile utilizzare le statistiche relative alla progettazione contenute nel set di righe restituito dopo ogni **DesignAggregations** comando sia iterativo e progettazione di batch. Nella progettazione di tipo iterativo è possibile utilizzare le statistiche relative alla progettazione per determinare e visualizzare lo stato di avanzamento. Quando si progettano le aggregazioni in batch, è possibile utilizzare le statistiche relative alla progettazione per determinare il numero di aggregazioni create dal comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
