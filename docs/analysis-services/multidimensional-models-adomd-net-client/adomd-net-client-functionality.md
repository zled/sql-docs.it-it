---
title: La funzionalità Client ADOMD.NET | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1347bad80b8fb076d3c4f2b765f06513ff76d8d8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="adomdnet-client-functionality"></a>Funzionalità client di ADOMD.NET
  Analogamente agli altri provider di dati [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, ADOMD.NET funge da ponte tra un'applicazione e un'origine dati. A differenza degli altri provider di dati .NET Framework, tuttavia, in ADOMD.NET vengono utilizzati dati analitici. Per utilizzare dati analitici, ADOMD.NET supporta funzionalità notevolmente diverse da quelle degli altri provider di dati .NET Framework. ADOMD.NET consente non solo di recuperare dati, ma anche di recuperare metadati e di modificare la struttura dell'archivio dati analitici:  
  
 **Il recupero dei metadati**  
 Per ottenere maggiori informazioni sui dati che possono essere recuperati dall'origine dati tramite il recupero di metadati, le applicazioni possono utilizzare set di righe dello schema o il modello a oggetti. È possibile individuare informazioni quali i tipi di ogni indicatore di prestazioni chiave (KPI) disponibile, le dimensioni in un cubo e i parametri necessari per i modelli di data mining. I metadati sono molto importanti per *dinamica* applicazioni che richiedono l'input dell'utente per determinare il tipo, di profondità e ambito dei dati da recuperare. ad esempio Query Analyzer, Microsoft Excel e altri strumenti per l'esecuzione di query. I metadati sono meno critici per *statico* applicazioni che eseguono un set predefinito di azioni.  
  
 Per ulteriori informazioni: [recupero di metadati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md).  
  
 **Recupero di dati**  
 Per recupero di dati si intende il recupero effettivo delle informazioni archiviate nell'origine dati. Il recupero di dati rappresenta la funzione principale di applicazioni "statiche" cui è nota la struttura dell'origine dati, nonché il risultato finale di applicazioni "dinamiche". Il valore dell'indicatore di prestazioni chiave a un'ora specificata del giorno, il numero di biciclette vendute nell'ultima ora per ogni punto vendita e i fattori che governano le prestazioni annuali dei dipendenti sono tutti esempi di dati che possono essere recuperati. Il recupero di dati è estremamente importante per tutte le applicazioni che eseguono query.  
  
 Per ulteriori informazioni: [recupero dei dati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md).  
  
 **Modifica della struttura di dati analitici**  
 ADOMD.NET può essere utilizzato inoltre per modificare la struttura dell'archivio dati analitici. Sebbene questa operazione venga in genere eseguita mediante il modello a oggetti della libreria AMO (Analysis Management Objects), è possibile utilizzare ADOMD.NET per inviare comandi ASSL (Analysis Services Scripting Language) per creare, modificare o eliminare oggetti nel server.  
  
 Per altre informazioni: [l'esecuzione di comandi su un analitici origine dati](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md), [allo sviluppo con Analysis Management Objects &#40;AMO&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md), [Analysis Services Scripting Lingua &#40;ASSL per XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)  
  
 Il recupero di metadati e di dati e la modifica della struttura di dati vengono eseguiti ciascuno in un punto specifico nel flusso di lavoro di un'applicazione ADOMD.NET tipica.  
  
## <a name="typical-process-flow"></a>Flusso di elaborazione tipico  
 In caso di utilizzo di un database analitico, le applicazioni ADOMD.NET tradizionali seguono in genere lo stesso flusso di lavoro:  
  
1.  Viene stabilita innanzitutto una connessione al database mediante l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Quando si apre la connessione, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> espone metadati relativi al server cui è stata eseguita la connessione. In un'applicazione dinamica alcune di queste informazioni vengono in genere mostrate all'utente in modo che quest'ultimo possa eseguire una selezione, ad esempio il cubo su cui eseguire una query. La connessione creata durante questo passaggio può essere riutilizzata più volte dall'applicazione, con la conseguente riduzione dell'overhead.  
  
     Per ulteriori informazioni: [Establishing Connections in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)  
  
2.  Una volta stabilita una connessione, un'applicazione dinamica potrebbe quindi eseguire una query sul server per ottenere metadati più specifici. Nel caso di un'applicazione statica, il programmatore conosce in anticipo gli oggetti sui quali l'applicazione eseguirà una query e pertanto non sarà necessario recuperare tali metadati. I metadati recuperati possono essere utilizzati dall'applicazione e dall'utente per il passaggio successivo.  
  
     Per ulteriori informazioni: [recupero di metadati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
3.  Successivamente l'applicazione esegue un comando sul server al fine di recuperare metadati o dati aggiuntivi o di modificare la struttura del database. Per ciascuna di queste attività, l'applicazione potrebbe utilizzare una query determinata in precedenza oppure avvalersi dei metadati appena recuperati per creare query aggiuntive.  
  
     Per ulteriori informazioni: [recupero di metadati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md), [recupero dei dati da un'origine dati analitici](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md), [l'esecuzione di comandi su un analitici origine dati](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md)  
  
4.  Una volta che il comando è stato inviato al server, quest'ultimo inizia a restituire i metadati oppure i dati al client. Queste informazioni possono essere visualizzate utilizzando un <xref:Microsoft.AnalysisServices.AdomdClient.CellSet> oggetto, un <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> oggetto, o un **System.XmlReader** oggetto.  
  
 Per illustrare questo flusso di lavoro tradizionale, nell'esempio seguente viene utilizzato un metodo che apre una connessione al database, esegue un comando su un cubo noto e recupera i risultati inserendoli in un set di celle. Quest'ultimo restituisce quindi una stringa delimitata da tabulazione che contiene intestazioni di colonna e di riga e dati delle celle.  
  
 [!code-cs[Adomd.NetClient#ReturnCommandUsingCellSet](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/adomd-net-client-functio_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
