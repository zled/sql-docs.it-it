---
title: 'Aggiornamento: documentazione di SSMS per SQL Server |Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato per modifiche recenti nella documentazione di SQL Server Management Studio (SSMS) per SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: ssms-sql-server-management-studio
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 917198902baf85f2bae57c9ade9f8d3e29dea357
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Articoli nuovi e aggiornati di recente: SQL Server Management Studio (SSMS) per SQL Server



Quasi ogni giorno Microsoft aggiorna alcuni articoli presenti sul sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **18/07/2017** &nbsp; - &nbsp; **11/09/2017**
- *Area di interesse:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Finestra di output in SQL Server Management Studio](output-window.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Scaricare SQL Server Management Studio (SSMS)](#TitleNum_1)
2. [Connettersi a SQL Server o al database SQL di Azure](#TitleNum_2)
3. [SQL Server Management Studio: log delle modifiche (SSMS)](#TitleNum_3)
4. [Creare e aggiornare le tabelle di database](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-sql-server-management-studio-ssmsdownload-sql-server-management-studio-ssmsmd"></a>1. &nbsp; [Scaricare SQL Server Management Studio (SSMS)](download-sql-server-management-studio-ssms.md)

*Aggiornamento: 07/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 63.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 23260f301f86651061b47065bee43d42c92a7be4 0c2178d96b621b96bfcd2fbb782f24792debb407  (PR=2775  ,  Filename=download-sql-server-management-studio-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=3f12671ace99d5fefc199c7b1c2db31e5b3cfade) -->



SSMS 17.2 è l'ultima versione di SQL Server Management Studio. La generazione 17.x offre il supporto per quasi tutte le aree di funzionalità da SQL Server 2008 fino a SQL Server 2017. La versione 17.x supporta anche SQL Analysis Services PaaS.

La versione 17.2 include:

- Multi-Factor Authentication (MFA).
  - Autenticazione multiutente di Azure AD per l'autenticazione universale con Multi-Factor Authentication (agente utente con MFA).
  - Aggiunto un nuovo campo di input delle credenziali utente per l'autenticazione universale con MFA per supportare l'autenticazione multiutente.
- La finestra di dialogo di connessione supporta ora i cinque metodi di autenticazione seguenti:
  - Autenticazione di Windows
  - autenticazione di SQL Server
  - Active Directory - Universale con supporto MFA
  - Active Directory - Password
  - Active Directory - Integrata

- L'importazione/esportazione di database per la procedura guidata di DacFx ora può usare l'autenticazione universale con MFA.
- Per il supporto API, vedere l'articolo relativo all'[interfaccia IUniversalAuthProvider](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx).
- La libreria gestita ADAL usata dall'autenticazione universale di Azure AD con MFA è stata aggiornata alla versione 3.13.9.
- Una nuova interfaccia CLI supporta l'impostazione di amministrazione di Azure AD per il database SQL e SQL Data Warehouse.

 Per altre informazioni sui metodi di autenticazione di Active Directory, vedere [Autenticazione universale con database SQL e SQL Data Warehouse (supporto SSMS per MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) e [Configurare Multi-Factor Authentication per SQL Server Management Studio e Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La finestra di output include voci per le query eseguite durante l'espansione dei nodi di Esplora oggetti.
- Progettazione viste abilitato per i database SQL di Azure.
- Sono state modificate le opzioni di scripting predefinite per l'inserimento di oggetti nello script da Esplora oggetti in SSMS:



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-connect-to-a-sql-server-or-azure-sql-databaseobjectconnect-to-an-instance-from-object-explorermd"></a>2. &nbsp; [Connettersi a SQL Server o al database SQL di Azure](object/connect-to-an-instance-from-object-explorer.md)

*Aggiornamento: 25/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1) | [Successivo](#TitleNum_3))

<!-- Source markdown line 40.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cfd72893c35c87df96dc8605807e542be28936e2 840981d3a115a15774a8e47ee2f6a0e5c4177b01  (PR=2961  ,  Filename=connect-to-an-instance-from-object-explorer.md  ,  Dirpath=docs\ssms\object\  ,  MergeCommitSha40=21f0cfd102a6fcc44dfc9151750f1b3c936aa053) -->



   ![firewall--../media/connect-to-server/new-firewall-rule.png)

1. Per creare la regola del firewall e connettersi al server fare clic su **OK**.

1. Il server viene visualizzato in **Esplora oggetti** dopo il completamento della connessione:

   ![connected--../media/connect-to-server/connected.png)

**Passaggi successivi**


[Progettare, creare e aggiornare tabelle--../visual-db-tools/design-tables-visual-database-tools.md)

**Vedere anche**


[SQL Server Management Studio (SSMS)--../sql-server-management-studio-ssms.md) [Scaricare SQL Server Management Studio (SSMS)--../download-sql-server-management-studio-ssms.md)

[Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)
[Integration Services](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)
[Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>3. &nbsp; [SQL Server Management Studio: log delle modifiche (SSMS)](sql-server-management-studio-changelog-ssms.md)

*Aggiornamento: 07/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_2) | [Successivo](#TitleNum_4))

<!-- Source markdown line 20.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1733ce3c556db1e51cb27bf830429f2c42e8f97e 2abb24fd6547e438181039d095cbad027473a57e  (PR=2775  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=3f12671ace99d5fefc199c7b1c2db31e5b3cfade) -->



Questo articolo fornisce informazioni dettagliate sugli aggiornamenti, i miglioramenti e le correzioni di bug per le versioni correnti e precedenti di SSMS. Scaricare le [versioni precedenti di SSMS indicate di seguito--#previous-ssms-releases).

**[SSMS 17.2--download-sql-server-management-studio-ssms.md)**


Disponibile a livello generale | Numero di build: 14.0.17177.0

**Miglioramenti**


- Multi-Factor Authentication (MFA).
  - Autenticazione multiutente di Azure AD per l'autenticazione universale con Multi-Factor Authentication (agente utente con MFA).
  - Aggiunto un nuovo campo di input delle credenziali utente per l'autenticazione universale con MFA per supportare l'autenticazione multiutente.
- La finestra di dialogo di connessione supporta ora i cinque metodi di autenticazione seguenti:
  - Autenticazione di Windows
  - autenticazione di SQL Server
  - Active Directory - Universale con supporto MFA
  - Active Directory - Password
  - Active Directory - Integrata

- Esportazione/importazione di database per la procedura guidata di DacFx tramite l'autenticazione universale con MFA.
- Per il supporto API, vedere l'articolo relativo all'[interfaccia IUniversalAuthProvider](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx).
- La libreria gestita ADAL usata dall'autenticazione universale di Azure AD con MFA è stata aggiornata alla versione 3.13.9.
- È stata aggiunta anche una nuova interfaccia CLI che supporta l'impostazione di amministrazione di Azure AD per il database SQL e SQL Data Warehouse.

 Per altre informazioni sui metodi di autenticazione di Active Directory, vedere [Autenticazione universale con database SQL e SQL Data Warehouse (supporto SSMS per MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) e [Configurare Multi-Factor Authentication per SQL Server Management Studio e Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La finestra di output include voci per le query eseguite durante l'espansione dei nodi di Esplora oggetti.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-create-and-update-database-tablesvisual-db-toolsdesign-tables-visual-database-toolsmd"></a>4. &nbsp; [Creare e aggiornare le tabelle di database](visual-db-tools/design-tables-visual-database-tools.md)

*Articolo aggiornato: 25/08/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Precedente](#TitleNum_3))

<!-- Source markdown line 30.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f63884ac2d04889e70c505cb5262c8dd81d73ee7 4b4c7aa5e8a0548405f02d11a66b722219fa78f0  (PR=2961  ,  Filename=design-tables-visual-database-tools.md  ,  Dirpath=docs\ssms\visual-db-tools\  ,  MergeCommitSha40=21f0cfd102a6fcc44dfc9151750f1b3c936aa053) -->



**Creare una tabella**


1. Fare clic con il pulsante destro del mouse sul nodo **Tabelle** nel database e quindi scegliere **Nuovo** > **Tabella**:

    ![Nuova tabella--../media/design-tables/new-table.png)

1. Aggiungere [columns--column-properties-visual-database-tools.md) alla tabella:

    ![progettare una tabella--../media/design-tables/new-table2.png)

1. Chiudere la finestra di progettazione e salvare le modifiche.

**Aggiornare una tabella**


1. Fare clic con il pulsante destro del mouse sulla tabella disponibile nel nodo **Tabelle** del database e quindi scegliere **Progetta**:

   ![Aggiornare una tabella--../media/design-tables/update-table.png)

1. Aggiornare le impostazioni specifiche della tabella:

   ![--../media/design-tables/update-table2.png)

1. Chiudere la finestra di progettazione e salvare le modifiche.

**Vedere anche**


[Tabelle](http://msdn.microsoft.com/82d7819c-b801-4309-a849-baa63083e83f) [Proprietà delle tabelle &#40;Visual Database Tools&#41;--../../ssms/visual-db-tools/table-properties-visual-database-tools.md) [Proprietà delle colonne--column-properties-visual-database-tools.md) [Aggiungere colonne a una tabella--../../relational-databases/tables/add-columns-to-a-table-database-engine.md) [Chiavi primarie ed esterne--../../relational-databases/tables/primary-and-foreign-key-constraints.md) [Indici--../../relational-databases/indexes/indexes.md) [Tipi di dati (Transact-SQL)--../../t-sql/data-types/data-types-transact-sql.md) [Scaricare SQL Server Management Studio (SSMS)--../download-sql-server-management-studio-ssms.md)







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+12): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (5+0): documentazione di **Connetti a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (5+1): documentazione di **Motore di database per SQL**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (19+82): documentazione di **Integration Services per SQL**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (1+8): documentazione di **Linux per SQL**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (12+1): documentazione di **Database relazionali per SQL**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (0+1): documentazione di **Reporting Services per SQL**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (7+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (1+1): documentazione di **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+2): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (1+4): documentazione di **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (4+1): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (0+1): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)



