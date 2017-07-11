---
title: Scaricare SQL Server Management Studio (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 06/27/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 60bdb820d74be98dd051d4729463d375d2a5202a
ms.contentlocale: it-it
ms.lasthandoff: 07/03/2017

---
<a id="download-sql-server-management-studio-ssms" class="xliff"></a>

# Scaricare SQL Server Management Studio (SSMS)
SQL Server Management Studio (SSMS) è un ambiente integrato per la gestione di qualsiasi infrastruttura SQL, da SQL Server al database SQL. SSMS fornisce gli strumenti per configurare, monitorare e amministrare le istanze di SQL Server da qualsiasi posizione venga distribuito. Con SSMS è possibile distribuire, monitorare e aggiornare i componenti livello dati usati dalle applicazioni, nonché creare query e script. 

Questa versione offre una migliore compatibilità con le versioni precedenti di SQL Server, un programma di installazione Web autonomo e notifiche di tipo avviso popup all'interno di SSMS relative alla disponibilità di nuove versioni.  
  
![download](../ssdt/media/download.png) SSMS è gratis! **[Download di SQL Server Management Studio 17.1](https://go.microsoft.com/fwlink/?linkid=849819)** SSMS 17.X è l'ultima generazione di SQL Server Management Studio e supporta SQL Server 2017. 

![download](../ssdt/media/download.png) **[Scaricare il pacchetto di aggiornamento di SQL Server Management Studio 17.1 (per l'aggiornamento dalla versione 17.0 alla versione 17.1)](https://go.microsoft.com/fwlink/?linkid=849821)**

> [!NOTE]
> Il modulo di PowerShell per SQL Server è ora un'installazione separata tramite PowerShell Gallery.  Per altre informazioni, vedere le [istruzioni per il download](download-sql-server-ps-module.md).

<a id="sql-server-management-studio" class="xliff"></a>

## SQL Server Management Studio   
**Informazioni sulla versione**  
  
Numero di versione: 17.1  
Numero di build per questa versione: 14.0.17119.0

<a id="new-in-this-release" class="xliff"></a>

## Novità in questa versione  

SSMS 17.1 è il primo aggiornamento alla generazione 17.X di SQL Server Management Studio.  La generazione 17.X fornisce supporto per quasi tutte le aree di funzionalità da SQL Server 2008 fino a SQL Server 2017.  La versione 17.X è anche la generazione di SSMS che supporta SQL Analysis Services PaaS.

La versione 17.1 include:

* Correzioni per vari problemi segnalati dagli utenti 
* Un nuovo strumento per la gestione della scalabilità orizzontale di Integration Services

Per l'elenco completo delle modifiche, vedere   
                [SQL Server Management Studio: log delle modifiche (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md)  
   
Per informazioni sulla raccolta dei dati utente, vedere   
                [Informativa sulla privacy di SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx) 
  
<a id="supported-sql-offerings" class="xliff"></a>

## Offerte di SQL supportate
  
* Questa versione di SSMS funziona con tutte le [versioni supportate da SQL Server 2008 a SQL Server 2017](https://support.microsoft.com/en-us/lifecycle?C2=1044) e offre il massimo livello di supporto per l'uso con le funzionalità cloud più recenti nel database SQL di Azure e in Azure SQL Data Warehouse.  
* Non è presente alcun blocco esplicito per SQL Server 2000 o SQL Server 2005, ma alcune funzionalità potrebbero non funzionare correttamente.  
* È supportata anche l'installazione affiancata di SSMS 17.X e SSMS 16.X o SQL Server 2014 SSMS e versioni precedenti. 
  
<a id="supported-operating-systems" class="xliff"></a>

## Sistemi operativi supportati
  
Se usata con l'ultimo Service Pack disponibile, questa versione di SSMS supporta le piattaforme seguenti:   
- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 (SP1)
- Windows Server 2016
- Windows Server 2012 (64 bit) 
- Windows Server 2012 R2 (64 bit) 
- Windows Server 2008 R2 (64 bit)  

>[!NOTE]
>SSMS 17.X è basato su Visual Studio 2015 Isolated Shell, rilasciato prima di Windows Server 2016. Per Microsoft la compatibilità delle app è molto importante, così come la garanzia che le applicazioni già rilasciate continuino a essere supportate nelle versioni più recenti di Windows. Per ridurre al minimo i problemi durante l'esecuzione di SSMS con Windows Server 2016, verificare che siano stati applicati tutti gli aggiornamenti di SSMS più recenti. In caso di problemi con SSMS in Windows Server 2016, contattare il supporto tecnico, che determinerà se il problema riguarda SSMS, Visual Studio o la compatibilità di Windows e inoltrerà il problema al team appropriato.

<a id="ssms-installation-tips-and-issues" class="xliff"></a>

## Suggerimenti e problemi di installazione di SSMS
**Ridurre al minimo i riavvii durante l'installazione**

- Per ridurre le probabilità che al termine del programma di installazione di SSMS sia necessario il riavvio del computer, eseguire le azioni seguenti:
  - Assicurarsi che sia in esecuzione una versione aggiornata di Visual C++ 2013 Redistributable Package. È obbligatoria la versione 12.00.40649.5 o successiva. È necessaria solo la versione x64.
  - Verificare che la versione di .NET Framework nel computer corrisponda alla versione 4.6.1 o successiva.
  - Chiudere eventuali altre istanze di Visual Studio aperte nel computer.
  - Assicurarsi che nel computer siano installati tutti gli aggiornamenti del sistema operativo più recenti.
  - Le azioni indicate sono in genere necessarie una sola volta. In pochi casi è necessario un riavvio durante aggiornamenti aggiuntivi alla stessa versione principale di SSMS. Per gli aggiornamenti secondari tutti i prerequisiti per SSMS saranno già stati installati nel computer.

- Per visualizzare l'elenco dei problemi noti e delle soluzioni alternative, vedere [SQL Server Management Studio - Note sulla versione](../ssms/sql-server-management-studio-release-notes.md)

<a id="available-languages" class="xliff"></a>

## Lingue disponibili  
> Le versioni di SSMS localizzate in lingue diverse dall'inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) . 
  
Questa versione di SSMS può essere installata nelle lingue seguenti:

SQL Server Management Studio 17.1:<br>
[Cinese (Repubblica popolare cinese)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804) | [Cinese (Taiwan)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412) | [Portoghese (Brasiliano)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

Pacchetto di aggiornamento di SQL Server Management Studio 17.1 (aggiornamento dalla versione 17.0 alla 17.1):<br>
[Cinese (Repubblica popolare cinese)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x804) | [Cinese (Taiwan)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x40a)

<a id="previous-releases" class="xliff"></a>

## Rilasci precedenti  
[Versioni precedenti di SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  
  
<a id="feedback" class="xliff"></a>

## Commenti e suggerimenti  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum (Forum sugli strumenti client di SQL)](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Segnalare un problema o inserire un suggerimento in Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)  
  
<a id="see-also" class="xliff"></a>

## Vedere anche  
[Esercitazione su SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Documentazione di SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[Altri aggiornamenti e Service Pack](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[Scaricare SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)  



