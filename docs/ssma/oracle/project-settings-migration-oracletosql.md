---
title: Impostazioni (migrazione) (OracleToSQL) del progetto | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcd6b988-633b-4b2b-9f36-6368b5e86b60
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 42d83671531f703e1d604dce5cb4e247767dae83
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-migration-oracletosql"></a>Impostazioni del progetto (migrazione) (OracleToSQL)
La pagina di migrazione del **impostazioni progetto** la finestra di dialogo contiene le impostazioni che consentono di personalizzare la modalità SSMA viene eseguita la migrazione dei dati da Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Il riquadro di migrazione è disponibile in entrambi i **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Per specificare le impostazioni per tutti i progetti SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **migrazione**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **migrazione**.  
  
## <a name="migration-engine"></a>Modulo di migrazione  
  
|Nome|Definizione|  
|--------|--------------|  
|**Modulo di migrazione**|Specifica il motore di database utilizzato durante la migrazione dei dati. Migrazione dei dati sul lato client fa riferimento al client SSMA recupero dei dati dall'origine e in blocco inserimento di dati in SQL Server. Migrazione dei dati lato server fa riferimento al modulo di migrazione di dati SSMA (programma di copia bulk) in esecuzione nella finestra di SQL Server come un processo SQL Agent, il recupero dei dati dall'origine e inserimento direttamente in SQL Server, evitando in tal modo un ulteriore client-hop (prestazioni).<br /><br />**Modalità predefinita**: modulo di migrazione dei dati sul lato Client<br /><br />**Modalità ottimistica**: modulo di migrazione dei dati sul lato Client<br /><br />**Modalità**: modulo di migrazione dei dati sul lato Client|  
  
> [!IMPORTANT]  
> Quando il **modulo di migrazione** opzione è impostata su **modulo di migrazione dei dati lato Server**, un nuovo progetto opzione **modulo di migrazione dei dati lato Server utilizzare 32 Bit** viene visualizzato. Specifica se l'utilità di programma di copia Bulk (BCP) a 32 bit o a 64 bit viene utilizzato per la migrazione dei dati.  
  
## <a name="miscellaneous-options"></a>Opzioni varie  
  
|Nome|Definizione|  
|--------|--------------|  
|**Dimensioni batch**|Specifica il batch di dimensioni utilizzate durante la migrazione dei dati.<br /><br />**Modalità predefinita**: 10000<br /><br />**Modalità ottimistica**: 10000<br /><br />**Modalità**: 10000|  
|**Vincoli CHECK**|Specifica se SSMA deve verificare i vincoli durante l'inserimento di dati in tabelle di SQL Server.<br /><br />**Modalità predefinita**: False<br /><br />**Modalità ottimistica**: False<br /><br />**Modalità**: False|  
|**Timeout della migrazione dei dati**|Specifica il timeout utilizzato durante la migrazione dei dati<br /><br />**Modalità predefinita**: 15<br /><br />**Modalità ottimistica**: 15<br /><br />**Modalità**: 15|  
|**Opzioni di migrazione di dati estesi**|Mostra opzioni di migrazione di dati aggiuntivi per ogni tabella nella scheda Dettagli separato.<br /><br />**Modalità predefinita**: nascondere<br /><br />**Modalità ottimistica**: nascondere<br /><br />**Modalità**: nascondere|  
|**Attive trigger**|Specifica se SSMA deve attivare i trigger di inserimento durante l'aggiunta di dati in tabelle SQL Server.<br /><br />**Modalità predefinita**: False<br /><br />**Modalità ottimistica**: False<br /><br />**Modalità**: False|  
|**Mantieni valori Identity**|Specifica se SSMA consente di mantenere i valori null nei dati di origine durante l'aggiunta di dati a SQL Server, indipendentemente dai valori predefiniti specificati in SQL Server.<br /><br />**Modalità predefinita**: True<br /><br />**Modalità ottimistica**: True<br /><br />**Modalità**: False|  
|**Mantieni valori Null**|Specifica se SSMA consente di mantenere i valori null nei dati di origine durante l'aggiunta di dati a SQL Server, indipendentemente dai valori predefiniti specificati in SQL Server.<br /><br />**Modalità predefinita**: True<br /><br />**Modalità ottimistica**: True<br /><br />**Modalità**: True|  
|**Contrassegnare l'operazione di taglio di stringa con errore**|Se le dimensioni di colonna di destinazione sono minore della lunghezza di stringa di origine, il valore verrà tagliato e contrassegnato come errore.<br /><br />**Modalità predefinita**: Sì<br /><br />**Modalità ottimistica**: Sì<br /><br />**Modalità**: Sì|  
|**In caso di errore**|Arresta la migrazione dei dati quando si verifica un errore. Sono disponibili tre opzioni:<br /><br />**Interrompere la migrazione:** interrompe l'operazione di migrazione di dati<br /><br />**Passare alla tabella riportata di seguito:** interrompe la migrazione dei dati alla tabella corrente e continua a quella successiva<br /><br />**Procedere al batch successivo:** interrompe la migrazione dei dati per il batch corrente e continua a quella successiva<br /><br />**Modalità predefinita**: procedere con il batch successivo<br /><br />**Modalità ottimistica**: procedere con il batch successivo<br /><br />**Modalità**: procedere con il batch successivo|  
|**Sostituire le date non supportate**|Specifica se SSMA deve correggere date precedenti rispetto a quello meno recente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **datetime** data (01 gennaio 1753).<br /><br />Per mantenere i valori di data corrente, selezionare **non eseguire alcuna operazione**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]in una colonna datetime non accetta le date precedenti 01 gennaio 1753. Se si utilizzano le date precedenti, è necessario convertire i valori datetime ai valori di carattere.<br /><br />Per convertire le date precedenti 01 gennaio 1753 su NULL, selezionare **sostituire con il valore NULL**.<br /><br />Per sostituire le date precedenti 01 gennaio 1753 con una data, selezionare **sostituire con più vicino di date supportato**.<br /><br />**Modalità predefinita**: non eseguire alcuna operazione<br /><br />**Modalità ottimistica**: non eseguire alcuna operazione<br /><br />**Modalità**: sostituire con più vicino di data supportati|  
|**Blocco a livello di tabella**|Specifica se SSMA consente di bloccare le tabelle durante l'aggiunta di dati alle tabelle durante la migrazione dei dati. Ottiene un blocco di aggiornamento bulk per tutta la durata dell'operazione di copia bulk. Se il valore è False, viene impostato un blocco a livello di riga.<br /><br />**Modalità predefinita**: True<br /><br />**Modalità ottimistica**: True<br /><br />**Modalità**: True|  
  
## <a name="parallel-data-migration"></a>Migrazione dei dati paralleli  
  
|Nome|Definizione|  
|--------|--------------|  
|**Modalità di migrazione di dati paralleli**|Specifica la modalità utilizzata per il thread di divisione per abilitare la migrazione di dati paralleli. In modalità Auto, SSMA sceglie il numero di thread (10 per impostazione predefinita) duplicato per la migrazione dei dati. In modalità personalizzata, utente può specificare il numero di thread duplicata per la migrazione dei dati (valore minimo è 1 e valore massimo è 100). Modulo di migrazione client solo dati sul lato attualmente supporta la migrazione dei dati paralleli.<br /><br />**Modalità predefinita**: Auto<br /><br />**Modalità ottimistica**: Auto<br /><br />**Modalità**: Auto|  
  
> [!IMPORTANT]  
> Quando il **modalità di migrazione di dati parallelo** opzione è impostata su **personalizzato**, un nuovo progetto, l'impostazione di opzione **conteggio Thread** viene visualizzato. Specifica il numero di thread utilizzati per la migrazione dei dati.  
  

