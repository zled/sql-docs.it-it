---
title: Scaricare SQL Server Management Studio (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 10/09/2017
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
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: be3d22491e1cf5e6446f9ac597d613e1d203a28e
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Scaricare SQL Server Management Studio (SSMS)

SSMS è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al database SQL. Offre gli strumenti per configurare, monitorare e amministrare le istanze di SQL. SSMS permette di distribuire, monitorare e aggiornare i componenti livello dati usati dalle applicazioni, nonché creare query e script.

È possibile usare SQL Server Management Studio (SSMS) per eseguire query, progettare e gestire database e data warehouse in qualsiasi posizione, nel computer locale o nel cloud.

**SSMS è gratuito.**

SSMS 17.x è l'ultima generazione di *SQL Server Management Studio* e supporta SQL Server 2017.

**[![Download](../ssdt/media/download.png) Scaricare SQL Server Management Studio 17.3](https://go.microsoft.com/fwlink/?linkid=858904)**

**[![Download](../ssdt/media/download.png) Scaricare il pacchetto di aggiornamento di SQL Server Management Studio 17.3 (aggiornamenti dalla versione 17.x alla versione 17.3)](https://go.microsoft.com/fwlink/?linkid=858906)**

L'installazione di SSMS 17.x non aggiorna o sostituisce SSMS 16.x o le versioni precedenti. SSMS 17.x viene installato side-by-side con le versioni precedenti in modo che entrambe le versioni siano disponibili per l'uso.
Se un computer contiene installazioni side-by-side di SSMS, assicurarsi di avviare la versione corretta per le esigenze specifiche. La versione più recente è denominata *Microsoft SQL Server Management Studio 17* e ha una nuova icona: 
 
   ![SSMS 17.x](media/download-sql-server-management-studio-ssms/version-icons.png)


> [!NOTE]
> Il modulo di PowerShell per SQL Server è ora un'installazione separata tramite PowerShell Gallery.  Per altre informazioni, vedere le [istruzioni per il download](download-sql-server-ps-module.md).

## <a name="sql-server-management-studio"></a>SQL Server Management Studio

**Informazioni sulla versione**

Numero di versione: 17.3

Numero di build per questa versione: 14.0.17199.0

## <a name="new-in-this-release"></a>Novità in questa versione

SSMS 17.3 è la versione più recente di SQL Server Management Studio. La generazione 17.x offre il supporto per quasi tutte le aree di funzionalità da SQL Server 2008 fino a SQL Server 2017. La versione 17.x supporta anche SQL Analysis Services PaaS.

La versione 17.3 include:

- È stata aggiunta la nuova procedura guidata "Importa file flat" per semplificare l'importazione di file con estensione CSV mediante un framework intelligente, che richiede livelli minimi di intervento dell'utente o conoscenza specifica dell'argomento. Per informazioni dettagliate, vedere [Import Flat File to SQL Wizard](../relational-databases/import-export/import-flat-file-wizard.md) (Procedura guidata Importa file flat in SQL).
- Nodo "XEvent Profiler" aggiunto a Esplora oggetti. Per altre informazioni, vedere [Usare il profiler XEvent di SQL Server Management Studio](../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Aggiornamento del filtro e della categorizzazione delle attese nel report cronologico attese di Performance Dashboard.
- È stato aggiunto il controllo della sintassi della funzione "Stima".
- È stato aggiunto il controllo della sintassi delle query di gestione librerie esterne.
- È stato aggiunto il supporto SMO per la gestione librerie esterne.
- È stato aggiunto il supporto di "Avvia PowerShell" alla finestra "Server registrati" (è necessario un nuovo modulo SQL PowerShell).
- Always On: è stato aggiunto il [supporto del routing in sola lettura](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) per i gruppi di disponibilità.
- È stata aggiunta un'opzione per l'invio dei dettagli di traccia alla finestra di output per gli accessi "Active Directory - Universale con supporto MFA" (disattivata per impostazione predefinita; deve essere attivata nelle impostazioni utente in "Strumenti > Opzioni > Servizi di Azure > Cloud di Azure > Livello di traccia della finestra di output di ADAL"). 
- Query Store: 
  - L'interfaccia utente di Query Store è accessibile anche quando QDS è OFF, a condizione che abbia registrato dei dati.
  - L'interfaccia utente di Query Store ora visualizza categorie per le attese in tutti i report esistenti. In questo modo i clienti possono sbloccare gli scenari delle prime query in attesa e molto altro ancora.
- L'inclusione delle intestazioni dei parametri di scripting è ora facoltativa (disattivata per impostazione predefinita; può essere attivata nelle impostazioni utente in"Strumenti > Opzioni > Esplora oggetti di SQL Server > Script > Includere l'intestazione dei parametri di scripting") - [Argomento Connect 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).
- La denominazione "RC" è stata rimossa.

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

SQL Server Management Studio 17.3:<br>
[Cinese (Repubblica popolare cinese)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804) | [Cinese (Taiwan)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)

Pacchetto di aggiornamento di SQL Server Management Studio 17.3 (aggiornamento dalla versione 17.x alla 17.3):<br>
[Cinese (Repubblica popolare cinese)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x804) | [Cinese (Taiwan)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x40a)

## <a name="release-notes"></a>Note sulla versione

Di seguito sono riportati problemi e limitazioni della versione 17.3:

**SQL Server Management Studio (SSMS) - Generale**

- Le funzionalità di SSMS riportate di seguito non sono supportate per l'autenticazione di Azure AD tramite agente utente con MFA:
   - La procedura Ottimizzazione guidata motore di database non è supportata per l'autenticazione di Azure AD: è stato rilevato un problema per cui l'utente visualizza un messaggio di errore poco chiaro: "Impossibile caricare il file o l'assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,…" mentre dovrebbe visualizzare il messaggio "Ottimizzazione guidata motore di database non supporta il database SQL di Microsoft Azure. (DTAClient)".
- Il tentativo di analizzare una query in DTA restituisce un errore: "L'oggetto deve implementare IConvertible. (mscorlib)".
- *Query regredite* non è disponibile nell'elenco di report Query Store in Esplora oggetti.
   - Soluzione alternativa: fare clic con il pulsante destro del mouse sul nodo **Query Store** e selezionare **View Regressed Queries** (Visualizza le query regredite).

**Integration Services (IS)**

- [execution_path] in [catalog].[event_messagea] non è corretto per le esecuzioni dei pacchetti in Scale Out. [execution_path] inizia con "\Package" anziché con il nome oggetto dell'eseguibile del pacchetto. Quando si visualizza il report panoramica delle esecuzioni dei pacchetti in SSMS, il collegamento "Percorso di esecuzione" in Panoramica sulle esecuzioni non funziona. La soluzione alternativa consiste nel fare clic su "Visualizzazione messaggi" nel report panoramica per controllare tutti i messaggi di evento.



## <a name="previous-releases"></a>Rilasci precedenti

[Versioni precedenti di SQL Server Management Studio](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>Commenti e suggerimenti

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum (Forum sugli strumenti client di SQL)](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Segnalare un problema o inserire un suggerimento in Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)

## <a name="see-also"></a>Vedere anche

- [Esercitazione su SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Documentazione di SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Altri aggiornamenti e Service Pack](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Scaricare SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)

