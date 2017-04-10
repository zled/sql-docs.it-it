---
title: "Scelta destinazione (Importazione/Esportazione guidata SQL Server) | Microsoft Docs"
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
  - "sql13.dts.impexpwizard.chooseadestination.f1"
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
caps.latest.revision: 104
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 95
---
# Scelta destinazione (Importazione/Esportazione guidata SQL Server)
 Dopo aver fornito informazioni sull'origine dei dati e su come connettersi a tale origine, nell'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene visualizzata l'opzione **Scegliere una destinazione**. In questa pagina è possibile specificare informazioni sulla destinazione per i dati e su come connettersi a tale destinazione.
  
Per informazioni sulle destinazioni di dati che è possibile usare, vedere [Quali origini e destinazioni di dati è possibile usare?](Import%20and%20Export%20Data%20with%20the%20SQL%20Server%20Import%20and%20Export%20Wizard.md\#wizardSources). 

## <a name="screen-shot-of-the-destination-page"></a>Screenshot della pagina Destinazione
Lo screenshot seguente mostra la prima parte della pagina **Scegliere una destinazione** della procedura guidata.

![Scegli destinazione](../../integration-services/import-export-data/media/choose-destination.png)

## <a name="choose-a-destination"></a>Scegliere una destinazione
 **Destinazione**  
 Specificare la destinazione selezionando il provider di dati che può importare i dati nella destinazione. Nella maggior parte dei casi il provider di dati necessario è deducibile dal nome, che contiene il nome della destinazione, ad esempio SQL Server, Oracle, file flat, Excel e Access.
 
L'elenco dei provider di dati disponibili nell'elenco **Destinazione** dipende dai provider installati nel computer. Dipende anche dalla procedura guidata che si esegue, se a 64 bit o a 32 bit.

Possono essere disponibili più provider per la destinazione. In genere, è possibile selezionare qualsiasi provider che funziona con la destinazione. Ad esempio, per connettersi a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, il provider di dati .NET Framework per SQL Server o il provider Microsoft OLE DB per SQL Server.
 
In alcuni casi, è necessario iniziare selezionando un provider di dati generici. Ad esempio, se si ha un driver ODBC per la destinazione, selezionare il provider di dati .NET Framework per ODBC.

Per alcune destinazioni può essere necessario scaricare il provider di dati da Microsoft o da terze parti. Per informazioni sulle destinazioni di dati che è possibile usare, vedere [Quali origini e destinazioni di dati è possibile usare?](Import%20and%20Export%20Data%20with%20the%20SQL%20Server%20Import%20and%20Export%20Wizard.md\#wizardSources).

## <a name="after-you-choose-a-destination"></a>Dopo aver scelto una destinazione
Dopo aver scelto una destinazione, il resto della proprietà della pagina **Scegliere una destinazione** ha un numero variabile di opzioni che dipendono dal provider di dati scelto.

Nelle sezioni seguenti vengono elencate le opzioni importanti per alcune destinazioni usate di frequente. Non sono elencate tutte le destinazioni che possono essere disponibili nell'elenco a discesa **Destinazione**. Per altre opzioni e altri provider, vedere la documentazione specifica del provider.

> [!TIP] Se la destinazione richiede una stringa di connessione, è possibile trovare esempi su questo sito di terze parti [The Connection Strings Reference](https://www.connectionstrings.com/) (Riferimento sulle stringhe di connessione).  

## <a name="microsoft-sql-server"></a>Microsoft SQL Server 

Se si vuole creare un nuovo database SQL Server come destinazione, selezionare SQL Server Native Client o il provider Microsoft OLE DB per SQL Server. Se si seleziona il provider di dati .NET Framework per SQL Server, l'opzione per creare un nuovo database non è disponibile.  

### <a name="connect-to-sql-server-with-sql-server-native-client-or-the-microsoft-ole-db-provider-for-sql-server"></a>Connettersi a SQL Server con SQL Server Native Client o al provider Microsoft OLE DB per SQL Server  

SQL Server Native Client e il provider Microsoft OLE DB per SQL Server presentano lo stesso set di opzioni. La schermata seguente mostra le opzioni per SQL Server Native Client come esempio.

![Destinazione SQL Native](../../integration-services/import-export-data/media/sql-native-destination.png)

 **Nome server**  
 Consente di digitare il nome o l'indirizzo IP del server di destinazione o di scegliere un server dall'elenco.  
  
> [!NOTE] Se si è connessi a una rete con più server, può risultare più facile digitare il nome del server. Se si sceglie l'elenco a discesa, l'esecuzione di una query della rete per tutti i server disponibili può richiedere molto tempo e il nome del server può non essere elencato nei risultati.  
 
 Per specificare una porta TCP non standard, digitare una virgola dopo il nome o l'indirizzo IP del server e quindi digitare il numero di porta.
 
 **Usa autenticazione di Windows**  
 Consente di specificare se per l'accesso al database deve essere usata l'autenticazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. L'autenticazione di Windows è la scelta consigliata.  
  
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

Questa pagina illustra un elenco raggruppato delle opzioni per il provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Di seguito sono elencate le opzioni importanti. Le altre opzioni che vengono elencate quando si seleziona questo provider non sono necessarie per stabilire correttamente la connessione al database di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 

Per altre informazioni, vedere [.NET Framework Data Provider for SQL Server connection strings](https://www.connectionstrings.com/sqlconnection/) (Stringhe di connessione del provider di dati .NET Framework per SQL Server).

![Rete di destinazione SQL Server](../../integration-services/import-export-data/media/sql-server-destination-net.png)
  
 **Destinazione**  
 Consente di digitare il nome o l'indirizzo IP del server di destinazione o di scegliere un server dall'elenco.  
  
> [!NOTE] Se si è connessi a una rete con più server, può risultare più facile digitare il nome del server. Se si sceglie l'elenco a discesa, l'esecuzione di una query della rete per tutti i server disponibili può richiedere molto tempo e il nome del server può non essere elencato nei risultati.  
 
 Per specificare una porta TCP non standard, digitare una virgola dopo il nome o l'indirizzo IP del server e quindi digitare il numero di porta.
 
 **Catalogo iniziale**  
 Consente di digitare il nome del database di destinazione, oppure di selezionarne uno nell'elenco.  
  
 **Sicurezza integrata**  
 Consente di specificare **True** per stabilire la connessione tramite l'autenticazione integrata di Windows, che rappresenta la soluzione consigliata, oppure **False** per connettersi tramite l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si specifica **False**, è necessario immettere un ID utente e una password. Il valore predefinito è **False**.  
  
 **ID utente**  
 Consente di specificare un nome utente per la connessione al database quando si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Password**  
 Consente di specificare una password per la connessione al database quando si usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

## <a name="oracle"></a>Oracle

Connettersi a Oracle usando il provider di dati .NET Framework per Oracle oppure il provider Microsoft OLE DB per Oracle. Il provider di dati .NET Framework per Oracle è più facile da configurare ed è illustrato nella schermata seguente.

Per altre informazioni, vedere [.NET Framework Data Provider for Oracle connection strings](https://www.connectionstrings.com/net-framework-data-provider-for-oracle/) (Stringhe di connessione del provider di dati .NET Framework per Oracle) o [Microsoft OLE DB Provider for Oracle connection strings](https://www.connectionstrings.com/microsoft-ole-db-provider-for-oracle-msdaora/) (Stringhe di connessione del provider Microsoft OLE DB per Oracle).

![Destinazione Oracle](../../integration-services/import-export-data/media/oracle-destination.png)

## <a name="odbc-destinations"></a>Destinazioni ODBC

Per salvare dati in qualsiasi destinazione che abbia un driver ODBC, selezionare il provider di dati .NET Framework per ODBC.

Per specificare una stringa di connessione per una destinazione ODBC, vedere la documentazione relativa al driver ODBC che si vuole usare, oppure cercare esempi in [The Connection Strings Reference](https://www.connectionstrings.com/) (Riferimento alle stringhe di connessione). 

La schermata seguente mostra una connessione ODBC a SQL Server come esempio. La stringa di connessione usata nell'esempio è:

    Driver={SQL Server};Server=(local);Database=TestData;Trusted_Connection=Yes;

Dopo aver immesso la stringa di connessione nel campo **ConnectionString**, la procedura guidata analizza la stringa e consente di visualizzare le singole proprietà e i relativi valori nella sezione **Varie** dell'elenco.

![Connessione ODBC a destinazione SQL](../../integration-services/import-export-data/media/odbc-connection-sql-destination.png)

 ## <a name="text-files-flat-files"></a>File di testo (file flat)
 
![Destinazione file flat](../../integration-services/import-export-data/media/flat-file-destination.png)  

**Nome file**  
 Consente di specificare il percorso e il nome del file in cui archiviare i dati. In alternativa, è possibile fare clic su **Sfoglia** per individuare un file.  
  
 **Sfoglia**  
 Consente di individuare un file tramite la finestra di dialogo **Apri**.  
  
 **Impostazioni locali**  
 Consente di specificare l'ID delle impostazioni locali (LCID) che definisce il tipo di ordinamento dei caratteri e i formati di data e ora.  
  
 **Unicode**  
 Indica se utilizzare il formato Unicode. Se si utilizza il formato Unicode, non è necessario specificare una tabella codici.  
  
 **Tabella codici**  
 Consente di specificare la tabella codici per la lingua che si desidera utilizzare.  
  
 **Formato**  
 Consente di indicare se utilizzare la formattazione non allineata a destra, a larghezza fissa o delimitata.  
  
|Valore|Description|  
|-----------|-----------------|  
|Delimitato|Le colonne sono separate da un delimitatore.|  
|A larghezza fissa|Le colonne hanno una larghezza fissa.|  
|Non allineato a destra|I file non allineati a destra sono file in cui ogni colonna ha una larghezza fissa ad eccezione dell'ultima, per la quale viene utilizzato il delimitatore di riga.|  
  
 **Qualificatore di testo**  
 Consente di impostare il qualificatore di testo da utilizzare. È possibile, ad esempio, specificare che ogni colonna di testo sia racchiusa tra virgolette.  
  
 **Nomi di colonne nella prima riga di dati**  
 Consente di indicare se si desidera visualizzare i nomi delle colonne nella prima riga di dati.  
 
 ## <a name="microsoft-excel"></a>Microsoft Excel

>  **Video**: la procedura guidata viene spesso usata per esportare i dati in Excel. Questo video di YouTube della durata di quattro minuti descrive come eseguire l'operazione con istruzioni chiare e semplici. [Using the SQL Server Import and Export Wizard to Export to Excel](https://go.microsoft.com/fwlink/?linkid=829049) (Uso dell'Importazione/Esportazione guidata SQL Server per l'esportazione in Excel). Nel video viene usato [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 2012.

La schermata seguente mostra una connessione di esempio a una cartella di lavoro di Microsoft Excel.

![Destinazione Excel](../../integration-services/import-export-data/media/excel-destination.png) 
 
 **Percorso file di Excel**  
 Consente di specificare il percorso e il nome file del foglio di calcolo nel quale esportare i dati. Ad esempio, **C:\\MyData.xlsx** per un file nel computer locale o **\\\\Sales\\Database\\Northwind.xlsx** per un file in una condivisione di rete. In alternativa, fare clic su **Sfoglia**.   
  
 **Sfoglia**  
 Consente di individuare il foglio di calcolo tramite la finestra di dialogo **Apri**.  

> [!NOTE] La procedura guidata non può aprire un file di Excel protetto da password.

 **Versione di Excel**  
Selezionare la versione di Excel usata dalla cartella di lavoro di destinazione.  

Per connettersi alla versione di Excel selezionata, può essere necessario scaricare e installare file aggiuntivi. Per altre informazioni, vedere [Download per Excel e Access](Choose%20a%20Data%20Source%20\%28SQL%20Server%20Import%20and%20Export%20Wizard%29.md\#officeDownloads) in questa pagina.

Se si verifica un problema quando si specifica una versione, ad esempio non è possibile installare il runtime di Access 2016 perché si usa Microsoft Office 365, provare a specificare una versione diversa, anche una versione precedente, ad esempio la versione 2013 anziché la versione 2016.

**Nomi di colonna nella prima riga**  
Questa opzione non sembra avere effetti su una destinazione Excel. Se la destinazione non include nomi di colonna, il driver non restituisce nomi di colonna, anche quando questa opzione è abilitata. Internamente, la procedura guidata usa F1, F2 e così via come intestazioni di colonna temporanee.
 
## <a name="microsoft-access"></a>Microsoft Access  

La schermata seguente mostra una connessione di esempio a un database Microsoft Access.

![Destinazione Access](../../integration-services/import-export-data/media/access-destination.png)

 **Nome file**  
 Consente di specificare il percorso e il nome del file di database nel quale esportare i dati. Ad esempio, **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**. In alternativa, fare clic su **Sfoglia**.
 
 >   [!NOTE] La procedura guidata può connettersi a un database di Access solo nel formato di file mdb.  
  
 **Sfoglia**  
 Consente di individuare il file di database tramite la finestra di dialogo **Apri**.  
  
 **Nome utente**  
Consente di specificare un nome utente valido per la connessione al database quando un file di informazioni sul gruppo di lavoro è associato al database.  
  
 **Password**  
Consente di specificare la password dell'utente per la connessione al database quando un file di informazioni sul gruppo di lavoro è associato al database.

Se il database è protetto con un'unica password valida per tutti gli utenti, specificare questo valore nella finestra di dialogo **Proprietà di Data Link**. Per aprire la finestra di dialogo **Proprietà di Data Link**, fare clic su **Avanzate**.    
  
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
Per usare Destinazione BLOB di Azure, è necessario installare il Feature Pack di Azure per SSIS. Per altre informazioni, vedere [Azure Feature Pack for Integration Services &#40;SSIS&#41;](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  

>   [!NOTE] Per assicurarsi che Gestione della connessione di archiviazione di Azure e i componenti da cui è usato, tra cui la destinazione BLOB, siano in grado di connettersi a entrambi gli account di archiviazione generici e agli account di archiviazione BLOB, scaricare [qui](https://www.microsoft.com/download/details.aspx?id=49492) la versione più recente del Feature Pack di Azure. Per altre informazioni su questi due tipi di account di archiviazione, vedere [Introduzione ad Archiviazione di Microsoft Azure](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts).

![Destinazione BLOB di Azure](../../integration-services/import-export-data/media/azure-blob-destination.png)

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
 Dopo aver fornito informazioni sulla destinazione dei dati e su come connettersi a tale destinazione, la pagina successiva è **Impostazione copia tabella o query**. In questa pagina è possibile specificare se si vuole copiare un'intera tabella o solo alcune righe. Per altre informazioni, vedere [Impostazione copia tabella o query](../../integration-services/import-export-data/specify-table-copy-or-query-sql-server-import-and-export-wizard.md).  
