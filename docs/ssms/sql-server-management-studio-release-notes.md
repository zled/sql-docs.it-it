---
title: SQL Server Management Studio - Note sulla versione | Microsoft Docs
ms.custom: 
ms.date: 06/22/2017
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
ms.translationtype: HT
ms.sourcegitcommit: 223d43974e6b63f7375a3d3e000492612fb6856e
ms.openlocfilehash: 7fb0aa5f5d8b78a4783efdbb4e1f064eb025538a
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="sql-server-management-studio----release-notes"></a>Note sulla versione di SQL Server Management Studio
Questo articolo illustra la versione disponibile di SQL Server Management Studio.  Questa versione di SQL Server Management Studio (SSMS) è un'installazione autonoma non compresa nel rilascio di SQL Server. L'obiettivo di Microsoft è aggiornarla di frequente con nuove funzionalità, correzioni e supporto alle nuove funzionalità di SQL Server e Database SQL di Azure.  
  
Per installare la versione più recente di SQL Server Management Studio, vedere [Scaricare SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
  
Di seguito è possibile trovare un elenco di problemi e limitazioni relativi a questa versione di SQL Server Management Studio:  

1. **La procedura guidata Ripristina database genera un modello di percorso errato per il percorso di file di database di destinazione** Si tratta di un problema noto quando SQL Server Management Studio viene connesso a un server Linux. Anche se il percorso sembra errato o strano, viene gestito correttamente sul lato server, ovvero non vi è alcun problema funzionale.

2. **Problemi del visualizzatore di file**
    - Quando si usa un'istanza basata su Windows di SQL Server 2017 CTP 2.0, l'apertura dell'interfaccia utente del visualizzatore di file in SQL Server Management Studio potrebbe non riuscire se nel server sono installati un'unità disco floppy vuota oppure un disco fisso protetto da Bitlocker. 
    - L'interfaccia utente del visualizzatore di file non supporta più versioni di SQL Server 2017 precedenti a CTP 2.0.
    


3. **Per un'istanza SSMS è possibile accedere a un solo account di Azure Active Directory con l'Autenticazione universale di Active Directory.**  
    Questa restrizione è limitata all'Autenticazione universale di Active Directory. È invece possibile accedere a server diversi usando l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.
    
    In alternativa, è possibile usare un'altra istanza di SSMS per accedere come un altro dell'account di Azure Active Directory. 
    
4. **I comandi Data-Tier Application Framework (DacFx) e Progettazione schema in SSM non supportano l'Autenticazione universale di Active Directory.**  
    I comandi che usano DacFx, ad esempio importazione ed esportazione, e Progettazione schema in SSMS non supportano attualmente l'Autenticazione universale di Active Directory.
    
    In alternativa, è possibile usare altre forme di autenticazione disponibili in SSMS, come l'Autenticazione della password di Active Directory, l'Autenticazione integrata di Active Directory o l'Autenticazione di SQL Server.

5. **SSMS 17.x può connettersi solo a istanze di SQL Server 2017 Integrated Services (SSIS 2017).**  
    Esiste un limite noto di compatibilità con SQL Server Integration Services che impedisce la connessione a versioni precedenti.
    
    Come soluzione alternativa a questo problema, è possibile connettersi all'istanza di SQL Server Integration Service tramite la versione di [SSMS allineata con l'istanza di SSIS.](../ssms/previous-sql-server-management-studio-releases.md) 
  
5. **SSMS non salva i piani di manutenzione per SQL Server 2008 R2 e le versione precedenti di SQL Server.**  
    Si tratta di un limite noto che si prevede di risolvere in futuro. Nel frattempo, è possibile usare la [versione di SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) per salvare i piani di manutenzione.  
    
5. **Le installazioni di SSMS non in lingua inglese potrebbero richiedere l'installazione di un pacchetto di protezione aggiuntivo.**  
Le versioni di SSMS non localizzate in lingua inglese e installate in Windows 8, Windows 7, Windows Server 2012 e Windows Server 2008 R2 richiedono il [pacchetto di aggiornamento della sicurezza KB 2862966](https://support.microsoft.com/en-us/kb/2862966) .

5. **Facendo clic su ? o premendo F1 la Guida non viene aperta**  
In alcuni ambienti quando si fa clic su ? o si preme F1 un messaggio indica che **è necessaria una nuova app per aprire ms-xhelp**. Questo errore è un problema noto e verrà risolto in una versione futura.
  
## <a name="feedback"></a>Commenti e suggerimenti  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [SQL Client Tools Forum (Forum sugli strumenti client di SQL)](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Segnalare un problema o inserire un suggerimento in Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Vedere anche  
[Esercitazione su SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Scaricare SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md)  
[Versioni precedenti di SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  

  

