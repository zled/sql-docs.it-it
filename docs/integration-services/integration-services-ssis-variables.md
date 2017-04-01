---
title: "Variabili di Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "variabili [Integration Services], passaggio tra pacchetti"
  - "variabili definite dall'utente [Integration Services]"
  - "ambito [Integration Services]"
  - "variabili di sistema [Integration Services]"
  - "variabili [Integration Services]"
  - "variabili [Integration Services], informazioni sulle variabili"
  - "valori [Integration Services]"
ms.assetid: c1e81ad6-628b-46d4-9b09-d2866517b6ca
caps.latest.revision: 60
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 59
---
# Variabili di Integration Services (SSIS)
  Nelle variabili vengono archiviati valori che possono essere usati in fase di esecuzione da un pacchetto di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e dai relativi contenitori, attività e gestori di eventi. Anche gli script nell'attività Script e nel componente script possono utilizzare le variabili. I vincoli di precedenza che definiscono la sequenza delle attività e dei contenitori in un flusso di lavoro possono utilizzare variabili quando le definizioni di vincolo includono espressioni.  
  
 Nei pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è possibile usare variabili per gli scopi seguenti:  
  
-   Aggiornamento delle proprietà degli elementi dei pacchetti in fase di esecuzione. È ad esempio possibile impostare dinamicamente il numero di eseguibili simultanei consentiti in un contenitore Ciclo Foreach.  
  
-   Inclusione di una tabella di ricerca in memoria. Un pacchetto può ad esempio eseguire un'attività Esegui SQL che carica una variabile con valori di dati.  
  
-   Caricamento di variabili con valori di dati da utilizzare per specificare una condizione di ricerca in una clausola WHERE. Lo script in un'attività Script può ad esempio aggiornare il valore di una variabile utilizzata da un'istruzione Transact-SQL in un'attività Esegui SQL.  
  
-   Caricamento di una variabile con un valore intero da utilizzare per il controllo del ciclo in un flusso di controllo di un pacchetto. È ad esempio possibile utilizzare una variabile nell'espressione di valutazione di un contenitore Ciclo For per controllare l'iterazione.  
  
-   Popolamento di valori di parametri per istruzioni Transact-SQL in fase di esecuzione. Un pacchetto può ad esempio eseguire un'attività Esegui SQL e quindi utilizzare variabili per impostare dinamicamente i parametri in un'istruzione Transact-SQL.  
  
-   Compilazione di espressioni che includono valori di variabili. La trasformazione Colonna derivata può ad esempio popolare una colonna con i risultati ottenuti moltiplicando il valore di una variabile per il valore di una colonna.  
  
## Variabili definite dall'utente e variabili di sistema  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] supporta due tipi di variabili: variabili definite dall'utente e variabili di sistema. Le variabili definite dall'utente vengono definite dagli sviluppatori dei pacchetti, mentre quelle di sistema sono definite da [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. È possibile creare un numero illimitato di variabili definite dall'utente, ma non è possibile creare ulteriori variabili di sistema.  
  
 Tutte le variabili, di sistema e definite dall'utente, possono essere utilizzate nelle associazioni di parametro utilizzate dall'attività Esegui SQL per il mapping variabili a parametri nelle istruzioni SQL. Per altre informazioni, vedere [Attività Esegui SQL](../integration-services/control-flow/execute-sql-task.md) e [Parametri e codici restituiti nell'attività Esegui SQL](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md).  
  
> [!NOTE]  
>  Per i nomi delle variabili di sistema e delle variabili definite dall'utente viene fatta distinzione tra maiuscole e minuscole.  
  
 È possibile creare variabili definite dall'utente per tutti i tipi di contenitori di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], ovvero pacchetti, contenitori Ciclo Foreach, contenitori Ciclo For, contenitori Sequenza, attività e gestori di eventi. Le variabili definite dall'utente sono membri della raccolta Variables del contenitore.  
  
 Se si crea il pacchetto usando Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)], sarà possibile vedere i membri di una raccolta Variables nella cartella **Variabili** della scheda **Esplora pacchetti** di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)]. Nelle cartelle vengono elencate sia le variabili definite dall'utente che le variabili di sistema.  
  
 Nella configurazione delle variabili definite dall'utente è possibile:  
  
-   Specificare un nome e una descrizione per la variabile.  
  
-   Specificare uno spazio dei nomi per la variabile.  
  
-   Indicare se la variabile genera un evento quando il relativo valore viene modificato.  
  
-   Indicare se la variabile è in sola lettura o in lettura e scrittura.  
  
-   Utilizzare il risultato della valutazione di un'espressione per impostare il valore della variabile.  
  
-   Creare la variabile nell'ambito del pacchetto o di un oggetto del pacchetto, ad esempio un'attività.  
  
-   Specificare il valore e il tipo di dati della variabile.  
  
 L'unica opzione configurabile delle variabili di sistema è quella che determina se debba essere generato o meno un evento quando il valore viene modificato.  
  
 Per ogni tipo di contenitore è disponibile un set di variabili di sistema specifico. Per altre informazioni sulle variabili di sistema usate dai pacchetti e dai relativi elementi, vedere [Variabili di sistema](../integration-services/system-variables.md).  
  
 Per altre informazioni su scenari reali relativi all'uso delle variabili, vedere [Utilizzo di variabili nei pacchetti](../Topic/Use%20Variables%20in%20Packages.md).  
  
## Proprietà delle variabili  
 È possibile configurare le variabili definite dall'utente impostando le proprietà seguenti nella finestra **Variabili** o nella finestra **Proprietà**. Alcune proprietà sono disponibili solo nella finestra Proprietà.  
  
> [!NOTE]  
>  L'unica opzione configurabile delle variabili di sistema è quella che determina se debba essere generato o meno un evento quando il valore viene modificato.  
  
 Description  
 Specifica la descrizione della variabile.  
  
 EvaluateAsExpression  
 Quando la proprietà è impostata su **True**, viene usata l'espressione fornita per impostare il valore della variabile.  
  
 Espressione  
 Specifica l'espressione assegnata alla variabile.  
  
 Nome  
 Specifica il nome della variabile.  
  
 Spazio dei nomi  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offre due spazi dei nomi: **User** e **System**. Per impostazione predefinita, le variabili personalizzate appartengono allo spazio dei nomi**User**, mentre le variabili di sistema appartengono allo spazio dei nomi **System**. È possibile creare altri spazi dei nomi per le variabili definite dall'utente e modificare il nome dello spazio dei nomi **User**, ma non è possibile modificare il nome dello spazio dei nomi **System**, né aggiungere variabili allo spazio dei nomi **System** o assegnare variabili di sistema a uno spazio dei nomi diverso.  
  
 RaiseChangedEvent  
 Se la proprietà è impostata su **True**, quando viene modificato il valore della variabile viene generato l'evento **OnVariableValueChanged**.  
  
 ReadOnly  
 Quando la proprietà è impostata su **False**, la variabile è in lettura/scrittura.  
  
 Ambito  
 > [!NOTE]  
>  È possibile modificare questa proprietà solo facendo clic su **Sposta variabile** nella finestra **Variabili**.  
  
 Le variabili vengono create nell'ambito di un pacchetto o nell'ambito di un contenitore, attività o gestore di evento di un pacchetto. Poiché il contenitore del pacchetto costituisce il livello principale della gerarchia dei contenitori, le variabili con ambito pacchetto sono variabili globali e possono essere utilizzate da tutti i contenitori del pacchetto. Analogamente, le variabili definite nell'ambito di un contenitore, quale Ciclo For, possono essere utilizzate da tutti i contenitori e le attività inclusi nel contenitore Ciclo For.  
  
 Se un pacchetto esegue altri pacchetti utilizzando l'attività Esegui pacchetto, sarà possibile utilizzare il tipo di configurazione Variabile pacchetto padre per rendere disponibili al pacchetto chiamato le variabili definite nell'ambito del pacchetto chiamante o dell'attività Esegui pacchetto. Per altre informazioni, vedere [Configurazioni di pacchetto](../integration-services/packages/package-configurations.md).  
  
 IncludeInDebugDump  
 Indica se il valore della variabile viene incluso nei file di dump del debug.  
  
 Per variabili definite dall'utente e variabili di sistema, il valore predefinito per l'opzione **InclueInDebugDump** è **true**.  
  
 Per le variabili definite dall'utente, tuttavia, l'opzione **IncludeInDebugDump** viene reimpostata su **false** quando sono rispettate le condizioni seguenti:  
  
-   Se la proprietà della variabile **EvaluateAsExpression** è impostata su **true**, l'opzione **IncludeInDebugDump** verrà reimpostata su **false**.  
  
     Per includere il testo dell'espressione come valore della variabile nei file di dump del debug, impostare l'opzione **IncludeInDebugDump** su **true**.  
  
-   Se il tipo di dati della variabile viene cambiato in String, l'opzione **IncludeInDebugDump** verrà reimpostata su **false**.  
  
 Durante la reimpostazione dell'opzione **IncludeInDebugDump** su **false** può essere eseguito l'override del valore selezionato dall'utente.  
  
 Valore  
 Il valore di una variabile definita dall'utente può essere un valore letterale o un'espressione. Le variabili includono opzioni per l'impostazione del valore e del relativo tipo di dati. Queste due proprietà devono essere compatibili. Non è ad esempio possibile utilizzare un valore stringa insieme a un tipo di dati Integer.  
  
 Se la variabile è configurata in modo da essere valutata come espressione, sarà necessario specificare un'espressione. In fase di esecuzione l'espressione verrà valutata e la variabile verrà impostata sul risultato della valutazione. Se ad esempio una variabile usa l'espressione `DATEPART("month", GETDATE())`, assumerà un valore equivalente al numero del mese della data corrente. È necessario utilizzare un'espressione valida che utilizza la sintassi della grammatica delle espressioni di [!INCLUDE[ssIS](../includes/ssis-md.md)]. Quando si utilizza un'espressione con variabili, quest'ultima può includere valori letterali, nonché le funzioni e gli operatori previsti dalla grammatica delle espressioni, ma non può fare riferimento a colonne di un flusso di dati del pacchetto. Un'espressione può avere una lunghezza massima di 4000 caratteri. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../integration-services/expressions/integration-services-ssis-expressions.md).  
  
 ValueType  
 > [!NOTE]  
>  Il valore della proprietà viene visualizzato nella colonna **Tipo di dati** della finestra **Variabili**.  
  
 Specificare il tipo di dati del valore della variabile.  
  
## Configurazione delle variabili  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)], vedere [Finestra Variabili](../integration-services/variables-window.md).  
  
 Per altre informazioni sulle proprietà delle variabili e sull'impostazione di tali proprietà a livello di codice, vedere <xref:Microsoft.SqlServer.Dts.Runtime.Variable>.  
  
## Attività correlate  
 [Aggiungere, eliminare o modificare l'ambito di una variabile definita dall'utente in un pacchetto](../Topic/Add,%20Delete,%20Change%20Scope%20of%20User-Defined%20Variable%20in%20a%20Package.md)  
  
 [Impostazione delle proprietà di una variabile definita dall'utente](../Topic/Set%20the%20Properties%20of%20a%20User-Defined%20Variable.md)  
  
 [Utilizzare i valori di variabili e parametri in un pacchetto figlio](../integration-services/packages/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
 [Mapping dei parametri di query a variabili in un componente del flusso di dati](../integration-services/data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
  