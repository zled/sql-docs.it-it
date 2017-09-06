---
title: Scaricare SQL Server Management Studio (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "installazione di ssms, download di ssms, ssms più recente"
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- installazione di sql management studio
- scaricare sql management studio
- ms sql management studio
- installare sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
caps.latest.revision: 145
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 3f12671ace99d5fefc199c7b1c2db31e5b3cfade
ms.openlocfilehash: a689293fadb1a442f94d88cc06a9e7a4ef06650f
ms.contentlocale: it-it
ms.lasthandoff: 08/08/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Scaricare SQL Server Management Studio (SSMS)

SSMS è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al database SQL. Offre gli strumenti per configurare, monitorare e amministrare le istanze di SQL. SSMS permette di distribuire, monitorare e aggiornare i componenti livello dati usati dalle applicazioni, nonché creare query e script.

È possibile usare SQL Server Management Studio (SSMS) per eseguire query, progettare e gestire database e data warehouse in qualsiasi posizione, nel computer locale o nel cloud.

**SSMS è gratuito.**

SSMS 17.x è l'ultima generazione di *SQL Server Management Studio* e supporta SQL Server 2017.

**[![Download](../ssdt/media/download.png) Scaricare SQL Server Management Studio 17.2](https://go.microsoft.com/fwlink/?linkid=854085)**

**[![Download](../ssdt/media/download.png) Scaricare il pacchetto di aggiornamento di SQL Server Management Studio 17.2 (aggiornamenti dalla versione 17.x alla versione 17.2)](https://go.microsoft.com/fwlink/?linkid=854087)**

L'installazione di SSMS 17.x non aggiorna o sostituisce SSMS 16.x o le versioni precedenti. SSMS 17.x viene installato side-by-side con le versioni precedenti in modo che entrambe le versioni siano disponibili per l'uso.
Se un computer contiene installazioni side-by-side di SSMS, assicurarsi di avviare la versione corretta per le esigenze specifiche. La versione più recente è denominata *Microsoft SQL Server Management Studio 17* e ha una nuova icona: 
 
   ![SSMS 17.x](media/download-sql-server-management-studio-ssms/version-icons.png)


> [!NOTE]
> Il modulo di PowerShell per SQL Server è ora un'installazione separata tramite PowerShell Gallery.  Per altre informazioni, vedere le [istruzioni per il download](download-sql-server-ps-module.md).

## <a name="sql-server-management-studio"></a>SQL Server Management Studio

**Informazioni sulla versione**

Numero di versione: 17.2 Numero di build per questa versione: 14.0.17177.0

## <a name="new-in-this-release"></a>Novità in questa versione

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
  - Per impostazione predefinita, in precedenza lo script generato in una nuova installazione era destinato all'ultima versione di SQL Server, attualmente SQL Server 2017.
  - In SSMS 17.2 è stata aggiunta una nuova opzione: *Corrispondenza delle impostazioni dello script con l'origine*. Se impostata su *True*, lo script generato è destinato alla stessa versione e allo stesso tipo ed edizione del motore del server da cui viene eseguito l'inserimento dell'oggetto nello script.
  - Per l'opzione *Corrispondenza delle impostazioni dello script con l'origine*, *True* è l'impostazione predefinita. Le nuove installazioni di SSMS, quindi, eseguono sempre lo scripting di oggetti nella stessa destinazione del server originale.
  - Quando il valore dell'opzione *Corrispondenza delle impostazioni dello script con l'origine* è impostato su *False*, vengono abilitate le normali opzioni di destinazione di scripting e ripristinato il funzionamento precedente.
  - Tutte le opzioni di scripting sono state spostate nella relativa sezione, *Opzioni versione*, e non si trovano più in *Opzioni generali di scripting*.

- Aggiunto il supporto per i cloud nazionali nel ripristino dall'URL.
- I report QueryStoreUI ora supportano metriche aggiuntive, come RowCount, DOP, CLR Time e così via, da sys.query_store_runtime_stats.
- IntelliSense è ora supportato per il database SQL di Azure.
    - https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- Sicurezza: per impostazione predefinita, la finestra di dialogo di connessione non riterrà attendibili i certificati del server e richiederà la crittografia per le connessioni del database SQL di Azure.
- Miglioramenti generali del supporto per SQL Server in Linux:
 - Il nodo Posta elettronica database è nuovamente disponibile.
 - Sono stati risolti alcuni problemi relativi ai percorsi.
 - Miglioramenti della stabilità di Monitoraggio attività.
 - La finestra di dialogo Proprietà connessione consente di visualizzare la piattaforma corretta.
- Il report del server di Performance Dashboard è ora disponibile come report predefinito:
  - Connessione a SQL Server 2008 e versioni successive.
  - Il sottoreport sugli indici mancanti usa l'assegnazione di punteggi per consentire l'identificazione degli indici più utili.
  - Il sottoreport sulle statistiche di attesa cronologiche ora aggrega le attese per categoria. Le attese per inattività e sospensione vengono escluse dal filtro per impostazione predefinita.
  - Nuovo sottoreport sui latch cronologici.
- La ricerca nel nodo showplan permette di cercare tra le proprietà del piano. È possibile cercare facilmente qualsiasi proprietà operatore, come il nome della tabella. Per usare questa opzione quando si visualizza un piano:
  - Fare clic con il pulsante destro del mouse sul piano e scegliere l'opzione Trova nodo nel menu di scelta rapida.
  - Usare CTRL+F.

Per l'elenco completo delle modifiche, vedere [SQL Server Management Studio - Log delle modifiche (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md).

Per informazioni sulla raccolta di dati dell'utente, vedere l'[Informativa sulla privacy di SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx).

## <a name="supported-sql-offerings"></a>Offerte di SQL supportate

* Questa versione di SSMS funziona con tutte le [versioni supportate da SQL Server 2008 a SQL Server 2017](https://support.microsoft.com/lifecycle?C2=1044) e offre il massimo livello di supporto per l'uso con le funzionalità cloud più recenti nel database SQL di Azure e in Azure SQL Data Warehouse.
* Non è presente alcun blocco esplicito per SQL Server 2000 o SQL Server 2005, ma alcune funzionalità potrebbero non funzionare correttamente.
* È supportata anche l'installazione side-by-side di SSMS 17.x con SSMS 16.x o SQL Server 2014 SSMS e versioni precedenti.

## <a name="supported-operating-systems"></a>Sistemi operativi supportati
  
Se usata con l'ultimo Service Pack disponibile, questa versione di SSMS supporta le seguenti piattaforme a 64 bit:
- Windows 10 (64 bit)
- Windows 8.1 (64 bit)
- Windows 8 (64 bit)
- Windows 7 (SP1) (64 bit)
- Windows Server 2016*
- Windows Server 2012 R2 (64 bit)
- Windows Server 2012 (64 bit)
- Windows Server 2008 R2 (64 bit)

\*SSMS 17.x è basato su Visual Studio 2015 Isolated Shell, rilasciato prima di Windows Server 2016. Per Microsoft la compatibilità delle app è molto importante, così come la garanzia che le applicazioni già rilasciate continuino a essere supportate nelle versioni più recenti di Windows. Per ridurre al minimo i problemi durante l'esecuzione di SSMS in Windows Server 2016, verificare che siano stati applicati tutti gli aggiornamenti di SSMS più recenti. In caso di problemi con SSMS in Windows Server 2016, contattare il supporto tecnico, che determinerà se il problema riguarda SSMS, Visual Studio o la compatibilità con Windows. Il team di supporto inoltrerà quindi il problema al team appropriato per ulteriori indagini.

## <a name="ssms-installation-tips-and-issues"></a>Suggerimenti e problemi di installazione di SSMS

### <a name="minimize-installation-reboots"></a>Ridurre al minimo i riavvii durante l'installazione

* Per ridurre le probabilità che al termine del programma di installazione di SSMS sia necessario il riavvio del computer, eseguire le azioni seguenti:
  * Assicurarsi che sia in esecuzione una versione aggiornata di Visual C++ 2013 Redistributable Package. È obbligatoria la versione 12.00.40649.5 o successiva. È necessaria solo la versione x64.
  * Verificare che la versione di .NET Framework nel computer corrisponda alla versione 4.6.1 o successiva.
  * Chiudere eventuali altre istanze di Visual Studio aperte nel computer.
  * Assicurarsi che nel computer siano installati tutti gli aggiornamenti del sistema operativo più recenti.
  * Le azioni indicate sono in genere necessarie una sola volta. In pochi casi è necessario un riavvio durante aggiornamenti aggiuntivi alla stessa versione principale di SSMS. Per gli aggiornamenti secondari tutti i prerequisiti per SSMS sono già stati installati nel computer.

* Per visualizzare l'elenco dei problemi noti e delle soluzioni alternative, vedere [SQL Server Management Studio - Note sulla versione](../ssms/sql-server-management-studio-release-notes.md)

## <a name="available-languages"></a>Lingue disponibili

> [!NOTE]
> Le versioni di SSMS localizzate in lingue diverse dall'inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) .

Questa versione di SSMS può essere installata nelle lingue seguenti:

SQL Server Management Studio 17.2:<br>
[Cinese (Repubblica popolare cinese)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804) | [Cinese (Taiwan)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

Pacchetto di aggiornamento di SQL Server Management Studio 17.2 (aggiornamento dalla versione 17.x alla 17.2):<br>
[Cinese (Repubblica popolare cinese)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x804) | [Cinese (Taiwan)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x40a)

## <a name="release-notes"></a>Note sulla versione

Di seguito sono riportati problemi e limitazioni della versione 17.2:

- Le finestre di query che usano l'autenticazione "Active Directory - Universale con supporto MFA" potrebbero restituire un errore simile al seguente, quando si prova a eseguire una query dopo circa un'ora o più dall'apertura:

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of *ConnectRetryCount* to increase the number of recovery attempts.`

   La riesecuzione della query dovrebbe consentire di superare l'errore e dare esito positivo.

- Le funzionalità di SSMS riportate di seguito non sono supportate per l'autenticazione di Azure AD tramite l'autenticazione universale con MFA:
  - La finestra di progettazione **Nuova tabella/vista** mostra il prompt di accesso obsoleto e non funziona per l'autenticazione di Azure AD.
  - La funzionalità **Modifica le prime 200 righe** non supporta l'autenticazione di Azure AD.
  - Il componente **Server registrato** non supporta l'autenticazione di Azure AD.
  - L'**Ottimizzazione guidata motore di database** non è supportata per l'autenticazione di Azure AD. C'è un problema noto in cui il messaggio di errore mostrato all'utente non è molto utile: *Impossibile caricare il file o l'assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory…*, anziché il messaggio previsto *Ottimizzazione guidata motore di database non supporta il database SQL di Microsoft Azure*  (DTAClient).

**Analysis Services**

- Esplora oggetti in SSAS non visualizza il nome utente dell'autenticazione di Windows nelle proprietà di connessione di Azure Analysis Services.
Per altre informazioni, vedere il [log delle modifiche di SSMS](sql-server-management-studio-changelog-ssms.md).

## <a name="previous-releases"></a>Rilasci precedenti

[Versioni precedenti di SQL Server Management Studio](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>Commenti e suggerimenti

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum (Forum sugli strumenti client di SQL)](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Segnalare un problema o inserire un suggerimento in Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)

## <a name="see-also"></a>Vedere anche

- [Esercitazione su SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Documentazione di SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Altri aggiornamenti e Service Pack](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Scaricare SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)

