---
title: Connettersi a un'origine dati ODBC (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6318776-a188-48a7-995d-9eafd7148ff2
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 0e3ffe2ff1695de69be7149f4be7b42f57b0e991
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-an-odbc-data-source-sql-server-import-and-export-wizard"></a>Connettersi a un'origine dati ODBC (SQL Server importazione / esportazione guidata)
In questo argomento viene illustrato come connettersi a un **ODBC** dell'origine dati dal **scegliere un'origine dati** o **scegliere una destinazione** pagina di SQL Server di importazione / esportazione guidata.

È possibile scaricare il driver ODBC è necessario Microsoft o da terze parti.

Inoltre è possibile cercare le informazioni necessarie per la connessione è necessario fornire. Questo sito di terze parti - [al riferimento di stringhe di connessione](https://www.connectionstrings.com/) -contiene le stringhe di connessione di esempio e altre informazioni sui provider di dati e le informazioni di connessione necessarie.

## <a name="make-sure-the-driver-you-want-is-installed"></a>Verificare che il driver desiderato è installato
1.  Cercare o sfogliare il **origini dati ODBC (64 bit)** applet del Pannello di controllo. Se si dispone solo di un driver a 32 bit, o che è necessario utilizzare un driver a 32 bit, una ricerca per **origini dati ODBC (32 bit)** invece.
2.  Avviare l'applet. Il **Amministrazione origine dati ODBC** verrà visualizzata la finestra.
3.  Nel **driver** scheda, è possibile trovare un elenco di tutti i driver ODBC installati nel computer. (I nomi di alcuni driver potrebbero essere indicati in più lingue).

    Di seguito è riportato un esempio dell'elenco di driver a 64 bit installato.

    ![Installare i driver ODBC a 64 bit](../../integration-services/import-export-data/media/installed-64-bit-odbc-drivers.png)

> [!TIP]
> Se è noto che il driver installato e non è visibile nell'applet a 64 bit, esaminare invece l'applet di 32 bit. Questo inoltre indica se è necessario eseguire a 64 bit o 32 bit SQL Server di importazione / esportazione guidata.
>
> Per utilizzare la versione a 64 bit di SQL Server di importazione / esportazione guidata, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installare solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.
    
## <a name="step-1---select-the-data-source"></a>Passaggio 1: selezionare l'origine dati
Il driver ODBC installati nel computer non sono elencati nell'elenco a discesa delle origini dati. Per connettersi con un driver ODBC, selezionare innanzitutto il **il Provider di dati .NET Framework per ODBC** come origine dati nel **scegliere un'origine dati** o **scegliere una destinazione** pagina della procedura guidata. Questo provider funge da wrapper per il driver ODBC.

Di seguito è riportata la schermata generica che viene visualizzato subito dopo aver selezionato il Provider di dati .NET Framework per ODBC.

![Connettersi a SQL con ODBC prima](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-before.jpg)

## <a name="step-2---provide-the-connection-info"></a>Passaggio 2: fornire le informazioni di connessione
Il passaggio successivo è per fornire le informazioni di connessione per il driver ODBC e l'origine dati. Sono disponibili due opzioni.
1.  Fornire un **DSN** (nome origine dati) già esistente o creato con il **Amministrazione origine dati ODBC** applet del Pannello di controllo. Un DSN viene salvato insieme di impostazioni necessarie per connettersi a un'origine dati ODBC.

    Se già si conosce il nome DSN, o appreso come creare un nuovo nome origine dati a questo punto, è possibile ignorare il resto di questa pagina. Immettere il nome DSN nel **Dsn** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina, quindi continuare con il passaggio successivo della procedura guidata.

    [Fornire un DSN](#odbc_dsn)
    
2.  Fornire un **stringa di connessione**, che è possibile cercare online, oppure creare e testare nel computer con il **Amministrazione origine dati ODBC** applet.

    Se è già la stringa di connessione o come crearlo, è possibile ignorare il resto di questa pagina. Immettere la stringa di connessione nella **ConnectionString** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina, quindi continuare con il passaggio successivo della procedura guidata.

    [Fornire una stringa di connessione](#odbc_connstring)

Se si specifica una stringa di connessione, il **scegliere un'origine dati** o **scegliere una destinazione** pagina vengono visualizzate tutte le informazioni di connessione che la procedura guidata che verrà utilizzata per la connessione all'origine dati, ad esempio di metodo di nome e l'autenticazione server e database. Se si specifica un DSN, queste informazioni non è visibile.

## <a name="odbc_dsn"></a>Opzione 1: specificare un nome DSN
Se si desidera fornire le informazioni di connessione con un DSN (nome dell'origine dati), utilizzare il **Amministrazione origine dati ODBC** applet per trovare il nome dell'origine dati esistente o creare un nuovo nome.
1.  Cercare o sfogliare il **origini dati ODBC (64 bit)** applet del Pannello di controllo. Se si dispone di un driver a 32 bit, o solo è necessario utilizzare un driver a 32 bit, cercare o selezionare **origini dati ODBC (32 bit)** invece.
2.  Avviare l'applet. Il **Amministrazione origine dati ODBC** verrà visualizzata la finestra. Ecco come appare l'applet.

    ![Applet del Pannello di controllo Amministratore ODBC](../../integration-services/import-export-data/media/odbc-administrator-control-panel-applet.png)
    
3.  Se si desidera **utilizzare un DSN esistente** per l'origine dati, è possibile utilizzare qualsiasi DSN visualizzate sul **DSN utente**, **DSN di sistema**, o **DSN su File** scheda. Controllare il nome, quindi tornare alla procedura guidata e immetterlo nel **Dsn** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina. Ignorare il resto di questa pagina e andare al passaggio successivo della procedura guidata.
4.  Se si desidera **creare un nuovo DSN**, decidere se si desidera che sia visibile solo all'utente (DSN utente), visibili a tutti gli utenti del computer tra cui servizi Windows (DSN di sistema) o salvata in un file (DSN su File). Questo esempio crea un nuovo DSN di sistema.
5. Nel **DSN di sistema** scheda, fare clic su **Aggiungi**.

    ![Aggiungere un nuovo DSN di sistema ODBC](../../integration-services/import-export-data/media/add-a-new-odbc-system-dsn.png)
    
6.  Nel **creare una nuova origine dati** la finestra di dialogo, selezionare il driver per l'origine dati, quindi fare clic su **fine**.

    ![Selezionare i driver per nuovo DSN di sistema](../../integration-services/import-export-data/media/pick-driver-for-new-system-dsn.png)
    
7. Il driver verrà visualizzato uno o più schermi specifici del driver dove si immetteranno le informazioni necessarie per la connessione all'origine dati. (Per il driver SQL Server, ad esempio, esistono quattro pagine di impostazioni personalizzate.) Al termine, nell'elenco viene visualizzato il nuovo sistema DSN.

    ![Nuovo DSN di sistema nell'elenco](../../integration-services/import-export-data/media/new-system-dsn-in-list.png)
    
8.  Tornare alla procedura guidata e immettere il nome DSN nel **Dsn** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina. Andare al passaggio successivo della procedura guidata.

## <a name="odbc_connstring"></a>Opzione 2: fornire una stringa di connessione
Se si desidera fornire le informazioni di connessione con una stringa di connessione, il resto di questo argomento contiene di ottenere la stringa di connessione che è necessario.

In questo esempio verrà utilizzata la seguente stringa di connessione, si connette a Microsoft SQL Server.

    Driver={ODBC Driver 13 for SQL Server};server=localhost;database=WideWorldImporters;trusted_connection=Yes;

Immettere la stringa di connessione nella **ConnectionString** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina. Dopo avere immesso la stringa di connessione, la procedura guidata analizza la stringa e visualizza le singole proprietà e i relativi valori nell'elenco.

Di seguito è riportata la schermata che viene visualizzato dopo aver immesso la stringa di connessione.

![Connettersi a SQL con ODBC dopo](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

> [!NOTE]
> Se si configura l'origine o destinazione, le opzioni di connessione per un driver ODBC sono gli stessi. Ovvero le opzioni disponibili sono gli stessi in entrambi i **scegliere un'origine dati** e **scegliere una destinazione** pagine della procedura guidata.

## <a name="get-the-connection-string-online"></a>Ottenere la stringa di connessione in linea
Per trovare stringhe di connessione per il driver ODBC in linea, vedere [al riferimento di stringhe di connessione](https://www.connectionstrings.com/). In questo sito di terze parti sono stringhe di connessione di esempio e altre informazioni sui provider di dati e le informazioni di connessione che richiedono.

## <a name="get-the-connection-string-with-an-app"></a>Ottenere la stringa di connessione a un'app
Per compilare e testare la stringa di connessione per il driver ODBC nel proprio computer, è possibile utilizzare il **Amministrazione origine dati ODBC** applet del Pannello di controllo. Creare un DSN su File per la connessione, quindi copiare le impostazioni di DSN su File per assemblare la stringa di connessione. Richiede diversi passaggi, ma consente di assicurarsi di disporre di una stringa di connessione valido.

1.  Cercare o sfogliare il **origini dati ODBC (64 bit)** applet del Pannello di controllo. Se si dispone di un driver a 32 bit, o solo è necessario utilizzare un driver a 32 bit, cercare o selezionare **origini dati ODBC (32 bit)** invece.
2.  Avviare l'applet. Il **Amministrazione origine dati ODBC** verrà visualizzata la finestra.
3.  Passare quindi al **DSN su File** dell'applet. Scegliere **Aggiungi**.

    Per questo esempio, creare un DSN su File anziché un DSN utente o DSN di sistema, poiché il DSN su File Salva le coppie nome-valore nel formato specifico richiesto per la stringa di connessione.

    ![Aggiungere un nuovo file ODBC DSN](../../integration-services/import-export-data/media/add-a-new-odbc-file-dsn.png)

4.  Nel **Crea nuova origine dati** nella finestra di dialogo selezionare i driver nell'elenco e quindi fare clic su **Avanti**. In questo esempio sta per creare un DSN che contiene gli argomenti di stringa di connessione che è necessario connettersi a Microsoft SQL Server.

    ![Creare una nuova origine dati ODBC](../../integration-services/import-export-data/media/create-new-odbc-data-source.png)
    
5.  Selezionare un percorso e immettere un nome per il nuovo DSN su File e quindi fare clic su **Avanti**. Tenere presente che in cui salvare il file in modo è possibile individuarlo e aprirlo in un passaggio successivo.

    ![Salvare di nuovo DSN su File](../../integration-services/import-export-data/media/save-new-file-dsn.png)

6.  Esaminare il riepilogo delle selezioni e quindi fare clic su **fine**.

7.  Dopo aver fatto clic **fine**, il driver selezionato vengono visualizzati uno o più schermi proprietari per raccogliere le informazioni necessarie per la connessione. In genere queste info include server, informazioni di accesso e database per le origini dati basate su server e file di formato e versione per le origini dati basate su file.

8. Dopo aver configurato l'origine dati e fare clic su **fine**, in genere di visualizzare un riepilogo delle selezioni e avere la possibilità di eseguirne il test.

    ![DSN File nuovo test](../../integration-services/import-export-data/media/test-new-file-dsn.png)

9. Dopo aver verificato l'origine dati e chiudere le finestre di dialogo, è possibile trovare il DSN su File in cui è stato salvato nel file system. Se si non modifica l'estensione di file, l'estensione predefinita è. DSN.

10. Aprire il file salvato con blocco note o un altro editor di testo. Ecco il contenuto di questo esempio di SQL Server.

        [ODBC]  
        DRIVER=ODBC Driver 13 for SQL Server  
        TrustServerCertificate=No  
        DATABASE=WideWorldImporters    
        WSID=<local computer name>  
        APP=Microsoft® Windows® Operating System  
        Trusted_Connection=Yes  
        SERVER=localhost   
        
11. Copiare e incollare i valori necessari in una stringa di connessione in cui le coppie nome-valore sono separate da punti e virgola.

    Dopo assemblare i valori necessari dal file di esempio DSN, è necessario la seguente stringa di connessione.
    
        DRIVER=ODBC Driver 13 for SQL Server;SERVER=localhost;DATABASE=WideWorldImporters;Trusted_Connection=Yes

    Non è in genere necessario tutte le impostazioni in un DSN creati dall'amministratore origine dati ODBC per creare una stringa di connessione appropriata.  
    -   È sempre necessario specificare il driver ODBC.
    -   Per un'origine dati basata su server ad esempio SQL Server, è necessario in genere Server, Database e informazioni di accesso. Nell'esempio di DSN, è necessario TrustServerCertificate, WSID o APP.
    -   Per un'origine dati basata su file, è necessario almeno nome file e percorso.
    
12. Incollare la stringa di connessione nel **ConnectionString** nel campo di **scegliere un'origine dati** o **scegliere una destinazione** pagina della procedura guidata. La procedura guidata analizza la stringa e si è pronti per continuare.

    ![Connettersi a SQL con ODBC dopo](../../integration-services/import-export-data/media/connect-to-sql-with-odbc-after.jpg)

## <a name="see-also"></a>Vedere anche
[Scegliere un'origine dati](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Scegliere una destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)



