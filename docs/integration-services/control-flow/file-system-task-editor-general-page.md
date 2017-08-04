---
title: "Editor attività file System (pagina generale) | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ab4f38b627ab6fdc566e9ba452d3bf83f9630bb9
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="file-system-task-editor-general-page"></a>Editor attività File system (pagina Generale)
  Usare la pagina **Generale** della finestra di dialogo **Editor attività File system** per configurare l'operazione di file system eseguita dall'attività.  
  
 Per altre informazioni su questa attività, vedere [Attività Inserimento bulk](../../integration-services/control-flow/file-system-task.md).  
  
 È necessario specificare una gestione connessione di origine e di destinazione impostando le proprietà SourceConnection e DestinationConnection. È possibile specificare i nomi delle gestioni connessione file che puntano ai file utilizzati dall'attività come origine o come destinazione oppure, se i percorsi dei file sono archiviati in variabili, è possibile specificare i nomi delle variabili. Per usare variabili per l'archiviazione dei percorsi dei file, è innanzitutto necessario impostare su **True**l'opzione IsSourcePathVariable per la connessione di origine e l'opzione IsDestinationPathVariable per la connessione di destinazione. È quindi possibile scegliere quali variabili utilizzare tra le variabili di sistema o definite dall'utente esistenti, oppure creare nuove variabili. Nella finestra di dialogo **Aggiungi variabile** è possibile configurare e specificare l'ambito delle variabili. L'ambito deve essere l'attività File system o un contenitore padre. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) e [Utilizzo di variabili nei pacchetti](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787).  
  
> [!NOTE]  
>  Per eseguire l'override delle variabili selezionate per le proprietà **SourceConnection** e **DestinationConnection**, immettere un'espressione per le proprietà **Source** e **Destination**. Le espressioni devono essere immesse nella pagina **Espressioni** di **Editor attività File system**. Ad esempio, per impostare il percorso dei file utilizzati dall'attività come destinazione, potrebbe essere necessario utilizzare la variabile A in determinate condizione e la variabile B in altre.  
  
> [!NOTE]  
>  L'attività File system opera su un singolo file o directory. Pertanto, questa attività non supporta l'utilizzo di caratteri jolly per eseguire la stessa operazione su più file o directory. Affinché l'attività File system ripeta un'operazione su più file o directory, inserirla in un contenitore Ciclo Foreach. Per altre informazioni, vedere [Attività File system](../../integration-services/control-flow/file-system-task.md).  
  
 Con le espressioni è possibile utilizzare variabili differenti per  
  
## <a name="options"></a>Opzioni  
 **IsDestinationPathVariable**  
 Consente di specificare se il percorso di destinazione è archiviato in una variabile. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**True**|Il percorso di destinazione è archiviato in una variabile. Se si seleziona questo valore, viene visualizzata l'opzione dinamica **DestinationVariable**.|  
|**False**|Il percorso di destinazione è specificato in una gestione connessione file. Se si seleziona questo valore, viene visualizzata l'opzione dinamica **DestinationConnection**.|  
  
 **OverwriteDestination**  
 Consente di specificare se l'operazione può sovrascrivere i file nella directory di destinazione.  
  
 **Nome**  
 Consente di specificare un nome univoco per l'attività File system. Tale nome viene utilizzato come etichetta nell'icona dell'attività.  
  
> [!NOTE]  
>  I nomi delle attività devono essere univoci all'interno di un pacchetto.  
  
 **Description**  
 Consente di digitare una descrizione dell'attività File system.  
  
 **Operazione**  
 Consente di selezionare l'operazione di file system da eseguire. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|**Copia directory**|Consente di copiare una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione.|  
|**Copia file**|Consente di copiare un file. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione.|  
|**Crea directory**|Consente di creare una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per una directory di origine e di destinazione.|  
|**Elimina directory**|Consente di eliminare una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine.|  
|**Elimina contenuto directory**|Consente di eliminare il contenuto di una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine.|  
|**Elimina file**|Consente di eliminare un file. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine.|  
|**Sposta directory**|Consente di spostare una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione.|  
|**Sposta file**|Consente di spostare un file. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione. Quando si sposta un file, non includere un nome file nel percorso della directory che si fornisce come destinazione.|  
|**Rinomina file**|Consente di rinominare un file. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione. Quando si rinomina un file, includere il nuovo nome file nel percorso della directory che si fornisce come destinazione.|  
|**Imposta attributi**|Consente di impostare gli attributi di un file o di una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e l'operazione.|  
  
 **IsSourcePathVariable**  
 Consente di specificare se il percorso di destinazione è archiviato in una variabile. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|Valore||  
|-----------|-|  
|**True**|Il percorso di destinazione è archiviato in una variabile. Se si seleziona questo valore, viene visualizzata l'opzione dinamica **SourceVariable**.|  
|**False**|Il percorso di destinazione è specificato in una gestione connessione file. Se si seleziona questo valore, viene visualizzata l'opzione dinamica **DestinationVariable**.|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a>Opzioni dinamiche di IsDestinationPathVariable  
  
### <a name="isdestinationpathvariable--true"></a>IsDestinationPathVariable = True  
 **DestinationVariable**  
 Selezionare il nome della variabile nell'elenco oppure fare clic su \< **nuova variabile...** > per creare una nuova variabile.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Aggiungi variabile](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="isdestinationpathvariable--false"></a>IsDestinationPathVariable = False  
 **DestinationConnection**  
 Selezionare una gestione connessione File nell'elenco oppure fare clic su \< **nuova connessione...** > per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## <a name="issourcepathvariable-dynamic-options"></a>Opzioni dinamiche di IsSourcePathVariable  
  
### <a name="issourcepathvariable--true"></a>IsSourcePathVariable = True  
 **SourceVariable**  
 Selezionare il nome della variabile nell'elenco oppure fare clic su \< **nuova variabile...** > per creare una nuova variabile.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Aggiungi variabile](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="issourcepathvariable--false"></a>IsSourcePathVariable = False  
 **SourceConnection**  
 Selezionare una gestione connessione File nell'elenco oppure fare clic su \< **nuova connessione...** > per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## <a name="operation-dynamic-options"></a>Opzioni dinamiche di Operation  
  
### <a name="operation--set-attributes"></a>Operation = Imposta attributi  
 **Hidden**  
 Consente di specificare se il file o la directory è visibile.  
  
 **ReadOnly**  
 Consente di specificare se il file è di sola lettura.  
  
 **Archive**  
 Consente di specificare se il file o la directory è pronta per l'archiviazione.  
  
 **Di sistema**  
 Consente di specificare se il file è un file di sistema.  
  
### <a name="operation--create-directory"></a>Operation = Crea directory  
 **UseDirectoryIfExists**  
 Indica se l'operazione **Crea directory** usa una directory esistente con il nome specificato anziché creare una nuova directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
  
