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
ms.translationtype: Human Translation
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: 1733a789fb2dc17eea82ab22d4a50614d1fffc3b
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-management-studio----release-notes"></a>Note sulla versione di SQL Server Management Studio
Questo articolo illustra la versione disponibile di SQL Server Management Studio.  Questa versione di SQL Server Management Studio (SSMS) è un'installazione autonoma non compresa nel rilascio di SQL Server. L'obiettivo di Microsoft è aggiornarla di frequente con nuove funzionalità, correzioni e supporto alle nuove funzionalità di SQL Server e Database SQL di Azure.  
  
Per installare la versione più recente di SQL Server Management Studio, vedere [Download SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
  
Di seguito è possibile trovare un elenco di problemi e limitazioni relativi a questa versione di SQL Server Management Studio:  

1. **Ripristino guidato Database genera un modello di percorso errato per percorso di file di database di destinazione** 
    si tratta di un problema noto quando SSMS viene connesso a un server Linux. Anche se il percorso è errato o dispari, viene gestita correttamente sul lato server, ad esempio non vi è alcun problema funzionale.

2. **Problemi di file del Browser**
    - Quando si utilizza un'istanza basati su Windows di SQL Server 2017 CTP 2.0, il browser di file dell'interfaccia utente in SQL Server Management Studio potrebbe non riuscire aprire, se il server ha un'unità floppy vuota o un disco fisso protette da Bitlocker installato. 
    - Interfaccia utente del browser di file non supporta più versioni di SQL Server 2017 prima della versione CTP 2.0.
    


3. **Per un'istanza SSMS è possibile accedere a un solo account di Azure Active Directory con l'Autenticazione universale di Active Directory.**  
    Questa restrizione è limitata all'Autenticazione universale di Active Directory. È invece possibile accedere a server diversi usando l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.
    
    In alternativa, è possibile usare un'altra istanza di SSMS per accedere come un altro dell'account di Azure Active Directory. 
    
4. **I comandi Data-Tier Application Framework (DacFx) e Progettazione schema in SSM non supportano l'Autenticazione universale di Active Directory.**  
    I comandi che usano DacFx, ad esempio importazione ed esportazione, e Progettazione schema in SSMS non supportano attualmente l'Autenticazione universale di Active Directory.
    
    In alternativa, è possibile usare altre forme di autenticazione disponibili in SSMS, come l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.

5. **SSMS può connettersi solo a istanze di SQL Server 2016 Integrated Services (SSIS 2016).**  
    Esiste un limite noto di compatibilità con SQL Server Integration Services che impedisce la connessione a versioni precedenti.
    
    Come soluzione alternativa a questo problema, è possibile connettersi all'istanza di SQL Server Integration Service tramite la versione di [SSMS allineata con l'istanza di SSIS.](../ssms/previous-sql-server-management-studio-releases.md) 
  
5. **SSMS non salva i piani di manutenzione per SQL Server 2008 R2 e le versione precedenti di SQL Server.**  
    Si tratta di un limite noto che si prevede di risolvere in futuro. Nel frattempo, è possibile usare la [versione di SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) per salvare i piani di manutenzione.  
    
5. **Le installazioni di SSMS non in lingua inglese potrebbero richiedere l'installazione di un pacchetto di protezione aggiuntivo.**  
Le versioni di SSMS non localizzate in lingua inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) .
  
## <a name="feedback"></a>Commenti e suggerimenti  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum (Forum sugli strumenti client di SQL)](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Segnalare un problema o inserire un suggerimento in Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Vedere anche  
[Esercitazione su SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Scaricare SQL Server Management Studio &amp;#40;SSMS&amp;#41;](../ssms/download-sql-server-management-studio-ssms.md)  
[Versioni precedenti di SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  

  

