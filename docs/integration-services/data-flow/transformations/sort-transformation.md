---
title: "Trasformazione Ordinamento | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sorttrans.f1"
helpviewer_keywords: 
  - "Ordinamento - trasformazione"
  - "ordinamenti decrescenti"
  - "ordinamenti crescenti"
  - "ordinamento di dati [Integration Services]"
  - "più ordinamenti"
  - "dati duplicati [Integration Services]"
ms.assetid: 728c9351-84a8-4a89-be4d-d50d4adc04e0
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Trasformazione Ordinamento
  La trasformazione Ordinamento consente di disporre i dati di input in ordine crescente o decrescente e di copiare i dati ordinati nell'output della trasformazione. A uno stesso input è possibile applicare più ordinamenti, ognuno dei quali è identificato da un numero che ne determina il tipo. La colonna con il numero più basso viene ordinata per prima, quindi viene ordinata quella con il secondo numero più basso e così via. Se ad esempio la colonna di nome **CountryRegion** ha come tipo di ordinamento 1 e la colonna di nome **City** ha come tipo di ordinamento 2, l'output verrà ordinato prima per country/region, quindi per city. Un numero positivo indica che l'ordinamento è crescente, mentre un numero negativo indica che è decrescente. Le colonne che non sono ordinate hanno un tipo di ordinamento 0. Le colonne non selezionate per l'ordinamento vengono copiate automaticamente nell'output della trasformazione insieme alle colonne ordinate.  
  
 La trasformazione Ordinamento include un set di opzioni di confronto che consentono di definire la modalità di gestione dei dati stringa in una colonna. Per altre informazioni, vedere [Comparing String Data](../../../integration-services/data-flow/comparing-string-data.md).  
  
> [!NOTE]  
>  La trasformazione Ordinamento non dispone i GUID nello stesso ordine della clausola ORDER BY in Transact-SQL. La trasformazione Ordinamento dispone i GUID che iniziano con 0-9 prima di quelli che iniziano con A-F, mentre la clausola ORDER BY li ordina in modo diverso, come implementato in [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]. Per altre informazioni, vedere [Clausola ORDER BY &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md).  
  
 La trasformazione Ordinamento è inoltre in grado di rimuovere le righe duplicate nell'ambito dell'operazione di ordinamento. Sono considerate duplicate le righe che hanno valori di chiave di ordinamento identici. Il valore della chiave di ordinamento viene generato in base alle opzioni utilizzate per il confronto delle stringhe e questo significa che stringhe letterali diverse possono avere gli stessi valori di chiave di ordinamento. La trasformazione identifica come duplicate le righe delle colonne di input che hanno valori di chiave di ordinamento identici, anche se i valori effettivi sono diversi.  
  
 La trasformazione Ordinamento include la proprietà personalizzata **MaximumThreads**, che può essere aggiornata da un'espressione di proprietà al caricamento del pacchetto. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Utilizzo delle espressioni di proprietà nei pacchetti](../../../integration-services/expressions/use-property-expressions-in-packages.md) e [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Questa trasformazione include un input e un output. Non supporta output degli errori.  
  
## Configurazione della trasformazione Ordinamento  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Ordinamento**, vedere [Editor trasformazione Ordinamento](../../../integration-services/data-flow/transformations/sort-transformation-editor.md).  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../Topic/Common%20Properties.md)  
  
-   [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## Attività correlate  
 Per altre informazioni su come impostare le proprietà del componente, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## Contenuto correlato  
 Esempio relativo al [componente SSIS personalizzato SortDeDuplicateDelimitedString](http://go.microsoft.com/fwlink/?LinkId=220821) su codeplex.com.  
  
## Vedere anche  
 [Flusso di dati](../../../integration-services/data-flow/data-flow.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  