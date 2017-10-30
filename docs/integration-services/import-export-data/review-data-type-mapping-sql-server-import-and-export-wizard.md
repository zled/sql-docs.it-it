---
title: Esaminare il tipo di dati di Mapping (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.reviewissues.f1
ms.assetid: 0625c4f9-b8ff-4593-b884-39398b9d43af
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c9ddeba48bde846c4c3494fef62d946bab792984
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="review-data-type-mapping-sql-server-import-and-export-wizard"></a>Verifica mapping tra i tipi di dati (Importazione/Esportazione guidata SQL Server)
Se nell'elenco **Mapping** della finestra di dialogo **Mapping colonne** è stato specificato un mapping tra i tipi di dati che può avere esito negativo, l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Importazione/Esportazione guidata mostra la pagina **Verifica mapping tra i tipi di dati** . In questa pagina è possibile esaminare le informazioni dettagliate sulle conversioni dei tipi di dati da eseguire tramite la procedura guidata per rendere i dati di origine compatibili con la destinazione. Queste informazioni includono segnali visivi per distinguere le conversioni di tipo di dati che dovrebbero avere esito positivo da quelle che possono causare errori o troncamenti. Per ogni conversione, decidere se accettare la conversione suggerita dalla procedura guidata e specificare come gestire gli eventuali errori restituiti.   
  
> [!TIP]
> Nella pagina **Verifica mapping tra i tipi di dati** non è possibile modificare i mapping tra i tipi di dati. È tuttavia possibile fare clic su **Indietro** per tornare alla pagina **Seleziona tabelle e viste di origine** e quindi fare clic su **Modifica mapping** per aprire di nuovo la finestra di dialogo **Mapping colonne** . Nella finestra di dialogo **Mapping colonne** è possibile specificare i mapping tra i tipi di dati che con maggiore probabilità avranno esito positivo. Per altre informazioni sulla finestra **Mapping colonne** , vedere [Mapping colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  
  
## <a name="screen-shot-of-the-review-data-type-mapping-page"></a>Screenshot della pagina Verifica mapping tra i tipi di dati
 La schermata seguente mostra un esempio del **revisione Data Type Mapping** pagina della procedura guidata.
 
 In questo esempio:
 -   L'utente ha specificato un mapping nel **i mapping delle colonne** la finestra di dialogo che potrebbe non riuscire.
 -   L'icona di avviso sulla riga dell'elenco **Tabella** indica che è presente un problema per la conversione di almeno una colonna di dati dai risultati della query a un tipo di dati compatibile nella tabella di destinazione.
 -   L'icona di avviso nella prima riga nel **mapping dei tipi di dati** elenco indica che il mapping tra il **int** il tipo di dati della colonna di origine per il **smalldatetime** tipo di dati di la colonna di destinazione può causare una perdita di dati.
 
 ![Pagina Mapping tipi di dati di verifica dell'importazione / esportazione guidata](../../integration-services/import-export-data/media/review-mapping.png "pagina revisione Data Type Mapping dell'importazione / esportazione guidata") 
 
## <a name="review-the-source-and-destination-tables"></a>Rivedere le tabelle di origine e di destinazione  
 La sezione superiore della pagina **Verifica mapping tra i tipi di dati** è costituita da un elenco **Tabella** contenente le tabelle da copiare dall'origine alla destinazione. Per visualizzare le informazioni di conversione relative a una singola tabella, selezionare una tabella dall'elenco **Tabella** . Le informazioni sulla conversione per le singole colonne della tabella selezionata viene visualizzata nella parte inferiore della pagina di **mapping dei tipi di dati** della griglia.

In questo esempio, i risultati della query fornito dall'utente verranno copiati nella tabella Sales.CustomerNew2 nella destinazione. L'icona di avviso indica che si verifica un problema di conversione almeno una colonna di dati dai risultati della query in un tipo di dati compatibili nella tabella di destinazione.

![Verifica mapping - Tabelle](../../integration-services/import-export-data/media/review-mapping-tables.png)
  
 La tabella seguente descrive le colonne dell'elenco **Tabella** .  
  
|Colonna|Description|  
|------------|-----------------|  
|(Icona di origine)|Indica la probabilità di esito positivo per le conversioni dei tipi di dati:<br /> -   Un'icona raffigurante un segno di spunta **verde** indica che la procedura guidata prevede l'esito positivo di tutte le conversioni dei tipi di dati per la tabella.<br />-   Un'icona di avviso **gialla** indica che è consigliabile verificare le singole conversioni eseguite dalla procedura guidata. Per verificare tali conversioni, selezionare la tabella, quindi controllare le conversioni per singole colonne nell'elenco **Mapping dei tipi di dati** .<br />-   Un'icona di errore **rossa** indica che la procedura guidata non è in grado di eseguire in modo affidabile alcune delle conversioni per la tabella.|  
|**Origine**|Nome della tabella di origine.|  
|(Icona di destinazione)|Indica se la destinazione è già presente o se verrà creata dalla procedura guidata:<br /> -   Un'icona di tabella indica che la destinazione è costituita da una tabella esistente.<br />-   Un'icona di tabella con un riflesso di luce indica che la destinazione è costituita da una nuova tabella che verrà creata dalla procedura guidata.|  
|**Destinazione**|Nome della tabella di destinazione.|  
  
## <a name="review-the-data-type-mappings"></a>Esaminare i mapping dei tipi di dati  
 La parte centrale della pagina **Verifica mapping tra i tipi di dati** è costituita dall'elenco **Mapping dei tipi di dati** . Questa griglia fornisce informazioni dettagliate sulle colonne nella tabella di origine selezionato nella conversione di **tabella** elenco nella parte superiore della pagina.

In questo esempio, ogni colonna di origine verrà copiato a una colonna con lo stesso nome e tipo di dati nella destinazione. L'icona di avviso nella prima riga nel **mapping dei tipi di dati** elenco indica che il mapping tra il **int** il tipo di dati della colonna di origine per il **smalldatetime** tipo di dati di la colonna di destinazione può causare una perdita di dati.
 
![Verifica mapping - Mapping](../../integration-services/import-export-data/media/review-mapping-mappings.png)  

La tabella seguente descrive le colonne dell'elenco **Mapping dei tipi di dati** . 

|Colonna|Description|  
|------------|-----------------|  
|(Icona di conversione)|Indica la probabilità di esito positivo per le conversioni dei tipi di dati:<br /> -   Un'icona raffigurante un segno di spunta **verde** indica che la procedura guidata prevede l'esito positivo della conversione del tipo di dati per la colonna specifica.<br />-   Un'icona di avviso **gialla** indica che è consigliabile verificare la conversione eseguita dalla procedura guidata. Per verificare la conversione, fare doppio clic sulla colonna per visualizzare la finestra di dialogo **Dettagli conversione colonna** . Per altre informazioni, vedere [Finestra di dialogo Dettagli conversione colonna (Importazione/Esportazione guidata SQL Server)](../../integration-services/import-export-data/column-conversion-details-dialog-box-sql-server-import-and-export-wizard.md).<br />-   Un'icona di errore **rossa** indica che la procedura guidata non è in grado di eseguire in modo affidabile la conversione.|  
|**Colonna di origine**|Nome della colonna di origine.|  
|**Tipo origine**|Tipo di dati della colonna di origine.|  
|**Colonna di destinazione**|Nome della colonna di destinazione.|  
|**Tipo destinazione**|Tipo di dati della colonna di destinazione.|  
|**Converti**|Specificare se continuare con la conversione pianificata:<br /> -   Selezionare la casella di controllo per fare in modo che la procedura guidata prosegua con la conversione pianificata.<br />-   Deselezionare la casella di controllo per annullare la conversione del tipo di dati.|  
|**In caso di errore**|Consente di specificare la modalità di gestione degli errori utilizzata dalla procedura guidata:<br /> -   Usare l'impostazione **In caso di errore (globale)** che è possibile specificare nella parte inferiore della pagina.<br />-   Generare un errore e arrestare il processo di importazione o esportazione.<br />-   Ignorare l'errore.|  
|**In caso di troncamento**|Consente di specificare la modalità di gestione del troncamento utilizzata dalla procedura guidata:<br /> -   Usare l'impostazione **In caso di troncamento (globale)** che è possibile specificare nella parte inferiore della pagina.<br />-   Generare un errore e arrestare il processo di importazione o esportazione.<br />-   Ignorare il troncamento.|  

> [!TIP]
> Per visualizzare informazioni dettagliate sulla conversione di una determinata colonna di dati, fare doppio clic su qualsiasi riga dell'elenco. Verrà visualizzata la finestra di dialogo **Dettagli conversione colonna** , che contiene informazioni più dettagliate sulla conversione per la colonna. Per altre informazioni, vedere [Finestra di dialogo Dettagli conversione colonna (Importazione/Esportazione guidata SQL Server)](../../integration-services/import-export-data/column-conversion-details-dialog-box-sql-server-import-and-export-wizard.md).
 
## <a name="specify-global-error-handling-options"></a>Specificare le opzioni di gestione degli errori globali  
 Nella sezione inferiore della pagina **Verifica mapping tra i tipi di dati** è possibile specificare le opzioni di gestione degli errori che verranno applicate per impostazione predefinita a tutte le colonne. Queste impostazioni vengono applicate a tutte le conversioni per cui nella colonna **In caso di errore** o **In caso di troncamento** dell'elenco **Mapping dei tipi di dati** è stata selezionata l'opzione **Usa valore globale** .   

Questo esempio mostra i valori predefiniti per le due opzioni di gestione degli errori globale.

![Verifica mapping - Errori](../../integration-services/import-export-data/media/review-mapping-errors.png)

 **In caso di errore (globale)**  
 Consente di specificare la modalità di gestione degli errori utilizzata dalla procedura guidata:  
 -   Generare un errore e arrestare il processo di importazione o esportazione. Si tratta del valore predefinito.
 -   Ignorare l'errore e continuare il processo di importazione o esportazione.  
  
 **In caso di troncamento (globale)**  
 Specificare la modalità di gestione del troncamento dei dati usata dalla procedura guidata:  
 -   Generare un errore e arrestare il processo di importazione o esportazione. Si tratta del valore predefinito.
 -   Ignorare il troncamento e continuare il processo di importazione o esportazione.  
   
## <a name="whats-next"></a>Operazioni successive  
 Dopo aver verificato gli avvisi e aver specificato le opzioni di conversione e gestione degli errori, dalla pagina **Verifica mapping tra i tipi di dati** tornare alla finestra di dialogo **Mapping colonne** . Per altre informazioni, vedere [Mapping colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>Vedere anche
[Data Type Mapping in the SQL Server Import and Export Wizard](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)


