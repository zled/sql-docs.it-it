---
title: Cronologia di driver per Microsoft SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 5/4/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
manager: kenvh
ms.openlocfilehash: 2f2f4bafe48018da5c6f634b272a540021fd4ca2
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="driver-history-for-microsoft-sql-server"></a>Cronologia di driver per Microsoft SQL Server

Questa pagina vengono descritti i dati cronologici connessione le tecnologie Microsoft per la connessione a SQL Server.

## <a name="odbc"></a>ODBC

Esistono tre generazioni distinte dei driver Microsoft ODBC per SQL Server. Il driver ODBC di "SQL Server" primo ancora fornito come parte di [Windows Data Access Components](#microsoft-or-windows-data-access-components). Non è consigliabile utilizzare il driver per i nuovi sviluppi. A partire da SQL Server 2005, il [SQL Server Native Client](#sql-server-native-client) include un'interfaccia ODBC e il driver ODBC fornito con SQL Server 2005 tramite SQL Server 2012. Non è consigliabile utilizzare il driver per i nuovi sviluppi. Dopo SQL Server 2012, il [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server) il driver viene aggiornato con le funzionalità di server più recenti in futuro.

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client è una libreria autonoma che viene utilizzata per OLE DB e ODBC. SQL Server Native Client (SNAC spesso abbreviato) è stata inclusa in SQL Server 2005-2012. SQL Server Native Client può essere utilizzato per le applicazioni per trarre vantaggio dalle nuove caratteristiche introdotte in SQL Server 2005 tramite SQL Server 2012. (Microsoft/Windows Data Access Components non vengono aggiornate per queste nuove funzionalità in SQL Server.) Per le nuove funzionalità oltre a SQL Server 2012, SQL Server Native Client non verrà aggiornato. Passare a Microsoft ODBC Driver per SQL Server o il Driver OLE DB Microsoft per SQL Server se si desidera avvalersi delle nuove funzionalità di SQL Server in futuro.

Per una documentazione completa di SQL Server Native Client, vedere la [documentazione di SQL Server Native Client](../relational-databases/native-client/sql-server-native-client-programming.md).

### <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

Dopo SQL Server 2012, sviluppati e rilasciati come Microsoft ODBC Driver for SQL Server primaria ODBC driver for SQL Server. Per altre informazioni, vedere la [Driver Microsoft ODBC per la documentazione di SQL Server](./odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="ole-db"></a>OLE DB

Esistono tre generazioni distinte di provider Microsoft OLE DB per SQL Server. Il primo "Microsoft OLE DB Provider per SQL Server" (SQLOLEDB) ancora fornito come parte di [Windows Data Access Components](#microsoft-or-windows-data-access-components). Questo provider non verrà aggiornato con le nuove funzionalità e non è consigliabile utilizzare il driver per i nuovi sviluppi. A partire da SQL Server 2005, il [SQL Server Native Client](#sql-server-native-client) include un'interfaccia di provider OLE DB (SQLNCLI) e il provider OLE DB fornito con SQL Server 2005 tramite SQL Server 2017. Era [deprecati nel 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) e non è consigliabile utilizzare il driver per i nuovi sviluppi. In 2017, tecnologia di accesso ai dati OLE DB è stato successivamente [undeprecated e un nuovo rilascio pianificato è stato annunciato](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) per 2018. Il nuovo provider OLE DB viene chiamato il "Microsoft OLE DB Driver per SQL Server" (MSOLEDBSQL) attualmente gestiti e supportati.

## <a name="adonet"></a>ADO.NET

ADO.NET è stata introdotta con Microsoft .NET Framework e continua a essere migliorato e gestito. È un componente essenziale di Microsoft .NET Framework. Per altre informazioni, vedere [Microsoft ADO.NET per SQL Server](ado-net/microsoft-ado-net-for-sql-server.md).

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>Microsoft JDBC Driver per SQL Server

Introdotta in 2000, Microsoft JDBC Driver per SQL Server continua a essere migliorato e gestito. Era open source in 2016. Per informazioni aggiornate, inclusa la modalità di scaricare il driver, vedere [Panoramica del Driver JDBC](./jdbc/overview-of-the-jdbc-driver.md).

## <a name="php"></a>PHP

### <a name="microsoft-drivers-for-php-for-sql-server"></a>Driver Microsoft per PHP per SQL Server

Introdotta in 2009 come progetto open source, Microsoft Drivers for PHP per SQL Server continueranno a essere migliorato e gestiti. Per informazioni aggiornate, inclusa la modalità di scaricare il driver PHP, vedere [Microsoft Drivers for PHP per SQL Server](./php/microsoft-php-driver-for-sql-server.md).

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>Driver Microsoft per Node. js per SQL Server

Il Driver Microsoft per Node. js per SQL Server consente alle applicazioni Node. js in Microsoft Windows e Microsoft Windows Azure di accedere a Microsoft SQL Server e Database SQL di Microsoft Windows Azure. Attività di sviluppo sono in corso smette di questo driver. È consigliabile non creare nuove applicazioni che utilizzano il Driver Microsoft per Node. js per SQL Server.

Per ulteriori informazioni sul Driver Microsoft per Node. js per SQL Server, vedere [WindowsAzure / nodo sqlserver](https://github.com/Azure/node-sqlserver).

### <a name="tedious"></a>Noioso

Microsoft contribuisce a attualmente e supporta il modulo noioso open source in Node. js per la connettività a SQL Server utilizzando JavaScript. Per altre informazioni, vedere [Node. js Driver per SQL Server](./node-js/node-js-driver-for-sql-server.md).

## <a name="microsoft-or-windows-data-access-components"></a>Microsoft o Windows Data Access Components

Microsoft/Windows Data Access Components (MDAC/WDAC) fornito con e supportata da Windows per l'applicazione la compatibilità e non fanno parte dello stack di tecnologie di SQL Server corrente. Non verrà aggiunto alcun nuove funzionalità per i componenti in MDAC/WDAC e non è consigliabile usarli per lo sviluppo di nuove applicazioni.

Ai fini di questo documento, è possibile suddividere lo stack MDAC/WDAC nei componenti seguenti, in base a prodotti e tecnologie:

* **ADO** (inclusi ADOMD e ADOX)
* **OLE DB** (inclusi i servizi principali OLE DB, il Provider SQL Server OLE DB, Provider OLE DB Oracle, Provider OLE DB per ODBC (driver), Data Shape Provider e Provider di dati remoto)
* **ODBC** (incluso Gestione Driver ODBC, il Driver ODBC SQL e il Driver ODBC Oracle)

### <a name="mdacwdac-components"></a>Componenti MDAC/WDAC

MDAC/WDAC include questi componenti:

* **ODBC:** l'interfaccia di Microsoft Open Database Connectivity (ODBC) è un'interfaccia di linguaggio di programmazione C che consente alle applicazioni di accedere ai dati da un'ampia gamma di sistemi DBMS (Database Management). Le applicazioni che utilizzano questa API sono limitate per l'accesso alle origini dati relazionali solo.
* **OLE DB:** OLE DB è un set di interfacce COM per l'accesso ai dati in una vasta gamma di archivi dati. Esistono provider OLE DB per l'accesso ai dati nel database, file System, archivi di messaggi, servizi di directory, del flusso di lavoro e gli archivi di documento.
* **ADO:** ActiveX Data Objects (ADO) fornisce un modello di programmazione generale. Sebbene un po' prestazioni inferiori rispetto a codice direttamente per OLE DB o ODBC, ADO è semplice da capire e utilizzare. E può essere utilizzato dai linguaggi di script, ad esempio Microsoft Visual Basic, Scripting Edition (VBScript) o Microsoft JScript.
* **ADOMD:** multidimensionale ADO (ADOMD) viene utilizzato con i provider di dati multidimensionali, ad esempio Provider di Microsoft OLAP, anche noto come Microsoft Analysis Services Provider. Nessun miglioramenti delle funzionalità principali sono stati apportati a esso MDAC 2.0.
* **ADOX:** le estensioni ADO per DDL e protezione (ADOX) consentono la creazione e modifica delle definizioni di un database, tabella, indice o stored procedure. È possibile utilizzare ADOX con qualsiasi provider. Il Provider OLE DB Microsoft Jet fornisce supporto completo per ADOX, mentre il Provider OLE DB Microsoft SQL Server offre un supporto limitato.
* **Librerie di rete di Microsoft SQL Server:** le librerie di rete SQL Server consente SQLOLEDB e SQLODBC comunicare con il database di SQL Server. Le seguenti librerie di rete SQL Server sono state deprecate nelle versioni MDAC/WDAC: Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet e RPC. TCP/IP e Named Pipes continuerà a essere supportato e sono disponibili nel sistema operativo Windows a 64 bit.
* **MSDASQL:** il Provider Microsoft OLE DB per ODBC (MSDASQL) consente alle applicazioni che vengono compilate in OLE DB e ADO (che utilizza internamente OLEDB) per accedere alle origini dati tramite un driver ODBC. MSDASQL è un provider OLEDB che si connette a ODBC, invece di un database. Ha lo scopo come bridge da OLE DB a un driver ODBC quando nessun provider OLE DB diretto è destinato a un'origine dati. MSDASQL viene fornito con il sistema operativo Windows e Windows Server 2008 e Vista SP1 sono stati che le finestre di primo rilascia per includere una versione a 64 bit della tecnologia.

### <a name="deprecated-mdacwdac-components"></a>Componenti MDAC/WDAC deprecati

Questi componenti sono ancora supportati nella versione di MDAC/WDAC corrente, ma potrebbe essere rimossa nelle versioni future. Quando si sviluppano nuove applicazioni, è consigliabile evitare di utilizzare questi componenti. Inoltre, quando si aggiorna o si modificano applicazioni esistenti, rimuovere qualsiasi dipendenza in questi componenti.

* **SQLOLEDB:** il Provider Microsoft OLE DB per SQL Server (SQLOLEDB), che supporta l'accesso a Microsoft SQL Server, è stato deprecato. La connettività alle versioni future di SQL Server potrebbe non essere supportata. La possibilità di connettersi a versioni precedenti a SQL Server 7 verrà rimossi dal sistema operativo dopo Windows 7. Le nuove applicazioni devono utilizzare il Driver OLE DB Microsoft per SQL Server (MSOLEDBSQL), che supporta la nuove funzionalità di SQL Server. Le applicazioni esistenti devono eseguire la migrazione del driver Microsoft OLE DB per SQL Server anche per migliori prestazioni, affidabilità e supporto. Per altre informazioni, vedere [aggiornamento di un'applicazione al Driver OLE DB per SQL Server da MDAC](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).
* **SQLODBC:** di Microsoft SQL Server ODBC Driver (SQLODBC), che supporta l'accesso a Microsoft SQL Server, è stato deprecato. La connettività alle versioni future di SQL Server potrebbe non essere supportata. La possibilità di connettersi a versioni precedenti a SQL Server 7 verrà rimossi dal sistema operativo dopo Windows 7. Le nuove applicazioni devono utilizzare Microsoft ODBC Driver for SQL Server in Windows, che supporta le nuove funzionalità di SQL Server. Le applicazioni esistenti devono eseguire la migrazione a Microsoft ODBC Driver per SQL Server nonché per migliori prestazioni, affidabilità e supporto. Per informazioni, vedere [aggiornamento di un'applicazione a SQL Server Native Client da MDAC](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).
* **Motore di Database Microsoft Jet 4.0:** a partire dalla versione 2.6, MDAC non contiene più componenti di Jet. In altre parole, MDAC 2.6, 2.7 e 2.8 non contengono Microsoft Jet, il Provider OLE DB Microsoft Jet, il driver ODBC di Database Desktop o Jet oggetti DAO (Data Access). I componenti del motore di Database di Microsoft Jet 4.0 passato a uno stato di deprecazione funzionale subito reparto tecnico e non hanno ricevuto i miglioramenti a livello di funzionalità perché diventi una parte di Microsoft Windows in Windows 2000.

  Non è disponibile alcuna versione a 64 bit del motore di Database Jet, il driver OLE DB per Jet, il driver ODBC di Jet o DAO Jet. Per altre informazioni, vedere [articolo della Knowledge Base 957570](http://support.microsoft.com/kb/957570). Nelle versioni a 64 bit di Windows, a 32 bit Jet viene eseguito con il sottosistema WOW64 Windows. Per ulteriori informazioni su WOW64, vedere la [documentazione MSDN WOW64](https://msdn.microsoft.com/library/windows/desktop/aa384274(v=vs.85).aspx). Le applicazioni native a 64 bit non possono comunicare con i driver Jet 32 bit in esecuzione in WOW64.

  Invece di Microsoft Jet, Microsoft consiglia di usare [Microsoft SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express) durante lo sviluppo di nuovo, le applicazioni non Microsoft Access che richiedono un archivio dati relazionale. Queste applicazioni di Jet nuove o convertire possono continuare a usare Jet con l'intenzione di utilizzo di Microsoft Office 2003 e versioni precedenti (con estensione mdb e con estensione xls) per l'archiviazione dei dati non primaria. Tuttavia, per queste applicazioni, è consigliabile pianificare la migrazione da Jet a 2007 Office System Driver. È possibile [scaricare 2007 Office System Driver](https://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=7554f536-8c28-4598-9b72-ef94e038c891), che consente di leggere e scrivere i file preesistenti in Office 2003 (con estensione mdb e con estensione xls) o i formati di file Office 2007 (accdb, *. xlsm, xlsx e *. xlsb).

  > [!IMPORTANT]
  > Leggere il contratto di licenza 2007 Office System utente finale per le limitazioni di utilizzo specifico.

  > [!NOTE]
  > Applicazioni SQL Server può inoltre accedere a Office System 2007 e versioni precedenti, file di integrazione applicativa dei dati eterogenee di SQL Server e Integrations Services anche, funzionalità tramite il Driver di sistema Office 2007. Inoltre, le applicazioni di SQL Server a 64 bit possono accedere a Jet 32 bit e i file di Office System 2007 utilizzando 32 bit SQL Server Integration Services (SSIS) in Windows a 64 bit.

* **MSDADS:** con il Provider Microsoft OLE DB per Data Shaping (MSDADS), è possibile creare relazioni gerarchiche tra le chiavi, campi o i set di righe in un'applicazione. Nessun miglioramenti delle funzionalità principali sono stati apportati MDAC 2.1. Questo Provider è stato deprecato. Si consiglia di usare il codice XML, anziché MSDADS.
* **Oracle ODBC e OLE DB Oracle:** il Driver ODBC per Oracle Microsoft (Oracle ODBC) e il Provider Microsoft OLE DB per Oracle (OLE DB Oracle) forniscono l'accesso ai server di database Oracle. L'azienda vengono compilati utilizzando Oracle Call Interface (OCI) versione 7 e fornisce supporto completo per Oracle 7. Inoltre, Usa emulazione Oracle 7 per fornire un supporto limitato per i database Oracle 8. Oracle non supporta più le applicazioni che utilizzano chiamate versione 7 OCI. Queste tecnologie sono deprecate. Se si utilizza origini dati Oracle, è necessario eseguire la migrazione al provider e driver fornito da Oracle.
* **Servizi Desktop remoto:** servizi di dati remoto (RDS) è un meccanismo di Microsoft proprietario per l'accesso a oggetti Recordset ADO remoti su Internet o Intranet. Servizi Desktop remoto è obsoleta. Nessun miglioramenti delle funzionalità principali sono stati apportati a Servizi Desktop remoto MDAC 2.1. Microsoft ha rilasciato .NET Framework, che dispone di ampie funzionalità di SOAP e sostituisce i componenti di servizi desktop remoto. Tutti i componenti server di servizi desktop remoto verranno rimossi dal sistema operativo dopo Windows 7.
* **JRO:** Jet replica oggetti (JRO) è deprecata. JRO viene utilizzato all'interno di ADO con Jet (*con estensione mdb) i database per creare e comprimere il database Jet (mdb) ed eseguire la gestione della replica Jet. MDAC 2.7 sarà l'ultima versione. JRO non sarà disponibili nel sistema operativo Windows a 64 bit. JRO non è supportato nel formato di file di Microsoft Access 2007 (* accdb).
* **Supporto di ODBC a 16 bit:** se si utilizzano applicazioni a 16 bit, è necessario eseguire la migrazione a un'applicazione a 32 bit. funzionalità di 16 bit è deprecata ed è stato rimosso da sistemi operativi a 64 bit. Per altre informazioni, vedere [articolo della Knowledge base 896458](http://support.microsoft.com/kb/896458).
* **Provider OLE DB semplici (MSDAOSP):** Provider semplice in OLE DB offre un framework per compilare rapidamente i provider OLE DB su dati semplici. MSDAOSP è deprecata.
* **Libreria di cursori ODBC:** libreria di cursori ODBC (Odbccr32) fornisce i cursori limitata dei dati lato client. Libreria di cursori ODBC è deprecata. l'applicazione può utilizzare le implementazioni di cursore sul lato server come una sostituzione.
* **La comunicazione remota dell'interfaccia OLE DB Out-of-Process:** la comunicazione remota di interfaccia OLE DB (msdaps.dll) è stato un tentativo per consentire ai provider OLE DB a esaurirsi processo. La comunicazione remota Out-of-Process interfaccia OLE DB è deprecata.
* **AppleTalk e librerie di rete Banyan Vines SQL:** The Banyan Vines, AppleTalk, ServerNet, IPX/SPX, Giganet e RPC SQL librerie di rete sono deprecate. Se si utilizza una di queste tecnologie, è necessario modificare le applicazioni possono utilizzare una delle altre librerie di rete, ad esempio TCP/IP e Named Pipe.

### <a name="mdacwdac-releases"></a>Versioni MDAC/WDAC

Ecco un elenco degli scenari di supporto delle versioni MDAC/WDAC precedenti, a partire dal meno recente.

* **1.5 MDAC, MDAC 2.0 e 2.1 di MDAC:** queste versioni di MDAC sono stati versioni indipendenti che sono state rilasciate tramite Microsoft Windows NT Option Pack, Microsoft Windows Platform SDK o il sito Web di MDAC. Queste versioni di MDAC non sono più supportate.
* **MDAC 2.5:** questa versione di MDAC è stata inclusa con il sistema operativo Windows 2000. Service Pack di MDAC 2.5 sono stati inclusi in Windows 2000 service Pack corrispondente.
* **MDAC 2.6:** MDAC 2.6 RTM, SP1 e SP2 inclusi con Microsoft SQL Server 2000 RTM, SP1 e SP2, rispettivamente. Inoltre, questi MDAC service pack sono stati rilasciati per il sito Web di MDAC conforme alla pianificazione versione service pack di Microsoft SQL Server 2000. È possibile installare questa versione di MDAC e i relativi service pack su piattaforme Windows 2000, Windows Millennium Edition, Windows NT, Windows 95 e Windows 98. Questa versione di MDAC non è più supportata.
* **MDAC 2.7:** questa versione di MDAC è stata inclusa con i sistemi operativi Microsoft Windows XP RTM e SP1. È possibile installare questa versione di MDAC e i relativi service pack su piattaforme Windows 2000, Windows Millennium Edition, Windows NT e Windows 98. È possibile installare questa versione nella piattaforma Windows XP solo tramite il sistema operativo o il Service Pack. Questa versione di MDAC non è più supportata.
* **MDAC 2.8:** questa versione di MDAC è stata inclusa con Windows Server 2003 e Windows XP SP2 e versioni successive. È anche possibile installare questa versione di MDAC e i relativi service pack in Windows 2000.

  * La versione a 32 bit di MDAC 2.8 è stato inoltre rilasciata per il sito Web di MDAC nello stesso momento che Windows Server 2003 è stato rilasciato al cliente.
  * La versione a 64 bit di MDAC 2.8 è stata rilasciata con la versione a 64 bit di Windows Server 2003 e Windows XP.

* **Windows Data Access Components (WDAC):** MDAC modificato in WDAC - "Windows Data Access Components" a partire da Windows Vista e Windows Server 2008. WDAC è incluso come parte del sistema operativo e non è disponibile separatamente per la ridistribuzione. I servizi per WDAC sono soggetto al ciclo di vita del sistema operativo.

  versioni a 32 e 64 bit di WDAC vengono rilasciate con le versioni a 32 e 64 bit dei sistemi operativi Windows, rispettivamente.

## <a name="obsolete-data-access-technologies"></a>Tecnologie di accesso ai dati obsoleti

Tecnologie obsolete sono tecnologie non avanzate o aggiornati nelle diverse versioni di prodotto e che verranno esclusi rispetto alle versioni future del prodotto. Non usare queste tecnologie quando si scrivono nuove applicazioni. Quando si modificano applicazioni esistenti che vengono scritti utilizzando queste tecnologie, prendere in considerazione la migrazione di tali applicazioni ADO.NET o un'altra tecnologia corrente.

I componenti seguenti sono considerati obsoleti:

* **DB-Library:** DB-Library è un modello di programmazione specifici di SQL Server che include le API di C. Sono non state apportate alcuna modifica in DB-Library dopo SQL Server 6.5. Stato di rilascio della versione finale con SQL Server 2000 e verrà non essere trasferita al sistema operativo Windows a 64 bit.
* **Embedded SQL (E-SQL):** E-SQL è un modello di programmazione specifici di SQL Server che consente di istruzioni Transact-SQL da incorporare nel codice Visual C#. Nessun miglioramenti apportati alle funzionalità sono state apportate alle istruzioni SQL E SQL Server 6.5. Stato di rilascio della versione finale con SQL Server 2000 e verrà non essere trasferita al sistema operativo Windows a 64 bit.
* **Data Access Objects (DAO):** DAO fornisce l'accesso ai database JET (accesso). Questa API può essere usata da Microsoft Visual Basic, Microsoft Visual C++ e linguaggi di scripting. È stato incluso con Microsoft Office 2000 e Office XP. 3.6 DAO è la versione finale di questa tecnologia. Non sarà disponibile nel sistema operativo Windows a 64 bit.
* **Oggetti dati remoti (RDO):** RDO è stato progettato specificamente per l'accesso remoto alle origini dati relazionali ODBC e più semplice utilizzare ODBC senza codice dell'applicazione complesso. È stato incluso con Microsoft Visual Basic le versioni 4, 5 e 6. RDO versione 2.0 è stata la versione finale di questa tecnologia.