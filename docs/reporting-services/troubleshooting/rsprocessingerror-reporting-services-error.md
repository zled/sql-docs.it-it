---
title: rsProcessingError - errore di Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rsProcessingError
ms.assetid: 414ee58a-8251-4367-9a8e-10c068d17280
caps.latest.revision: 29
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7065e2f766ec3ce56bed2d9b3bc0e90c5290b6ea
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="rsprocessingerror---reporting-services-error"></a>rsProcessingError - Errore di Reporting Services
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|rsProcessingError|  
|Origine evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Errori durante l'elaborazione del report.|  
  
## <a name="explanation"></a>Spiegazione  
 Sono stati rilevati uno o più errori durante la pubblicazione, l'elaborazione, la visualizzazione in anteprima locale, la visualizzazione dal server di report o la creazione di una sottoscrizione per un report. Il messaggio di errore indica che è stato rilevato almeno un errore.  
  
### <a name="possible-causes"></a>Possibili cause  
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
  
## <a name="user-action"></a>Azione dell'utente  
  
### <a name="finding-more-information"></a>Per ulteriori informazioni  
 Eseguire una o più delle operazioni seguenti:  
  
-   Se si visualizza il report dal server di report o come sottoscrizione, esaminare il testo completo del messaggio di errore per ottenere ulteriori informazioni.  
  
-   Se il report viene creato in Progettazione report e questo errore viene visualizzato durante l'anteprima o la pubblicazione del report, ulteriori informazioni saranno disponibili nella finestra Elenco errori.  
  
-   Se il report viene creato in Anteprima di Progettazione report, esaminare il testo completo del messaggio di errore per ottenere ulteriori informazioni.  
  
-   Se si visualizza un report nel server di report e si esegue il servizio come amministratore locale nel server di report, è possibile visualizzare lo stack di chiamate facendo clic con il pulsante destro del mouse sulla pagina e scegliendo **Visualizza origine**. Nello stack di chiamate verranno fornite ulteriori informazioni.  
  
-   Se l'accesso al server di report è stato eseguito come amministratore locale, ricercare `ReportProcessingException`nel file di log. Le voci del log contengono ulteriori informazioni. File di log del server di report si trovano in genere \< *unità*>: \Programmi\Microsoft SQL Server\MSRS12. MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__*datetimestamp*. log. Per altre informazioni, vedere [File di log e origini di Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
### <a name="failed-to-load-expression-host-assembly"></a>Impossibile caricare l'assembly delle espressioni  
 Gli assembly personalizzati devono essere firmati con nome sicuro. È inoltre necessario che il relativo attributo AllowPartiallyTrustedCallers sia impostato. Per altre informazioni, vedere [Utilizzo di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md) e [Informazioni sui criteri di sicurezza](../../reporting-services/extensions/secure-development/understanding-security-policies.md).  
  
### <a name="a-built-in-global-name-does-not-exist"></a>Impossibile trovare un nome globale predefinito  
 Controllare l'ortografia nelle espressioni. I nomi predefiniti globali, dei parametri e dei campi rispettano la distinzione tra maiuscole e minuscole. Nell'espressione che provoca l'errore controllare che il nome esista effettivamente nel report e che sia stato digitato correttamente. Per altre informazioni, vedere [Raccolte predefinite nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
### <a name="parameter-properties-and-null"></a>Proprietà dei parametri e valori Null  
 Il valore di un parametro multivalore non può essere Null. Per altre informazioni, vedere [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
### <a name="main-report-with-subreport-could-not-be-processed"></a>Impossibile elaborare un report principale con sottoreport  
 È necessario che un report con sottoreport venga elaborato dalla stessa versione di Elaborazione report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Durante l'aggiornamento di report alla versione corrente dello schema di definizione del report, è possibile che il report principale e i sottoreport non vengano aggiornati contemporaneamente. Se la versione di un report non è compatibile con quella dei sottoreport, viene visualizzato un messaggio di errore che indica l'impossibilità di elaborare il sottoreport.  
  
 È necessario modificare il report principale o i sottoreport in modo che tutti i report possano essere elaborati dalla stessa versione di Elaborazione report. Per informazioni sui motivi relativi all'impossibilità di aggiornare un report, vedere [Aggiornare i report](../../reporting-services/install-windows/upgrade-reports.md).  
  
### <a name="verify-function-calls-are-visual-basic-and-not-sql"></a>Chiamate di funzione di Visual Basic e non SQL  
 È possibile usare le funzioni SQL nel testo della query in un database relazionale. Nel testo della query non è possibile usare funzioni [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
 In espressioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]è possibile usare funzioni [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , funzioni System.Math o System.String, funzioni [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] complete o funzioni personalizzate incluse in codice o in un assembly personalizzato. Non è possibile usare funzioni SQL in un'espressione.  
  
 Verificare che le chiamate di funzione eseguite nella query e nelle espressioni siano valide.  
  
### <a name="cannot-compare-data-types-for-a-filter"></a>Impossibile confrontare tipi di dati per un filtro  
 In un'equazione di filtro è necessario che il tipo di dati dell'espressione che definisce gli elementi da filtrare e quello del valore del filtro sia lo stesso, in modo che sia possibile eseguirne il confronto. Se viene visualizzato uno degli errori seguenti, modificare l'espressione del campo o il valore del filtro in modo che i tipi di dati corrispondano:  
  
-   L'elaborazione di  *\<tipo di elemento del report >* per il  *\<nome elemento report >* non può essere eseguita. Impossibile confrontare tipi di dati  *\<tipo >* e  *\<tipo >*. Verificare il tipo di dati restituito dal  *\<nome elemento report >*.  
  
-   Impossibile valutare il  *\<nome proprietà >*.  
  
-   Impossibile valutare il  *\<nome proprietà >*. Fa riferimento a un campo del set di dati che contiene un errore:  *\<stringa di errore >*.  
  
 Per altre informazioni, vedere [Filtro, raggruppamento e ordinamento di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
### <a name="invalid-or-conflicting-scope-specification-in-an-aggregate-function-call"></a>Specifica di un ambito non valido o in conflitto in una chiamata di funzione di aggregazione  
 Quando si includono chiamate di funzioni di aggregazione in un'espressione di una cella Tablix, in Elaborazione report l'espressione viene valutata nell'ambito dei gruppi più interni cui la cella appartiene.  
  
 È anche possibile passare il nome di un ambito specifico a una funzione di aggregazione. L'ambito può fare riferimento al nome di un set di dati o di un'area dati oppure al nome di un ambito a livello più elevato nella gerarchia dei dati. Questa condizione è valida per i seguenti messaggi:  
  
-   Il  *\<tipo di elemento del report >* '*\<nome elemento report >*' ha un ambito non valido "*\<nome ambito >*". L'ambito deve essere l'ambito corrente oppure deve essere contenuto nell'ambito corrente.  
  
-   Il  *\<nome proprietà >* espressione per il  *\<tipo di elemento del report >* '*\<nome di elemento di report >*' ha un parametro di ambito che non è valido per una funzione di aggregazione. Il parametro di ambito deve essere impostato su una costante stringa uguale al nome di un gruppo contenitore, al nome di un'area dati contenitore oppure al nome di un set di dati.  
  
 Per le funzioni di aggregazione che calcolano i totali parziali (**Previous**, **RunningValue**o **RowNumber**), è possibile specificare come parametro di ambito un nome di un gruppo di righe oppure un nome di un gruppo di colonne, ma non entrambi. Questa condizione è valida per il seguente messaggio di errore:  
  
-   **Precedente**, **RunningValue** o **RowNumber** utilizzate nelle celle di dati di funzioni di aggregazione di  *\<tipo degli elementi del report >* '*\<nome di elemento di report >*' fare riferimento ad ambiti in entrambe le colonne e righe di raggruppamento il  *\<tipo di elemento del report >*. I parametri di ambito di tutti **precedente**, **RunningValue** e **RowNumber** le funzioni di aggregazione un  *\<tipo di elemento del report >* può fare riferimento a raggruppamenti di righe o raggruppamenti di colonne di dati, ma non entrambi.  
  
 Per altre informazioni, vedere [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md) e [Raccolte predefinite nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
### <a name="default-dataset-scope-for-a-top-level-text-box"></a>Ambito predefinito del set di dati per una casella di testo di livello principale  
 Non usare un ambito predefinito per una casella di testo aggiunta all'area di progettazione del report quando nel report è contenuto più di un set di dati. Usare invece un'espressione che includa il nome del set di dati come ambito e una funzione di aggregazione, Ad esempio, `=First(Fields!FieldName.Value, "DataSet2")`.  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Riferimento a funzioni di aggregazione &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Esempi di espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Set di dati del report &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Filtri di uso comune &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/commonly-used-filters-report-builder-and-ssrs.md)   
 [Raccolta di campi del set di dati &#40; Generatore report e SSRS &#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Codice personalizzato e riferimenti ad Assembly in espressioni in Progettazione Report &#40; SSRS &#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)   
 [Riferimenti alla raccolta di parametri &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
