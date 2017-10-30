---
title: Configurazione del componente Script nell'Editor del componente di Script | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script component
- Script Component Editor
- SSIS Script component, configuring
- Script component [Integration Services], configuring
ms.assetid: 586dd799-f383-4d6d-b1a1-f09233d14f0a
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8488fcc7d402430f66b9b9018b31956a5a1d8383
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="configuring-the-script-component-in-the-script-component-editor"></a>Configurazione del componente script nell'editor corrispondente
  Prima di scrivere codice personalizzato nel componente Script, è necessario selezionare il tipo di componente del flusso di dati che si desidera creare, ovvero origine, trasformazione o destinazione e quindi configurare i metadati e le proprietà del componente di **Editor trasformazione Script**.  
  
## <a name="selecting-the-type-of-component-to-create"></a>Selezione del tipo di componente da creare  
 Quando si aggiunge un componente di Script nel riquadro flusso di dati di [!INCLUDE[ssIS](../../../includes/ssis-md.md)] finestra di progettazione, il **Seleziona tipo componente Script** viene visualizzata la finestra di dialogo. Preconfigurare il componente come origine, trasformazione o destinazione. Dopo aver effettuato la selezione iniziale, è possibile continuare a configurare il componente di **Editor trasformazione Script**.  
  
 Per impostare il linguaggio script predefinito per il componente Script, utilizzare il **linguaggio di Scripting** opzione il **generale** pagina del **opzioni** la finestra di dialogo. Per ulteriori informazioni, vedere [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
## <a name="understanding-the-two-design-time-modes"></a>Informazioni sulle due modalità della fase di progettazione  
 In Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] sono disponibili due modalità per il componente script: progettazione metadati e progettazione codice.  
  
 Quando si apre il **Editor trasformazione Script**, il componente passa alla modalità di progettazione metadati. In questa modalità è possibile selezionare colonne di input e aggiungere o configurare output e colonne di output, ma non è possibile scrivere codice. Dopo aver configurato i metadati del componente, è possibile passare in modalità di progettazione codice per scrivere lo script.  
  
 Quando si passa alla modalità di progettazione codice facendo clic su **modifica Script**, il componente Script blocca i metadati per impedire modifiche aggiuntive e quindi genera automaticamente il codice di base dai metadati di input e output. Quando il codice generato automaticamente è completo, sarà possibile immettere il codice personalizzato. Il codice utilizza le classi di base generate automaticamente per elaborare le righe di input, per accedere a buffer e colonne nei buffer e per recuperare gestioni connessioni e variabili dal pacchetto, tutti come oggetti fortemente tipizzati.  
  
 Dopo aver immesso il codice personalizzato in modalità di progettazione codice, è possibile tornare in modalità di progettazione metadati. In questo modo il codice immesso non viene eliminato. Tuttavia, le successive modifiche ai metadati causano la rigenerazione della classe di base. In seguito, la convalida del componente può non riuscire perché è possibile che gli oggetti a cui fa riferimento il codice personalizzato non esistano più o siano stati modificati. In questo caso, è necessario correggere manualmente il codice in modo che possa essere compilato correttamente rispetto alla classe di base rigenerata.  
  
## <a name="configuring-the-component-in-metadata-design-mode"></a>Configurazione del componente in modalità di progettazione metadati  
 In modalità di progettazione metadati è possibile selezionare colonne di input e aggiungere e configurare output e colonne di output, ma non è possibile scrivere codice. Dopo aver configurato i metadati del componente, passare in modalità di progettazione codice per scrivere lo script.  
  
 Le proprietà che è necessario configurare nell'editor personalizzato dipendono dall'utilizzo del componente script. Il componente script può essere configurato come origine, trasformazione o destinazione. A seconda di come viene utilizzato, il componente supporta un input o più output oppure entrambi. Il codice personalizzato che verrà scritto elabora le righe e le colonne di input e output.  
  
### <a name="inputs-columns-page-of-the-script-transformation-editor"></a>Pagina Colonne di input dell'editor trasformazione Script  
 Il **colonne di Input** pagina della finestra di **Editor trasformazione Script** viene visualizzata per trasformazioni e destinazioni, ma non per le origini. In questa pagina selezionare le colonne di input che si desidera rendere disponibili per lo script personalizzato, quindi specificare l'accesso di sola lettura o di lettura/scrittura a tali colonne.  
  
 Nel progetto di codice che verrà generato in base a questi metadati, l'elemento di progetto BufferWrapper contiene una classe per ogni input, la quale contiene proprietà delle funzioni di accesso tipizzate per ogni colonna di input selezionata. Ad esempio, se si seleziona un numero intero **CustomerID** colonna e una stringa **CustomerName** colonna da un input denominato **CustomerInput**, l'elemento di progetto BufferWrapper conterrà una **CustomerInput** classe che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>e **CustomerInput** classe esporrà una proprietà integer denominata **CustomerID** e una proprietà stringa denominata **CustomerName**. Con questa convenzione è possibile scrivere codice con controllo dei tipi come riportato di seguito:  
  
```vb  
Dim currentCustomerID as Integer = CustomerInput.CustomerID  
Dim currentCustomerName as String = CustomerInput.CustomerName  
```  
  
 Per ulteriori informazioni su come configurare le colonne di input per un tipo specifico del componente del flusso di dati, vedere l'esempio appropriato in [lo sviluppo di specifici tipi di componenti Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
### <a name="inputs-and-outputs-page-of-the-script-transformation-editor"></a>Pagina Input e output dell'editor trasformazione Script  
 Il **Input e output** pagina della finestra di **Editor trasformazione Script** viene visualizzata per origini, trasformazioni e destinazioni. In questa pagina è possibile aggiungere, rimuovere e configurare input, output e colonne di output che si desidera utilizzare nello script personalizzato, con le limitazioni seguenti:  
  
-   Se utilizzato come origine, il componente script non include input e supporta più output.  
  
-   Se utilizzato come trasformazione, il componente script supporta un input e più output.  
  
-   Se utilizzato come destinazione, il componente script supporta un input e non include output.  
  
 Nel progetto di codice che verrà generato in base a questi metadati, l'elemento di progetto BufferWrapper contiene una classe per ogni input e output. Ad esempio, se si crea un output denominato **CustomerOutput**, l'elemento di progetto BufferWrapper conterrà una **CustomerOutput** classe che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>e **CustomerOutput** classe conterrà le proprietà delle funzioni di accesso tipizzate per ogni colonna di output creato.  
  
 È possibile configurare le colonne di output solo per il **Input e output** pagina. È possibile scegliere le colonne di input per trasformazioni e destinazioni di **le colonne di Input** pagina. Le proprietà delle funzioni di accesso tipizzate create nell'elemento di progetto BufferWrapper saranno di sola scrittura per le colonne di output. Le proprietà della funzione di accesso per le colonne di input verranno sola lettura o lettura/scrittura a seconda del tipo di utilizzo selezionato per ogni colonna nella **le colonne di Input** pagina.  
  
 Per ulteriori informazioni sulla configurazione di input e output per un tipo di dati specifico componente del flusso di vedere l'esempio appropriato in [lo sviluppo di specifici tipi di componenti Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
> [!NOTE]  
>  Anche se non è possibile configurare direttamente un output come output degli errori nel componente script per la gestione automatica delle righe di errore, è possibile riprodurre la funzionalità di un output degli errori creando un output aggiuntivo e utilizzando lo script per indirizzare le righe a questo output quando è appropriato. Per ulteriori informazioni, vedere [simulando un Output degli errori per il componente Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).  
  
#### <a name="exclusiongroup-and-synchronousinputid-properties-of-outputs"></a>Proprietà ExclusionGroup e SynchronousInputID degli output  
 Il **ExclusionGroup** proprietà ha un valore diverso da zero solo nelle trasformazioni con output sincroni, in cui il codice esegue il filtro o diramazione e indirizza ogni riga a uno degli output che condividono lo stesso è diverso da zero **ExclusionGroup** valore. Ad esempio, la trasformazione può indirizzare le righe all'output predefinito o a un output degli errori. Quando si crea output aggiuntivi per questo scenario, assicurarsi di impostare il valore della **SynchronousInputID** proprietà su un valore integer che corrisponde alla **ID** di input del componente.  
  
 Il **SynchronousInputID** proprietà ha un valore diverso da zero solo nelle trasformazioni con output sincroni. Se il valore di questa proprietà è zero, significa che l'output è asincrono. Per un output sincrono, in cui le righe vengono passate per il file o agli output selezionati senza l'aggiunta di nuove righe, questa proprietà deve contenere il **ID** di input del componente.  
  
> [!NOTE]  
>  Quando il **Editor trasformazione Script** crea il primo output, i set di editor la **SynchronousInputID** proprietà dell'output di **ID** di input del componente. Tuttavia, quando l'editor crea gli output successivi, nell'editor viene impostata la **SynchronousInputID** le proprietà di tali output su zero.  
>   
>  Se si sta creando un componente con output sincroni, ogni output è necessario che il relativo **SynchronousInputID** proprietà impostata sul **ID** di input del componente. Di conseguenza, ogni output che nell'editor viene creato dopo il primo output è necessario che il relativo **SynchronousInputID** valore cambiato da zero per il **ID** di input del componente.  
>   
>  Se si sta creando un componente con output asincroni, ogni output è necessario che il relativo **SynchronousInputID** proprietà è impostata su zero. Pertanto, è necessario il primo output relativo **SynchronousInputID** valore cambiato dal **ID** di input del componente a zero.  
  
 Per un esempio di indirizzamento delle righe a uno dei due output sincroni nel componente Script, vedere [la creazione di una trasformazione sincrona con il componente Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md).  
  
### <a name="object-names-in-generated-script"></a>Nomi di oggetti nello script generato  
 Il componente script analizza i nomi di input e output, nonché i nomi di colonne negli input e negli output, e in base a tali nomi genera classi e proprietà nell'elemento di progetto BufferWrapper. Se i nomi individuati includono caratteri che non appartengono alle categorie Unicode **UppercaseLetter**, **LowercaseLetter**, **TitlecaseLetter**, **ModifierLetter**, **OtherLetter**, o **DecimalDigitLetter**, vengono eliminati i caratteri non validi nei nomi generati. Ad esempio, gli spazi vengono eliminati, due colonne che presentano nomi di input **FirstName** e [**nome**] vengono entrambe interpretate come avente il nome della colonna **FirstName**, con risultati imprevisti. Per evitare questa situazione, i nomi di input e output e di colonne di input e output utilizzati dal componente script devono contenere solo caratteri delle categorie Unicode elencate in questa sezione.  
  
### <a name="script-page-of-the-script-transformation-editor"></a>Pagina Script dell'editor trasformazione Script  
 Nel **Script** pagina il **Editor attività Script**, si assegna un nome univoco e una descrizione per l'attività Script. È anche possibile assegnare valori per le proprietà seguenti.  
  
> [!NOTE]  
>  In [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] e versioni successive, tutti gli script sono precompilati. Nelle versioni precedenti, è specificato se gli script sono precompilati impostando una **Precompile** proprietà per l'attività.  
  
#### <a name="validateexternalmetadata-property"></a>Proprietà ValidateExternalMetadata  
 Il valore booleano di **proprietà ValidateExternalMetadata** proprietà specifica se il componente deve eseguire la convalida rispetto a origini dati esterne in fase di progettazione o se deve posticiparla fino al runtime. Per impostazione predefinita, il valore di questa proprietà è **True**; ovvero, i metadati esterni viene convalidato in fase di progettazione e in fase di esecuzione. È possibile impostare il valore di questa proprietà su **False** quando un'origine dati esterna non è disponibile in fase di progettazione: ad esempio, quando il pacchetto Scarica l'origine o crea la destinazione solo in fase di esecuzione.  
  
#### <a name="readonlyvariables-and-readwritevariables-properties"></a>Proprietà ReadOnlyVariables e ReadWriteVariables  
 È possibile immettere elenchi delimitati da virgole di variabili esistenti come valori di queste proprietà per rendere le variabili disponibili per l'accesso di sola lettura o di lettura/scrittura all'interno del codice del componente script. Le variabili sono accessibili nel codice tramite le proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadOnlyVariables%2A> e <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReadWriteVariables%2A> della classe di base generata automaticamente. Per ulteriori informazioni, vedere [utilizzo di variabili nel componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).  
  
> [!NOTE]  
>  Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.  
  
#### <a name="scriptlanguage"></a>ScriptLanguage  
 È possibile selezionare [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# come linguaggio di programmazione per il componente Script.  
  
#### <a name="edit-script-button"></a>Pulsante Modifica script  
 Il **modifica Script** pulsante consente di aprire il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE in cui scrivere lo script personalizzato. Per ulteriori informazioni, vedere [la codifica e debug del componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="connection-managers-page-of-the-script-transformation-editor"></a>Pagina Gestioni connessioni dell'editor trasformazione Script  
 Nel **gestioni connessioni** pagina del **Editor trasformazione Script**, aggiungere e rimuovere le gestioni connessioni che si desidera utilizzare nello script personalizzato. Normalmente, è necessario fare riferimento a gestioni connessioni quando si crea un componente di origine o di destinazione.  
  
 Nel codice di progetto che verrà generato in base a questi metadati, il **ComponentWrapper** elemento di progetto contiene un **connessioni** classe di raccolta che contiene una proprietà di funzioni di accesso tipizzate per ogni gestione connessione selezionata. Ogni proprietà di funzione di accesso tipizzata ha lo stesso nome della gestione connessione e restituisce un riferimento alla gestione connessione come istanza di <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100>. Ad esempio, se è stato aggiunto a una gestione connessione denominata `MyADONETConnection` sul **gestioni connessioni** pagina dell'editor, è possibile ottenere un riferimento alla gestione connessione nello script usando il codice seguente:  
  
```vb  
Dim myADONETConnectionManager As IDTSConnectionManager100 = _  
    Me.Connections.MyADONETConnection  
```  
  
 Per ulteriori informazioni, vedere [connessione alle origini dati nel componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).  
  
## <a name="see-also"></a>Vedere anche  
 [La codifica e debug del componente Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  

