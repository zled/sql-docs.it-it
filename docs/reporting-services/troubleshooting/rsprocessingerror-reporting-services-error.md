---
title: "rsProcessingError - Errore di Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rsProcessingError"
ms.assetid: 414ee58a-8251-4367-9a8e-10c068d17280
caps.latest.revision: 29
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 29
---
# rsProcessingError - Errore di Reporting Services
    
## Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|rsProcessingError|  
|Origine evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Errori durante l'elaborazione del report.|  
  
## Spiegazione  
 Sono stati rilevati uno o più errori durante la pubblicazione, l'elaborazione, la visualizzazione in anteprima locale, la visualizzazione dal server di report o la creazione di una sottoscrizione per un report. Il messaggio di errore indica che è stato rilevato almeno un errore.  
  
### Possibili cause  
 Le cause possibili includono:  
  
-   Si è verificato un errore di elaborazione nel server di report.  
  
-   Si è verificato un errore di elaborazione durante l'elaborazione del report locale quando è stata visualizzata l'anteprima di un report.  
  
-   Un'espressione di raggruppamento ha restituito un tipo di dati non corretto.  
  
-   Una definizione del filtro ha specificato due espressioni che hanno restituito tipi di dati che non è stato possibile confrontare.  
  
-   Un'espressione ha fatto riferimento a un campo non esistente dell'insieme Fields.  
  
-   Un'espressione ha incluso una chiamata di funzione di aggregazione con un ambito non valido o in conflitto.  
  
-   Un'espressione ha fatto riferimento a un parametro non esistente nella raccolta dei parametri del report.  
  
-   Un assembly personalizzato o un assembly di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] distribuito in modo non corretto non è stato caricato.  
  
-   Un parametro la cui proprietà che ammette i valori Null è impostata su **False** ha rilevato un valore Null nel parametro.  
  
-   Un'espressione relativa alla proprietà Hidden di un'area dati contiene il seguente errore: "Riferimento oggetto non impostato su un'istanza di un oggetto".  
  
-   Un'espressione ha incluso una chiamata di funzione non valida oppure un errore di sintassi.  
  
## Azione dell'utente  
  
### Per ulteriori informazioni  
 Eseguire una o più delle operazioni seguenti:  
  
-   Se si visualizza il report dal server di report o come sottoscrizione, esaminare il testo completo del messaggio di errore per ottenere ulteriori informazioni.  
  
-   Se il report viene creato in Progettazione report e questo errore viene visualizzato durante l'anteprima o la pubblicazione del report, ulteriori informazioni saranno disponibili nella finestra Elenco errori.  
  
-   Se il report viene creato in Anteprima di Progettazione report, esaminare il testo completo del messaggio di errore per ottenere ulteriori informazioni.  
  
-   Se si visualizza un report nel server di report e si esegue il servizio come amministratore locale nel server di report, è possibile visualizzare lo stack di chiamate facendo clic con il pulsante destro del mouse sulla pagina e scegliendo **Visualizza origine**. Nello stack di chiamate verranno fornite ulteriori informazioni.  
  
-   Se l'accesso al server di report è stato eseguito come amministratore locale, ricercare `ReportProcessingException` nel file di log. Le voci del log contengono ulteriori informazioni. Il file di log del server di report si trova in genere nel percorso \<*unità*>:\Programmi\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__*datetimestamp*.log. Per altre informazioni, vedere [File di log e origini di Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
### Impossibile caricare l'assembly delle espressioni  
 Gli assembly personalizzati devono essere firmati con nome sicuro. È inoltre necessario che il relativo attributo AllowPartiallyTrustedCallers sia impostato. Per altre informazioni, vedere [Utilizzo di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md) e [Informazioni sui criteri di sicurezza](../../reporting-services/extensions/secure-development/understanding-security-policies.md).  
  
### Impossibile trovare un nome globale predefinito  
 Controllare l'ortografia nelle espressioni. I nomi predefiniti globali, dei parametri e dei campi rispettano la distinzione tra maiuscole e minuscole. Nell'espressione che provoca l'errore controllare che il nome esista effettivamente nel report e che sia stato digitato correttamente. Per altre informazioni, vedere [Raccolte predefinite nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder-and-ssrs.md).  
  
### Proprietà dei parametri e valori Null  
 Il valore di un parametro multivalore non può essere Null. Per altre informazioni, vedere [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
### Impossibile elaborare un report principale con sottoreport  
 È necessario che un report con sottoreport venga elaborato dalla stessa versione di Elaborazione report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Durante l'aggiornamento di report alla versione corrente dello schema di definizione del report, è possibile che il report principale e i sottoreport non vengano aggiornati contemporaneamente. Se la versione di un report non è compatibile con quella dei sottoreport, viene visualizzato un messaggio di errore che indica l'impossibilità di elaborare il sottoreport.  
  
 È necessario modificare il report principale o i sottoreport in modo che tutti i report possano essere elaborati dalla stessa versione di Elaborazione report. Per informazioni sui motivi relativi all'impossibilità di aggiornare un report, vedere [Aggiornare i report](../../reporting-services/install-windows/upgrade-reports.md).  
  
### Chiamate di funzione di Visual Basic e non SQL  
 È possibile usare le funzioni SQL nel testo della query in un database relazionale. Nel testo della query non è possibile usare funzioni [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
 In espressioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è possibile usare funzioni [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], funzioni System.Math o System.String, funzioni [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] complete o funzioni personalizzate incluse in codice o in un assembly personalizzato. Non è possibile usare funzioni SQL in un'espressione.  
  
 Verificare che le chiamate di funzione eseguite nella query e nelle espressioni siano valide.  
  
### Impossibile confrontare tipi di dati per un filtro  
 In un'equazione di filtro è necessario che il tipo di dati dell'espressione che definisce gli elementi da filtrare e quello del valore del filtro sia lo stesso, in modo che sia possibile eseguirne il confronto. Se viene visualizzato uno degli errori seguenti, modificare l'espressione del campo o il valore del filtro in modo che i tipi di dati corrispondano:  
  
-   L'elaborazione di *\<tipo di elemento del report>* per *\<nome dell'elemento del report>* non può essere eseguita. Impossibile confrontare dati di tipo *\<tipo>* e *\<tipo>*. Verificare il tipo di dati restituito dal *\<nome dell'elemento del report>*.  
  
-   Impossibile valutare *\<nome proprietà>*.  
  
-   Impossibile valutare *\<nome proprietà>*. Fa riferimento a un campo del set di dati che contiene un errore: *\<stringa di errore>*.  
  
 Per altre informazioni, vedere [Filtro, raggruppamento e ordinamento di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
### Specifica di un ambito non valido o in conflitto in una chiamata di funzione di aggregazione  
 Quando si includono chiamate di funzioni di aggregazione in un'espressione di una cella Tablix, in Elaborazione report l'espressione viene valutata nell'ambito dei gruppi più interni cui la cella appartiene.  
  
 È anche possibile passare il nome di un ambito specifico a una funzione di aggregazione. L'ambito può fare riferimento al nome di un set di dati o di un'area dati oppure al nome di un ambito a livello più elevato nella gerarchia dei dati. Questa condizione è valida per i seguenti messaggi:  
  
-   Il *\<tipo di elemento del report>* '*\<nome dell'elemento del report>*' ha un ambito "*\<nome ambito>*" non valido. L'ambito deve essere l'ambito corrente oppure deve essere contenuto nell'ambito corrente.  
  
-   L'espressione *\<nome proprietà>* per il *\<tipo di elemento del report>* '*\<nome dell'elemento del report>*' ha un parametro di ambito non valido per una funzione di aggregazione. Il parametro di ambito deve essere impostato su una costante stringa uguale al nome di un gruppo contenitore, al nome di un'area dati contenitore oppure al nome di un set di dati.  
  
 Per le funzioni di aggregazione che calcolano i totali parziali (**Previous**, **RunningValue** o **RowNumber**), è possibile specificare come parametro di ambito un nome di un gruppo di righe oppure un nome di un gruppo di colonne, ma non entrambi. Questa condizione è valida per il seguente messaggio di errore:  
  
-   Le funzioni di aggregazione **Previous**, **RunningValue** o **RowNumber** usate nelle celle di dati del *\<tipo di elemento del report>* '*\<nome dell'elemento del report>*' fanno riferimento agli ambiti di raggruppamento sia nelle colonne che nelle righe di *\<tipo di elemento del report>*. I parametri di ambito di tutte le funzioni di aggregazione **Previous**, **RunningValue** e **RowNumber** all'interno di *\<tipo di elemento del report>* possono fare riferimento a raggruppamenti di righe o colonne di dati, ma non a entrambi.  
  
 Per altre informazioni, vedere [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md) e [Raccolte predefinite nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder-and-ssrs.md).  
  
### Ambito predefinito del set di dati per una casella di testo di livello principale  
 Non usare un ambito predefinito per una casella di testo aggiunta all'area di progettazione del report quando nel report è contenuto più di un set di dati. Usare invece un'espressione che includa il nome del set di dati come ambito e una funzione di aggregazione, Ad esempio, `=First(Fields!FieldName.Value, "DataSet2")`.  
  
## Vedere anche  
 [Espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Set di dati del report &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Filtri di uso comune &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/commonly-used-filters-report-builder-and-ssrs.md)   
 [Raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Riferimenti a codice personalizzato e ad assembly in espressioni in Progettazione report &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)   
 [Riferimenti alla raccolta dei parametri &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/parameters-collection-references-report-builder-and-ssrs.md)  
  
  