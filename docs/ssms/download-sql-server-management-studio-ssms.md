---
title: Scaricare SQL Server Management Studio (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 04/03/2017
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
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: cc827737cec19c11d2102f968dc2b8bc638bda86
ms.lasthandoff: 04/11/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Scaricare SQL Server Management Studio (SSMS)
SQL Server Management Studio (SSMS) è un ambiente integrato per l'accesso, la configurazione, la gestione, l'amministrazione e lo sviluppo di tutti i componenti di SQL Server. SSMS integra un'ampia gamma di strumenti grafici con numerosi editor di script avanzati per consentire a sviluppatori e amministratori di qualsiasi livello di competenza di accedere a SQL Server. Questa versione offre una migliore compatibilità con le versioni precedenti di SQL Server, un programma di installazione Web autonomo e notifiche di tipo avviso popup all'interno di SSMS relative alla disponibilità di nuove versioni.  

    
| ![download](../ssdt/media/download.png) Scaricare SQL Server Management Studio (SSMS)  |  |
|:---|:---|
|**[Scaricare SQL Server Management Studio (16.5.3)](https://go.microsoft.com/fwlink/?LinkID=840946)**|Versione corrente per l'uso in un ambiente di produzione.|
|**[Scaricare SQL Server Management Studio - Versione finale candidata (17.0 RC3)](../ssms/sql-server-management-studio-ssms-release-candidate.md)**|Include il supporto per SQL Server vNext CTP1.3 e viene usata side-by-side con la versione 16.x, ma non è consigliata per l'uso in un ambiente di produzione.| 


> [!NOTE]
> Le versioni di SSMS sono ora contrassegnate numericamente, non sono suddivise per mese. SSMS è gratuito. Non è necessaria una licenza per l'installazione e l'uso.  


## <a name="sql-server-management-studio"></a>SQL Server Management Studio   
**Informazioni sulla versione**  
  
Numero di versione: 16.5.3  
Numero di build per questa versione: 13.0.16106.4
  
**Versioni di SQL Server supportate**  
  
* Questa versione di SSMS funziona con tutte le [versioni supportate di SQL Server (SQL Server 2008 - SQL Server 2016)](https://support.microsoft.com/en-us/lifecycle?C2=1044) e offre il massimo livello di supporto per l'uso con le funzionalità cloud più recenti nel database SQL di Azure e in Azure SQL Data Warehouse.  
* Non è presente alcun blocco esplicito per SQL Server 2000 o SQL Server 2005, ma alcune funzionalità potrebbero non funzionare correttamente.  
* Inoltre, è possibile installare una versione di SSMS 16.x o SSMS 2016 side-by-side con SSMS 2014 e versioni precedenti. 
  
**Sistemi operativi supportati**  
  
Se usata con l'ultimo Service Pack disponibile, questa versione di SSMS supporta le piattaforme seguenti:   
 Windows 10, Windows 8, Windows 8.1, Windows 7 (SP1), Windows Server 2012 (64 bit), Windows Server 2012 R2 (64 bit) e Windows Server 2008 R2 (64 bit)  
   
 **Lingue disponibili**  
> [!NOTE]  
> Le versioni di SSMS localizzate in lingue diverse dall'inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) . 
  
 Questa versione di SSMS può essere installata nelle lingue seguenti:  
[Cinese (Repubblica popolare cinese)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804) | [Cinese (Taiwan)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404) | [Inglese (Stati Uniti)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409) | [Francese](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c)  
[Tedesco](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407) | [Italiano](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410) | [Giapponese](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411) | [Coreano](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412) | [Portoghese (Brasile)](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416) | [Russo](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419) | [Spagnolo](http://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)  

 
## <a name="changelog"></a>Log delle modifiche  

16.5.3

In questa versione sono stati risolti i problemi seguenti:

* Risolto un problema introdotto in SSMS 16.5.2 che causava l'espansione del nodo 'Tabella' quando la tabella aveva più di una colonna di tipo sparse.

* Gli utenti possono distribuire pacchetti SSIS contenenti Gestione connessione OData per connettere una risorsa Microsoft Dynamics AX/CRM Online al catalogo SSIS. Per altre informazioni, vedere [Gestione connessione OData](https://msdn.microsoft.com/library/dn584133.aspx).

* La configurazione di Always Encrypted per una tabella esistente ha esito negativo con errori per gli oggetti correlati. [ID Connect 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* La configurazione di Always Encrypted per un database esistente con più schemi non funziona. [ID Connect 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* La procedura guidata Always Encrypted, Colonna crittografata ha esito negativo a causa del database che contiene viste che fanno riferimento a viste di sistema. [ID Connect 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* Durante la crittografia con Always Encrypted, gli errori derivanti dall'aggiornamento dei moduli dopo la crittografia non vengono gestiti in modo corretto.

* Il menu *Apri recenti* non mostra i file salvati di recente. [ID Connect 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS è lento quando si fa clic con il pulsante destro del mouse su un indice per una tabella (tramite una connessione Internet remota). [ID Connect 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)
 
* Risolto un problema con la barra di scorrimento di SQL Designer. [ID Connect 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Il menu di scelta rapida per le tabelle si blocca momentaneamente 
 
* SSMS in alcuni casi genera eccezioni in Monitoraggio attività e subisce un arresto anomalo. [ID Connect 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* Si verifica un arresto anomalo di SSMS 2016 con l'errore "Il processo è stato terminato a causa di un errore interno del runtime .NET in IP 71AF8579 (71AE0000) con codice di uscita 80131506"





Per l'elenco completo delle funzionalità, vedere   
                [SQL Server Management Studio - Changelog (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md)  
  
Per l'elenco dei problemi noti e delle soluzioni alternative, vedere   
                [Note sulla versione di SQL Server Management Studio](../ssms/sql-server-management-studio-release-notes.md)  
  
Per informazioni sulla raccolta dei dati utente, vedere   
                [Informativa sulla privacy di SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx).  
  
## <a name="previous-releases"></a>Rilasci precedenti  
[Versioni precedenti di SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  
  
## <a name="feedback"></a>Commenti e suggerimenti  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum (Forum sugli strumenti client di SQL)](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Segnalare un problema o inserire un suggerimento in Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Vedere anche  
[Esercitazione su SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Documentazione di SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[Altri aggiornamenti e Service Pack](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[Scaricare SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)  



