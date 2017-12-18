---
title: Eseguire un ciclo su file e tabelle di Excel usando un contenitore Ciclo Foreach | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: a5393c1a-cc37-491a-a260-7aad84dbff68
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 41d1bbd66cb2dc73441e95cfa9573f60ced3358b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="loop-through-excel-files-and-tables-by-using-a-foreach-loop-container"></a>Esecuzione di un ciclo su file e tabelle di Excel utilizzando un contenitore Ciclo Foreach
  In questo argomento vengono illustrate le procedure per l'esecuzione di un ciclo sulle cartelle di lavoro di Excel archiviate in una directory oppure sulle tabelle incluse in una cartella di Excel mediante il contenitore Ciclo Foreach con l'enumeratore appropriato.  
  
### <a name="to-loop-through-excel-files-by-using-the-foreach-file-enumerator"></a>Per eseguire un ciclo su un gruppo di file di Excel mediante Foreach File Enumerator  
  
1.  Creare una variabile stringa che riceverà il percorso e il nome del file di Excel correnti a ogni iterazione del ciclo. Per evitare problemi di convalida, assegnare un percorso e un nome file di Excel validi come valore iniziale della variabile. Nell'espressione di esempio indicata di seguito in questa procedura viene utilizzata una variabile denominata `ExcelFile`.  
  
2.  Facoltativamente, creare un'altra variabile stringa che conterrà il valore dell'argomento Proprietà estese della stringa di connessione a Excel. Tale argomento contiene una serie di valori che specificano la versione di Excel e determinano se la prima riga contiene i nomi delle colonne, nonché se viene utilizzata la modalità di importazione. Nell'espressione di esempio riportata di seguito in questa procedura viene utilizzata una variabile denominata `ExtProperties`, con un valore iniziale "`Excel 8.0;HDR=Yes`".  
  
     Se non si utilizza una variabile per l'argomento Proprietà estese, è necessario aggiungerla manualmente all'espressione contenente la stringa di connessione.  
  
3.  Aggiungere un contenitore Ciclo Foreach alla scheda **Flusso di controllo** . Per informazioni su come configurare il contenitore Ciclo Foreach, vedere [Configurare un contenitore Ciclo Foreach](http://msdn.microsoft.com/library/519c6f96-5e1f-47d2-b96a-d49946948c25).  
  
4.  Nella pagina **Raccolta** dell' **Editor ciclo Foreach**selezionare l'enumeratore Foreach File, quindi specificare la directory in cui si trovano le cartelle di lavoro di Excel e il filtro file (in genere, con estensione xls).  
  
5.  Nella pagina **Mapping variabili** eseguire il mapping dell'indice 0 a una variabile stringa definita dall'utente che riceverà il percorso e il nome del file di Excel corrente a ogni iterazione del ciclo. Nell'espressione di esempio indicata di seguito in questa procedura viene utilizzata una variabile denominata `ExcelFile`.  
  
6.  Chiudere l' **Editor ciclo Foreach**.  
  
7.  Aggiungere una gestione connessione Excel in un pacchetto, come descritto in [Aggiungere, eliminare o condividere una gestione connessione in un pacchetto](http://msdn.microsoft.com/library/6f2ba4ea-10be-4c40-9e80-7efcf6ee9655). Selezionare un file di una cartella di lavoro di Excel esistente per la connessione, per evitare errori di convalida.  
  
    > [!IMPORTANT]  
    >  Per evitare errori di convalida durante la configurazione delle attività e dei componenti dei flussi di dati che usano questa gestione connessione Excel, selezionare una cartella di lavoro di Excel esistente nella finestra di dialogo **Editor gestione connessione Excel**. Questa cartella di lavoro non verrà usata dalla gestione connessione in fase di esecuzione dopo aver configurato un'espressione per la proprietà **ConnectionString** , come descritto nella procedura seguente. Dopo aver creato e configurato il pacchetto, è possibile cancellare il valore della proprietà **ConnectionString** nella finestra Proprietà. Se, tuttavia, si cancella questo valore, la proprietà relativa alla stringa di connessione della gestione connessione Excel non sarà più valida fino a quando non viene eseguito il ciclo Foreach. Per evitare errori di convalida, è pertanto necessario impostare la proprietà **DelayValidation** su **True** nelle attività in cui viene usata la gestione connessione o nel pacchetto.  
    >   
    >  È anche necessario usare il valore predefinito **False** per la proprietà **RetainSameConnection** della gestione connessione Excel. Se si modifica questo valore in **True**, ogni iterazione del ciclo continuerà ad aprire la prima cartella di lavoro di Excel.  
  
8.  Selezionare la nuova gestione connessione Excel, fare clic sulla proprietà **Espressioni** nella finestra Proprietà e quindi fare clic sul pulsante con i puntini di sospensione (...).  
  
9. Nell' **Editor espressioni di proprietà**selezionare la proprietà **ConnectionString** e quindi fare clic sul pulsante con i puntini di sospensione (...).  
  
10. In Generatore di espressioni immettere l'espressione seguente:  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=\"" + @[User::ExtProperties] + "\""  
    ```  
  
     Si noti l'uso del carattere di escape "\\" per le virgolette interne necessarie per racchiudere il valore dell'argomento Extended Properties.  
  
     L'argomento Proprietà estese non è facoltativo. Se non si utilizza una variabile per contenere il relativo valore, è necessario aggiungerla manualmente all'espressione, come indicato nell'esempio seguente per un file di Excel 2003:  
  
    ```  
    "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" +  @[User::ExcelFile] + ";Extended Properties=Excel 8.0"  
    ```  
  
11. Creare attività nel contenitore Ciclo Foreach mediante le quali viene utilizzata la gestione connessione Excel per eseguire le stesse operazioni in ogni cartella di lavoro di Excel corrispondente allo schema e al percorso di file specificati.  
  
### <a name="to-loop-through-excel-tables-by-using-the-foreach-adonet-schema-rowset-enumerator"></a>Per eseguire un ciclo su un gruppo di tabelle mediante Foreach ADO.NET Schema Rowset Enumerator  
  
1.  Creare una gestione connessione ADO.NET che utilizzi il provider OLE DB Microsoft Jet per connettersi a una cartella di lavoro di Excel. Nella pagina Tutte della finestra di dialogo **Gestione connessione** assicurarsi di immettere Excel 8.0 come valore della proprietà Extended Properties. Per altre informazioni, vedere [Add, Delete, or Share a Connection Manager in a Package](http://msdn.microsoft.com/library/6f2ba4ea-10be-4c40-9e80-7efcf6ee9655).  
  
2.  Creare una variabile stringa che riceverà il nome della tabella corrente a ogni iterazione del ciclo.  
  
3.  Aggiungere un contenitore Ciclo Foreach alla scheda **Flusso di controllo** . Per informazioni su come configurare il contenitore Ciclo Foreach, vedere [Configurare un contenitore Ciclo Foreach](http://msdn.microsoft.com/library/519c6f96-5e1f-47d2-b96a-d49946948c25).  
  
4.  Nella pagina **Raccolta** dell' **Editor ciclo Foreach**selezionare Enumeratore Foreach ADO.NET set di righe dello schema.  
  
5.  Selezionare la gestione connessione ADO.NET creata in precedenza come valore di **Connessione**.  
  
6.  Selezionare Tabelle come valore di **Schema**.  
  
    > [!NOTE]  
    >  Nell'elenco di tabelle di una cartella di Excel sono inclusi sia i fogli di lavoro (con suffisso $) sia gli intervalli denominati. Se è necessario applicare un filtro all'elenco per individuare solo fogli di lavoro o solo intervalli denominati, potrebbe essere necessario scrivere appositamente codice personalizzato in un'attività Script. Per altre informazioni, vedere [Uso di file di Excel con l'attività Script](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md).  
  
7.  Nella pagina **Mapping variabili** eseguire il mapping tra l'indice 2 e la variabile stringa creata in precedenza in modo che contenga il nome della tabella corrente.  
  
8.  Chiudere l' **Editor ciclo Foreach**.  
  
9. Creare attività nel contenitore Ciclo Foreach che utilizzano la gestione connessione Excel per eseguire le stesse operazioni in ogni tabella di Excel inclusa nella cartella di lavoro specificata. Se per esaminare il nome della tabella enumerata o per lavorare con ogni tabella si usa un'attività Script, ricordarsi di aggiungere la variabile stringa alla proprietà ReadOnlyVariables dell'attività Script.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare un contenitore Ciclo Foreach](http://msdn.microsoft.com/library/519c6f96-5e1f-47d2-b96a-d49946948c25)   
 [Aggiungere o modificare un'espressione di proprietà](../../integration-services/expressions/add-or-change-a-property-expression.md)   
 [Gestione connessione Excel](../../integration-services/connection-manager/excel-connection-manager.md)   
 [Origine Excel](../../integration-services/data-flow/excel-source.md)   
 [Destinazione Excel](../../integration-services/data-flow/excel-destination.md)   
 [Utilizzo di file di Excel con l'attività Script](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
