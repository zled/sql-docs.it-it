---
title: Iniziare con questo semplice esempio di importazione / esportazione guidata | Documenti Microsoft
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: ea3db39b-698b-4a74-8eb8-21dc7252dc1a
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 59c7e1cc3c31f77652acb21d375e1294bdc93397
ms.openlocfilehash: 9eee58be471d8b39b051c1343f9eb26a2960b6d6
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="get-started-with-this-simple-example-of-the-import-and-export-wizard"></a>Iniziare con questo semplice esempio di importazione / esportazione guidata
Informazioni su cosa accade in SQL Server importazione / esportazione guidata, illustrando in uno scenario comune - importazione di dati da un foglio di calcolo di Excel a un database di SQL Server. Anche se si prevede di utilizzare un'origine diversa e una destinazione diversa, in questo argomento illustra la maggior parte di ciò che è necessario conoscere l'esecuzione della procedura guidata.

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Prerequisito: È la procedura guidata installata nel computer?
Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="heres-the-excel-source-data-for-this-example"></a>Di seguito è l'origine dati di Excel per questo esempio
Ecco i dati di origine che si intende copiare - una piccola tabella a due colonne nel foglio di lavoro WizardWalkthrough della cartella di lavoro di WizardWalkthrough.xlsx Excel.

![Dati di origine Excel](../../integration-services/import-export-data/media/excel-source-data.jpg)

## <a name="heres-the-sql-server-destination-database-for-this-example"></a>Ecco il database di destinazione di SQL Server per questo esempio
Di seguito (in SQL Server Management Studio) è il database di destinazione di SQL Server a cui si desidera copiare i dati di origine. La tabella di destinazione non è presente, che si intende consentire alla procedura guidata crea la tabella per l'utente.

![Database di destinazione di SQL Server](../../integration-services/import-export-data/media/sql-server-destination-database.jpg)

## <a name="step-1---start-the-wizard"></a>Passaggio 1: avviare la procedura guidata
Avviare la procedura guidata dal gruppo di Microsoft SQL Server 2016 nel menu Start di Windows.

![Avvio guidato](../../integration-services/import-export-data/media/start-wizard.jpg)

> [!NOTE]
> Per questo esempio, è possibile selezionare la procedura guidata a 32 bit poiché è la versione a 32 bit di Microsoft Office. Di conseguenza, è necessario utilizzare il provider di dati a 32 bit per connettersi a Excel. Per molte altre origini dati, è possibile selezionare in genere la procedura guidata a 64 bit.
>
> Per utilizzare la versione a 64 bit di SQL Server di importazione / esportazione guidata, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installare solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

Per altre informazioni, vedere [Avviare SQL Server importazione / esportazione guidata](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).

## <a name="step-2---view-the-welcome-page"></a>Passaggio 2: visualizzare la pagina di benvenuto
La prima pagina della procedura guidata è la **iniziale** pagina. 

Probabilmente non si desidera vedere questa pagina, faccio, quindi fare clic su **non visualizzare più questa pagina iniziale**.

![Installazione guidata](../../integration-services/import-export-data/media/welcome-to-the-wizard.jpg)

## <a name="step-3---pick-excel-as-your-data-source"></a>Passaggio 3: selezione di Excel come origine dati
Nella pagina successiva, **scegliere un'origine dati**, si sceglie Microsoft Excel come origine dati. Quindi, è esplorare per selezionare il file di Excel. Infine possibile specificare la versione di Excel utilizzata per creare il file.

![Scegliere l'origine dati di Excel](../../integration-services/import-export-data/media/choose-the-excel-data-source.jpg)

Per ulteriori informazioni sulla connessione in Excel, vedere [Connetti a un'origine dati di Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md). Per ulteriori informazioni su questa pagina della procedura guidata, vedere [scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md).

## <a name="step-4---pick-sql-server-as-your-destination"></a>Passaggio 4: selezione di SQL Server come destinazione di
Nella pagina successiva, **scegliere una destinazione**, scelto Microsoft SQL Server come destinazione di scegliendo uno dei provider di dati nell'elenco che si connette a SQL Server. In questo esempio, si sceglie il **.Net Framework Data Provider per SQL Server**.

La pagina Visualizza un elenco di proprietà del provider. Molti di questi sono impostazioni familiare e i nomi non compatibili. Fortunatamente, per connettersi a qualsiasi database dell'organizzazione, in genere è necessario fornire solo tre tipi di informazioni. È possibile ignorare i valori predefiniti per le altre impostazioni.

|Informazioni necessarie|.NET framework di Provider di dati per la proprietà di SQL Server|
|---|---|
|Nome server|**Data Source**|
|Informazioni di autenticazione (accesso)|**La sicurezza integrata di**; o **ID utente** e **Password**<br/>Se si desidera visualizzare un elenco a discesa dei database nel server, è innanzitutto necessario specificare le informazioni sull'account di accesso valido.|
|Nome database|**Catalogo iniziale**|

![Scegliere la destinazione SQL Server](../../integration-services/import-export-data/media/choose-the-sql-server-destination.jpg)

Per ulteriori informazioni sulla connessione a SQL Server, vedere [connettersi a un'origine dati di SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md). Per ulteriori informazioni su questa pagina della procedura guidata, vedere [scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).

## <a name="step-5---copy-a-table-instead-of-writing-a-query"></a>Passaggio 5: copia di una tabella invece di scrivere una query
Nella pagina successiva, **impostazione copia tabella o Query**, specificare che si desidera copiare l'intera tabella di dati di origine. Non si desidera scrivere una query nel linguaggio SQL per selezionare i dati da copiare.

![Specificare per copiare una tabella](../../integration-services/import-export-data/media/specify-to-copy-a-table.jpg)

Per ulteriori informazioni su questa pagina della procedura guidata, vedere [impostazione copia tabella o Query](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).

## <a name="step-6---pick-the-table-to-copy"></a>Passaggio 6: selezionare la tabella da copiare
Nella pagina successiva, **Selezione origine tabelle e viste**, si seleziona la tabella o tabelle che si desidera copiare dall'origine dati. Quindi eseguire il mapping di ogni tabella di origine selezionato in una tabella di destinazione di nuovo o esistente.

In questo esempio, per impostazione predefinita la procedura guidata ha eseguito il mapping di **WizardWalkthrough$** foglio di lavoro di **origine** colonna in una nuova tabella con lo stesso nome della destinazione di SQL Server. (La cartella di lavoro di Excel contiene solo un singolo foglio di lavoro.)
-   Il segno di dollaro ($) al nome della tabella di origine indica un foglio di lavoro di Excel. (Un oggetto denominato intervallo incluso in Excel è rappresentato da solo il nome.)
-   La forma sull'icona di tabella di destinazione indica che la procedura guidata sta per creare una nuova tabella di destinazione.

![Selezionare la tabella (prima di rinominare)](../../integration-services/import-export-data/media/select-the-table-before-renaming.jpg)

Probabilmente necessario rimuovere il segno di dollaro ($) dal nome della nuova tabella di destinazione.

![Selezionare la tabella (dopo la ridenominazione)](../../integration-services/import-export-data/media/select-the-table-after-renaming.jpg)

Per ulteriori informazioni su questa pagina della procedura guidata, vedere [Selezione origine tabelle e viste](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md).

## <a name="optional-step-7---review-the-column-mappings"></a>Passaggio facoltativo 7 - controllare i mapping di colonna
Prima di lasciare il **Selezione origine tabelle e viste** pagina fare clic facoltativamente sul **Modifica mapping** pulsante per aprire il **i mapping delle colonne** la finestra di dialogo. Di seguito, nel **mapping** tabella, viene visualizzato come la procedura guidata sta per eseguire il mapping di colonne nel foglio di lavoro di origine alle colonne nella nuova tabella di destinazione.

![Visualizza mapping colonne](../../integration-services/import-export-data/media/view-column-mappings.jpg)

Per ulteriori informazioni su questa pagina della procedura guidata, vedere [i mapping delle colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).

## <a name="optional-step-8---review-the-create-table-statement"></a>Passaggio facoltativo 8 - esaminare l'istruzione CREATE TABLE
Mentre il **i mapping delle colonne** la finestra di dialogo è aperta, fare clic su di **modifica SQL** pulsante per aprire la **istruzione SQL Create Table** la finestra di dialogo. Qui viene visualizzato il **CREATE TABLE** istruzione generata dalla procedura guidata per creare la nuova tabella di destinazione. In genere è necessario modificare l'istruzione.

![Istruzione CREATE TABLE View](../../integration-services/import-export-data/media/view-create-table-statement.jpg)

Per ulteriori informazioni su questa pagina della procedura guidata, vedere [istruzione SQL Create Table](../../integration-services/import-export-data/create-table-sql-statement-sql-server-import-and-export-wizard.md).

## <a name="optional-step-9---preview-the-data-to-copy"></a>Passaggio facoltativo, 9 - visualizzare in anteprima i dati da copiare
Dopo aver fatto clic **OK** per chiudere la **istruzione SQL Create Table** finestra di dialogo casella, quindi fare clic su **OK** per chiudere la **i mapping delle colonne** nella finestra di dialogo si è nel **Selezione origine tabelle e viste** pagina. Facoltativamente, fare clic sul **anteprima** pulsante per visualizzare un campione di dati che il verranno da copiare. In questo esempio, è corretto.

![Anteprima dei dati da copiare](../../integration-services/import-export-data/media/preview-data-to-copy.jpg)

Per ulteriori informazioni su questa pagina della procedura guidata, vedere [Anteprima dati](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).

## <a name="step-10---yes-you-want-to-run-the-import-export-operation"></a>Passaggio 10: Sì, si desidera eseguire l'operazione di importazione, esportazione
Nella pagina successiva, **Salva ed Esegui pacchetto**, si lascia **eseguire immediatamente** abilitata per copiare i dati non appena si fa clic su **fine** nella pagina successiva. È possibile ignorare la pagina successiva facendo **fine** sul **Salva ed Esegui pacchetto** pagina.

![Eseguire il pacchetto](../../integration-services/import-export-data/media/run-the-package.jpg)

Per ulteriori informazioni su questa pagina della procedura guidata, vedere [Salva ed Esegui pacchetto](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).

## <a name="step-11---finish-the-wizard-and-run-the-import-export-operation"></a>Passaggio 11: completare la procedura guidata, eseguire l'operazione di importazione, esportazione
Se fa clic su **Avanti** anziché **fine** sul **Salva ed Esegui pacchetto** pagina, quindi nella pagina successiva, **completare la procedura guidata**, viene visualizzato un riepilogo delle attività in corso la procedura guidata per eseguire. Fare clic su **fine** per eseguire l'operazione di esportazione di importazione.

![Completamento procedura guidata](../../integration-services/import-export-data/media/complete-the-wizard.jpg)

Per ulteriori informazioni su questa pagina della procedura guidata, vedere [completare la procedura guidata](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md).

## <a name="step-12---review-what-the-wizard-did"></a>Passaggio 12: esaminare cosa ha la procedura guidata
Nella pagina finale, guardare della procedura guidata al termine di ogni attività, quindi esaminare i risultati. La riga evidenziata indica che la procedura guidata copiato correttamente i dati. Si è finito.

![La procedura guidata ha avuto esito positivo](../../integration-services/import-export-data/media/the-wizard-succeeded.jpg)

Per ulteriori informazioni su questa pagina della procedura guidata, vedere [esecuzione delle operazioni](../../integration-services/import-export-data/performing-operation-sql-server-import-and-export-wizard.md).

## <a name="heres-the-new-table-of-data-copied-to-sql-server"></a>Ecco la nuova tabella di dati copiati in SQL Server
Qui (in SQL Server Management Studio) visualizzare la nuova tabella di destinazione che verrà creato in SQL Server.

![Dati copiati in SQL Server](../../integration-services/import-export-data/media/data-copied-to-sql-server.jpg)

Di seguito (nuovo in SQL Server Management Studio) verranno visualizzati i dati che verrà copiato in SQL Server.

![Dati copiati in SQL Server 2](../../integration-services/import-export-data/media/data-copied-to-sql-server-2.jpg)

## <a name="learn-more"></a>Altre informazioni  
Ulteriori informazioni sul funzionamento della procedura guidata.
-   **Ulteriori informazioni sulla procedura guidata.** Per una panoramica della procedura guidata, vedere [Importare ed esportare dati con l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

-   **Informazioni sui passaggi della procedura guidata.** Se si sta cercando informazioni sui passaggi della procedura guidata, selezionare la pagina desiderata dall'elenco, [i passaggi in SQL Server importazione / esportazione guidata](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). È inoltre disponibile una pagina separata della documentazione per ogni pagina della procedura guidata.

-   **Informazioni su come connettersi a origini dati e destinazioni.** Se si sta cercando informazioni su come connettersi ai dati, selezionare la pagina desiderata dall'elenco, [connessione a origini dati con SQL Server di importazione / esportazione guidata](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). È una pagina separata della documentazione per ognuna delle diverse origini dati di uso comune.



