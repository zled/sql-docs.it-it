---
title: SQL Server Management Studio - Note sulla versione | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b95337b-80bf-4624-8f5d-cdaf6181d3b8
caps.latest.revision: 51
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 51e336a22d0c1052c48b8e569330aef26f2af094
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-management-studio----release-notes"></a>Note sulla versione di SQL Server Management Studio
Questo articolo illustra la versione disponibile di SQL Server Management Studio.  Questa versione di SQL Server Management Studio (SSMS) è un'installazione autonoma non compresa nel rilascio di SQL Server. L'obiettivo di Microsoft è aggiornarla di frequente con nuove funzionalità, correzioni e supporto alle nuove funzionalità di SQL Server e Database SQL di Azure.  
  
Per installare la versione più recente di SQL Server Management Studio, vedere [Download SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
  
Di seguito è possibile trovare un elenco di problemi e limitazioni relativi a questa versione di SQL Server Management Studio:  

1. **Per un'istanza SSMS è possibile accedere a un solo account di Azure Active Directory con l'Autenticazione universale di Active Directory.**  
    Questa restrizione è limitata all'Autenticazione universale di Active Directory. È invece possibile accedere a server diversi usando l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.
    
    In alternativa, è possibile usare un'altra istanza di SSMS per accedere come un altro dell'account di Azure Active Directory. 
    
2. **I comandi Data-Tier Application Framework (DacFx) e Progettazione schema in SSM non supportano l'Autenticazione universale di Active Directory.**  
    I comandi che usano DacFx, ad esempio importazione ed esportazione, e Progettazione schema in SSMS non supportano attualmente l'Autenticazione universale di Active Directory.
    
    In alternativa, è possibile usare altre forme di autenticazione disponibili in SSMS, come l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.

3. **SSMS può connettersi solo a istanze di SQL Server 2016 Integrated Services (SSIS 2016).**  
    Esiste un limite noto di compatibilità con SQL Server Integration Services che impedisce la connessione a versioni precedenti.
    
    Come soluzione alternativa a questo problema, è possibile connettersi all'istanza di SQL Server Integration Service tramite la versione di [SSMS allineata con l'istanza di SSIS.](../ssms/previous-sql-server-management-studio-releases.md) 
  
4. **SSMS non salva i piani di manutenzione per SQL Server 2008 R2 e le versione precedenti di SQL Server.**  
    Si tratta di un limite noto che si prevede di risolvere in futuro. Nel frattempo, è possibile usare la [versione di SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) per salvare i piani di manutenzione.  
    
5. **Le installazioni di SSMS non in lingua inglese potrebbero richiedere l'installazione di un pacchetto di protezione aggiuntivo.**  
Le versioni di SSMS non localizzate in lingua inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) .
  
6. **Gestione configurazione SQL Server non si avvia se nessuna versione di SQL Server è installata nel computer client**  
    Se si avvia Gestione configurazione SQL Server senza aver installato una versione di SQL Server nel computer client, si riceverà l'errore seguente:   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Se sono state aggiunte istanze di SQL Server all'elenco 'Server registrati' in SSMS:  
        1. Passare alla vista Server registrati' in SSMS.  
        2. Fare clic con il pulsante destro del mouse sull'istanza di SQL Server che si vuole configurare.  
        3. Selezionare Gestione configurazione SQL Server... dal menu di scelta rapida.    
          
      * Se non sono state aggiunte istanze di SQL Server all'elenco 'Server registrati' in SSMS:  
        1. Aprire un prompt dei comandi come amministratore.  
        2. Eseguire lo strumento Mofcomp usando il comando seguente:  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Dopo aver eseguito lo strumento Mofcomp, eseguire i comandi seguenti per riavviare il servizio WMI e rendere effettive le modifiche:  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  

## <a name="feedback"></a>Commenti e suggerimenti  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum (Forum sugli strumenti client di SQL)](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Segnalare un problema o inserire un suggerimento in Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Vedere anche  
[Esercitazione su SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Scaricare SQL Server Management Studio &amp;#40;SSMS&amp;#41;](../ssms/download-sql-server-management-studio-ssms.md)  
[Versioni precedenti di SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  

  

