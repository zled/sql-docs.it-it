---
title: "Trasformazione Campionamento percentuale | Microsoft Docs"
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
  - "sql13.dts.designer.percentagesamplingtrans.f1"
helpviewer_keywords: 
  - "test di modelli di data mining"
  - "valori di inizializzazione del campionamento [Integration Services]"
  - "data mining [Analysis Services], set di dati di esempio"
  - "Campionamento percentuale - trasformazione"
  - "set di dati di esempio [Integration Services]"
  - "set di dati [Integration Services], esempio"
  - "training di modelli di data mining"
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Trasformazione Campionamento percentuale
  La trasformazione Campionamento percentuale consente di creare un set di dati campione selezionando una percentuale delle righe di input della trasformazione. Il set di dati campione viene ottenuto selezionando casualmente dall'input della trasformazione un numero di righe sufficiente per ottenere un campione rappresentativo dell'input.  
  
> [!NOTE]  
>  Oltre alla percentuale specificata, la trasformazione Campionamento percentuale utilizza un algoritmo per determinare quali righe devono essere incluse nell'output campione. Il numero delle righe nell'output campione potrebbe di conseguenza non corrispondere esattamente alla percentuale specificata. Se ad esempio si specifica il 10% per un set di dati di input di 25.000 righe, il campione generato potrebbe non includere 2.500 righe, ma alcune righe in più o in meno.  
  
 La trasformazione Campionamento percentuale è particolarmente utile per il data mining. Tramite questa trasformazione è possibile suddividere casualmente un set di dati in due set di dati: uno per il training del modello di data mining e uno per il test del modello.  
  
 La trasformazione Campionamento percentuale può essere utilizzata anche per la creazione di set di dati di esempio per lo sviluppo dei pacchetti. Applicando la trasformazione Campionamento percentuale a un flusso di dati, è possibile ridurre uniformemente le dimensioni di un set di dati, mantenendo tuttavia le caratteristiche dei dati. Il pacchetto di test può essere pertanto eseguito più rapidamente, perché utilizza un set di dati più piccolo ma comunque rappresentativo.  
  
## Configurazione della trasformazione Campionamento percentuale  
 È possibile specificare un valore di inizializzazione del campionamento per modificare il comportamento del generatore di numeri casuali utilizzato dalla trasformazione per la selezione delle righe. Se si utilizza sempre lo stesso valore di inizializzazione del campionamento, la trasformazione creerà sempre lo stesso output campione. Se non viene specificato alcun valore di inizializzazione, per creare il numero casuale la trasformazione utilizzerà il numero di tick del sistema operativo. È pertanto possibile scegliere di utilizzare un valore di inizializzazione standard per verificare i risultati della trasformazione durante lo sviluppo e il test di un pacchetto e quindi passare all'utilizzo di un valore di inizializzazione casuale quando il pacchetto viene introdotto nell'ambiente di produzione.  
  
 Questa trasformazione è simile alla trasformazione Campionamento righe, che crea un set di dati campione selezionando un numero specificato di righe di input. Per altre informazioni, vedere [Trasformazione Campionamento righe](../../../integration-services/data-flow/transformations/row-sampling-transformation.md).  
  
 La trasformazione Campionamento percentuale include la proprietà personalizzata **SamplingValue**, che può essere aggiornata da un'espressione di proprietà al caricamento del pacchetto. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Utilizzo delle espressioni di proprietà nei pacchetti](../../../integration-services/expressions/use-property-expressions-in-packages.md) e [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Questa trasformazione include un input e due output. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Campionamento percentuale**, vedere [Editor trasformazione Campionamento percentuale](../../../integration-services/data-flow/transformations/percentage-sampling-transformation-editor.md).  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../Topic/Common%20Properties.md)  
  
-   [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  