---
title: "Scelta origine dati (Importazione/Esportazione guidata SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.chooseadatasource.f1"
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
caps.latest.revision: 124
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 113
---
# Scelta origine dati (Importazione/Esportazione guidata SQL Server)
  Dopo la pagina di benvenuto, l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mostra **Scelta origine dati**. In questa pagina è necessario fornire informazioni sull'origine dati e su come connettersi a tale origine.
  
Per informazioni sulle origini dati che è possibile usare, vedere [Quali origini dati e destinazioni è possibile usare](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>Screenshot della pagina Scegliere un'origine dati 
Lo screenshot seguente mostra la prima parte della pagina **Scegliere un'origine dati** della procedura guidata.

![Scegliere l'origine](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>Scegliere un'origine dati
 **Origine dati**  
Specificare l'origine dati selezionando un provider di dati che può connettersi all'origine. Nella maggior parte dei casi il provider di dati necessario è deducibile dal nome, che contiene il nome dell'origine, ad esempio SQL Server, Oracle, file flat, Excel e Access.

L'elenco dei provider di dati disponibili nell'elenco **Origine dati** dipende dai provider installati nel computer. Dipende anche dalla procedura guidata che si esegue, se a 64 bit o a 32 bit.

Potrebbero essere disponibili più provider per l'origine dati. In genere è possibile selezionare qualsiasi provider che funziona con l'origine. Ad esempio, per connettersi a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, il provider di dati .NET Framework per SQL Server o il provider Microsoft OLE DB per SQL Server. 

In alcuni casi, è necessario iniziare selezionando un provider di dati generici. Ad esempio, se si dispone di un driver ODBC per l'origine dati, selezionare il provider di dati .NET Framework per ODBC.  
 
Per alcune origini dati, potrebbe essere necessario scaricare il provider di dati da Microsoft o da terze parti. Per informazioni sulle origini dati che è possibile usare, vedere [Quali origini dati e destinazioni è possibile usare](Import%20and%20Export%20Data%20with%20the%20SQL%20Server%20Import%20and%20Export%20Wizard.md\#wizardSources)

## <a name="after-you-choose-a-data-source"></a>Dopo aver scelto un'origine dati
Dopo aver scelto un'origine dati, il resto della proprietà della pagina **Scelta origine dati** ha un numero variabile di opzioni che dipendono dal provider di dati scelto.

Nelle sezioni seguenti vengono elencate le opzioni importanti per alcune origini dati utilizzate di frequente. Non tutte le origini disponibili nell'elenco a discesa **Origine dati** sono descritte in queste sezioni. Per altre opzioni e altri provider, vedere la documentazione specifica del provider. 
  
> [!TIP]  Se l'origine dati richiede una stringa di connessione, è possibile trovare esempi su questo sito di terze parti relativo al [riferimento sulle stringhe di connessione](https://www.connectionstrings.com/).  

## <a name="microsoft-sql-server"></a>Microsoft SQL Server 

### <a name="connect-to-sql-server-with-sql-server-native-client-or-the-microsoft-ole-db-provider-for-sql-server"></a>Connettersi a SQL Server con SQL Server Native Client o al provider Microsoft OLE DB per SQL Server  

SQL Server Native Client e il provider Microsoft OLE DB per SQL Server presentano lo stesso set di opzioni. Ad esempio, la schermata seguente mostra le opzioni per SQL Server Native Client.

![Connessione SQL Server native](../../integration-services/import-export-data/media/sql-server-connection-native.png)

 **Nome server**  
 Consente di digitare il nome o l'indirizzo IP del server che contiene i dati o di scegliere un server dall'elenco.  
  
> [!NOTE] Se si è connessi a una rete con più server, può risultare più facile digitare il nome del server. Se si sceglie l'elenco a discesa, l'esecuzione di una query della rete per tutti i server disponibili può richiedere molto tempo e il nome del server può non essere elencato nei risultati.

Per specificare una porta TCP non standard, digitare una virgola dopo il nome o l'indirizzo IP del server e quindi digitare il numero di porta.
  
 **Usa autenticazione di Windows**  
 Consente di specificare se per l'accesso al database deve essere usata l'autenticazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Per una maggiore sicurezza è consigliabile utilizzare l'autenticazione di Windows.  
  
 **Usa autenticazione di SQL Server**  
 Consente di specificare se per l'accesso al database deve essere usata l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è necessario specificare un nome utente e una password.  
  
 **Nome utente**  
 Consente di specificare un nome utente per la connessione al database quando si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Password**  
 Consente di specificare una password per la connessione al database quando si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Database**  
 Consente di selezionare uno dei database nell'elenco nell'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Aggiorna**  
 Consente di ripristinare l'elenco dei database disponibili facendo clic su **Aggiorna**.  
  
### <a name="connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server"></a>Connettersi a SQL Server con il provider di dati .NET Framework per SQL Server 

Questa pagina illustra un elenco raggruppato delle opzioni per il provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Di seguito sono elencate le opzioni importanti. Le altre opzioni che vengono elencate quando si seleziona questo provider non sono generalmente necessarie per stabilire correttamente la connessione al database di origine di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 

Per altre informazioni, vedere la pagina relativa alle [stringhe di connessione del provider di dati .NET Framework per SQL Server](https://www.connectionstrings.com/sqlconnection/).

![Rete di connessione SQL Server](../../integration-services/import-export-data/media/sql-server-connection-net.png)
  
 **Origine dati**  
 Consente di digitare il nome o l'indirizzo IP del server che contiene i dati o di scegliere un server dall'elenco.  
  
> [!NOTE] Se si è connessi a una rete con più server, può risultare più facile digitare il nome del server. Se si sceglie l'elenco a discesa, l'esecuzione di una query della rete per tutti i server disponibili può richiedere molto tempo e il nome del server può non essere elencato nei risultati.  
 
 Per specificare una porta TCP non standard, digitare una virgola dopo il nome o l'indirizzo IP del server e quindi digitare il numero di porta.
 
 **Catalogo iniziale**  
 Digitare il nome del database di origine o scegliere un database dall'elenco.  
  
 **Sicurezza integrata**  
 Consente di specificare **True** per stabilire la connessione tramite l'autenticazione integrata di Windows, che rappresenta la soluzione consigliata, oppure **False** per connettersi tramite l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si specifica **False**, è necessario immettere un ID utente e una password. Il valore predefinito è **False**.  
  
 **ID utente**  
 Consente di specificare un nome utente per la connessione al database quando si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Password**  
 Consente di specificare una password per la connessione al database quando si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

## <a name="oracle"></a>Oracle

Connettersi a Oracle usando il provider di dati .NET Framework per Oracle oppure il provider Microsoft OLE DB per Oracle. Il provider di dati .NET Framework per Oracle è più facile da configurare ed è illustrato nella schermata seguente.

Per altre informazioni, vedere la pagina relativa alle[ stringhe di connessione del provider di dati .NET Framework per Oracle](https://www.connectionstrings.com/net-framework-data-provider-for-oracle/) o alle [stringhe di connessione del provider Microsoft OLE DB per Oracle](https://www.connectionstrings.com/microsoft-ole-db-provider-for-oracle-msdaora/).

![Connessione Oracle](../../integration-services/import-export-data/media/oracle-connection.png)

## <a name="odbc-data-sources"></a>origini dati ODBC

Per caricare dati da qualsiasi origine che fornisce un driver ODBC, selezionare il provider di dati .NET Framework per ODBC.

Per fornire una stringa di connessione per un'origine dati ODBC, vedere la documentazione relativa al driver ODBC che si desidera usare, o cercare esempi nella pagina relativa al [riferimento sulle stringhe di connessione](https://www.connectionstrings.com/). 

La schermata seguente mostra una connessione ODBC per SQL Server come esempio. La stringa di connessione usata nell'esempio è:

    Driver={SQL Server};Server=(local);Database=TestData;Trusted_Connection=Yes;

Dopo avere immesso la stringa di connessione nel campo **ConnectionString**, la procedura guidata analizza la stringa e consente di visualizzare le singole proprietà e i relativi valori nella sezione **Varie** dell'elenco.

![Connessione ODBC SQL](../../integration-services/import-export-data/media/odbc-connection-sql.png)

## <a name="text-files-flat-files"></a>File di testo (file flat)
 
 Esistono numerose pagine di opzioni per le origini dati di file flat.
 
 ### <a name="general-page"></a>Pagina Generale
 Nella pagina **Generale**, selezionare il file, quindi verificare le impostazioni nella sezione **Formato**.
 
 ![Connessione file flat generale](../../integration-services/import-export-data/media/flat-file-connection-general.png)  
   
Per altre informazioni sulla pagina **Generale**, vedere la pagina di riferimento di Integration Services seguente: [Editor gestione connessione file flat &#40;pagina Generale&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md).  

### <a name="columns-page"></a>Pagina Colonne

 Nella pagina **Colonne** verificare l'elenco di colonne e i delimitatori che la procedura guidata ha identificato.
 
 ![Connessione file flat colonne](../../integration-services/import-export-data/media/flat-file-connection-columns.png)
  
Per altre informazioni sulla pagina **Colonne**, vedere la pagina di riferimento di Integration Services seguente: [Editor gestione connessione file flat &#40;pagina Colonne&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md).

### <a name="advanced-page"></a>Pagina Avanzate

La pagina **Avanzate** mostra informazioni dettagliate su ogni colonna nell'origine dati, inclusi il tipo di dati e le dimensioni.

Nella schermata seguente, si noti che la colonna **id** inizialmente presenta un tipo di dati di stringa.

![Connessione file flat avanzate prima](../../integration-services/import-export-data/media/flat-file-connection-advanced-before.png)

Fare clic su **Suggerisci tipi** per visualizzare la finestra di dialogo **Suggerisci tipi di colonne**. 

![Connessione file flat suggerisci](../../integration-services/import-export-data/media/flat-file-connection-suggest.png)

Dopo aver scelto di opzioni nella finestra di dialogo **Suggerisci tipi di colonne** e aver fatto clic su **OK**, la procedura guidata potrebbe modificare i tipi di dati di alcune delle colonne da importare.

La schermata seguente mostra che la procedura guidata ha riconosciuto che la colonna **id** nell'origine dati è in realtà un numero e non una stringa di testo ed è stato modificato il tipo di dati della colonna da una stringa a un numero intero.

![Connessione file flat avanzate dopo](../../integration-services/import-export-data/media/flat-file-connection-advanced-after.png)
  
Per altre informazioni sulla pagina **Avanzate**, vedere la pagina di riferimento di Integration Services seguente: [Editor gestione connessione file flat &#40;pagina Avanzate&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md).

### <a name="preview-page"></a>Pagina Anteprima

Nella pagina **Anteprima** verificare che l'elenco di colonne e i dati di esempio siano quelli desiderati.

![Anteprima connessione file flat](../../integration-services/import-export-data/media/flat-file-connection-preview.png)

Per altre informazioni sulla pagina **Anteprima**, vedere la pagina di riferimento di Integration Services seguente: [Editor gestione connessione file flat &#40;pagina Anteprima&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md).  
 
## <a name="microsoft-excel"></a>Microsoft Excel

La schermata seguente mostra una connessione di esempio a una cartella di lavoro di Microsoft Excel.

![Connessione di Excel](../../integration-services/import-export-data/media/excel-connection.png) 
 
 **Percorso file di Excel**  
 Consente di specificare il percorso e il nome file del foglio di calcolo dal quale si importano i dati. Ad esempio, **C:\\MyData.xlsx** per un file nel computer locale o **\\\\Sales\\Database\\Northwind.xlsx** per un file in una condivisione di rete. In alternativa, fare clic su **Sfoglia**.  
  
 **Sfoglia**  
 Consente di individuare il foglio di calcolo tramite la finestra di dialogo **Apri**.  

> [!NOTE] La procedura guidata non può aprire un file di Excel protetto da password.

 **Versione di Excel**  
 Selezionare la versione di Excel usata dalla cartella di lavoro di origine.

Per connettersi alla versione di Excel selezionata, può essere necessario scaricare e installare file aggiuntivi. Per altre informazioni, vedere [Download per Excel e Access](Choose%20a%20Data%20Source%20\%28SQL%20Server%20Import%20and%20Export%20Wizard%29.md\#officeDownloads) in questa pagina.

Se si verifica un problema quando si specifica una versione, ad esempio non è possibile installare il runtime di Access 2016 perché si usa Microsoft Office 365, provare a specificare una versione diversa, anche una versione precedente, ad esempio la versione 2013 anziché la versione 2016.

**Nomi di colonna nella prima riga**  
Specificare se la prima riga dei dati di origine contiene nomi di colonna.
-   Se i dati di origine non contengono nomi di colonna e si abilita questa opzione, la procedura guidata considera la prima riga dei dati di origine come nomi di colonna.
-   Se i dati di origine contengono nomi di colonna e si disabilita questa opzione, la procedura guidata considera la riga dei nomi di colonna come prima riga di dati.

Se i dati di origine non contengono nomi di colonna, la procedura guidata usa F1, F2 e così via internamente come intestazioni di colonna temporanee.

## <a name="microsoft-access"></a>Microsoft Access  

La schermata seguente mostra una connessione di esempio a un database Microsoft Access.

![Connessione di accesso](../../integration-services/import-export-data/media/access-connection.png)

 **Nome file**  
 Consente di specificare il percorso e il nome del file di database dal quale si importano i dati. Ad esempio, **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**. In alternativa, fare clic su **Sfoglia**.
 
 >   [!NOTE] La procedura guidata può connettersi a un database di Access solo nel formato di file mdb.  
  
 **Sfoglia**  
 Consente di individuare il file di database tramite la finestra di dialogo **Apri**.  
  
 **Nome utente**  
Consente di specificare un nome utente valido per la connessione al database quando un file di informazioni sul gruppo di lavoro è associato al database.  
  
 **Password**  
Consente di specificare la password dell'utente per la connessione al database quando un file di informazioni sul gruppo di lavoro è associato al database.
 
Se il database è protetto con un'unica password valida per tutti gli utenti, fornire questo valore nella finestra di dialogo **Proprietà di Data Link**. Per aprire la finestra di dialogo **Proprietà di Data Link**, fare clic su **Avanzate**.  
  
 **Avanzate**  
Consente di specificare le opzioni avanzate, ad esempio la password del database o un file di informazioni sul gruppo di lavoro diverso da quello predefinito, mediante la finestra di dialogo **Proprietà di Data Link**.  
  
## <a name="a-nameofficedownloadsaget-the-downloads-you-need-for-excel-and-access"></a><a name="officeDownloads"></a>Download per Excel e Access  
Se non sono già stati installati, potrebbe essere necessario scaricare i componenti di connettività per le origini dati Microsoft Excel e Access.

Le versioni più recenti dei componenti possono aprire file creati da versioni precedenti dei programmi. In alcuni casi le versioni precedenti dei componenti possono aprire anche file creati dalle ultime versioni dei programmi.  
  
Se nel computer è installata una versione a 32 bit di Office, è necessario installare la versione a 32 bit dei componenti. È anche necessario assicurarsi di eseguire la procedura guidata o il pacchetto Integration Services creato dalla procedura guidata in modalità a 32 bit.  
|Versione di Microsoft Office|Scarica|  
|------------------------------|--------------|  
|2007|[Driver di Office System 2007: Data Connectivity Components](https://www.microsoft.com/download/details.aspx?id=23734)|  
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|  
 
 
## <a name="azure-blob-storage"></a>Archiviazione BLOB Azure  
Per usare Origine BLOB di Azure, è necessario installare il Feature Pack di Azure per SSIS. Per altre informazioni, vedere [Azure Feature Pack for Integration Services &#40;SSIS&#41;](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  

>   [!NOTE] Per assicurarsi che Gestione della connessione di archiviazione di Azure e i componenti da cui è usato, tra cui l'origine BLOB, riescano a connettersi a entrambi gli account di archiviazione generici e agli account di archiviazione BLOB, scaricare [qui](https://www.microsoft.com/download/details.aspx?id=49492) la versione più recente del Feature Pack di Azure . Per altre informazioni su questi due tipi di account di archiviazione, vedere [Introduzione ad Archiviazione di Microsoft Azure](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts).

![Connessione all'archiviazione BLOB di Azure](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

 **Usa account Azure**  
 Consente di specificare se usare un account online.
  
 **Nome dell'account di archiviazione**  
 Specificare il nome dell'account di archiviazione di Azure.  
  
**Chiave account**  
Specificare la chiave per l'account di archiviazione di Azure.  
  
 **Usa HTTPS**  
 Specificare se usare HTTP o HTTPS per connettersi all'account di archiviazione.  
  
 **Usa account per sviluppatore locale**  
 Specificare se usare l'emulatore di archiviazione nel computer locale.  
  
 **Nome del contenitore BLOB**  
 Selezionare dall'elenco dei contenitori di archiviazione disponibili nell'account di archiviazione specificato.  
  
 **Formato del file BLOB**  
 Selezionare il formato di file Testo o Avro.  
  
 **Carattere delimitatore di colonna**  
 Se è stato selezionato il formato Testo, consente di specificare il carattere delimitatore di colonna.  
  
 **Usa la prima riga come nomi di colonna**  
 Specificare se la prima riga di dati contiene nomi di colonna.  
  
## <a name="whats-next"></a>Operazioni successive  
 Dopo avere fornito informazioni sull'origine dei dati e su come connettersi a tale origine, la pagina successiva è **Scelta destinazione**. In questa pagina fornire informazioni sulla destinazione per i dati e su come connettersi a tale destinazione. Per altre informazioni, vedere [Scelta destinazione](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md).  
