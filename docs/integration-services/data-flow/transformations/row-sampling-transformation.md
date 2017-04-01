---
title: "Trasformazione Campionamento righe | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.rowsamplingtrans.f1"
helpviewer_keywords: 
  - "valori di inizializzazione del campionamento [Integration Services]"
  - "inizializzazioni casuali"
  - "campionamento casuale"
  - "set di dati di esempio [Integration Services]"
  - "Campionamento righe - trasformazione"
  - "pacchetti [Integration Services], esempi"
  - "set di dati [Integration Services], esempio"
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Trasformazione Campionamento righe
  La trasformazione Campionamento righe consente di ottenere un subset di elementi selezionati casualmente da un set di dati di input. È possibile specificare le dimensioni esatte dell'output campione e un valore di inizializzazione per il generatore di numeri casuali.  
  
 Il campionamento casuale può essere utilizzato in molte circostanze. Se ad esempio in una società si desidera selezionare casualmente 50 dipendenti a cui assegnare i premi di una lotteria, sarà possibile utilizzare la trasformazione Campionamento righe sul database dei dipendenti per generare esattamente il numero di vincitori specificato.  
  
 La trasformazione Campionamento righe risulta utile anche durante lo sviluppo dei pacchetti, per la creazione di un set di dati piccolo ma rappresentativo. È possibile testare l'esecuzione del pacchetto e la trasformazione dei dati con dati altamente rappresentativi, ma più rapidamente, perché al posto del set di dati completo viene utilizzato un campione casuale. Poiché le dimensioni del set di dati di esempio utilizzato dal pacchetto di test sono sempre uguali, l'utilizzo del subset campione semplifica inoltre l'identificazione di eventuali problemi di prestazioni nel pacchetto.  
  
 Questa trasformazione è simile alla trasformazione Campionamento percentuale, che crea un set di dati campione selezionando una percentuale delle righe di input. Vedere [Trasformazione Campionamento percentuale](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md).  
  
## Configurazione della trasformazione Campionamento righe  
 La trasformazione Campionamento righe crea un set di dati campione selezionando un numero specificato di righe di input della trasformazione. Poiché la selezione delle righe dall'input della trasformazione è casuale, il campione risultante è rappresentativo dell'input. Per determinare la modalità di selezione delle righe da parte della trasformazione, è inoltre possibile specificare il valore di inizializzazione utilizzato dal generatore di numeri casuali.  
  
 Se si utilizza sempre lo stesso valore di inizializzazione per il generatore di numeri casuali sullo stesso input della trasformazione, si otterrà sempre lo stesso output campione. Se non viene specificato alcun valore di inizializzazione, per creare il numero casuale la trasformazione utilizzerà il numero di tick del sistema operativo. È pertanto possibile utilizzare un valore di inizializzazione costante durante il test per verificare i risultati della trasformazione durante lo sviluppo e il test di un pacchetto e quindi passare all'utilizzo di un valore di inizializzazione casuale quando il pacchetto viene introdotto nell'ambiente di produzione.  
  
 La trasformazione Campionamento righe include la proprietà personalizzata **SamplingValue**, che può essere aggiornata da un'espressione di proprietà al caricamento del pacchetto. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Utilizzo delle espressioni di proprietà nei pacchetti](../../../integration-services/expressions/use-property-expressions-in-packages.md) e [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Questa trasformazione include un input e due output. Non include alcun output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Campionamento righe**, vedere [Editor trasformazione Campionamento righe &#40;pagina Campionamento&#41;](../../../integration-services/data-flow/transformations/row-sampling-transformation-editor-sampling-page.md).  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../Topic/Common%20Properties.md)  
  
-   [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Per ulteriori informazioni sull'impostazione delle proprietà, vedere.  
  
## Attività correlate  
 [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
  