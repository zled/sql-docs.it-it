---
title: Impostazioni (migrazione) (MySQLToSQL) del progetto | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9
caps.latest.revision: 14
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4ab9b6365d527d2cbd804ab0095021c2f2d9dc2b
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-migration-mysqltosql"></a>Impostazioni del progetto (migrazione) (MySQLToSQL)
La pagina di migrazione del **impostazioni progetto** la finestra di dialogo contiene le impostazioni che consentono di personalizzare la modalità SSMA viene eseguita la migrazione dei dati da MySQL a SQL Server.  
  
Il riquadro di migrazione è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Per specificare le impostazioni per tutti i progetti SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto in **versione di destinazione della migrazione** elenco a discesa di cui si desidera accedere alle impostazioni, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **migrazione**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro e quindi fare clic su **migrazione**.  
  
## <a name="options"></a>Opzioni  
  
### <a name="bulk-copy"></a>Copia bulk  
  
|Nome|Definizione|  
|--------|--------------|  
|**Dimensioni batch**|Specifica il batch di dimensioni utilizzate durante la migrazione dei dati.<br /><br />**Modalità predefinita**: 1000<br /><br />**Modalità ottimistica**: 1000<br /><br />**Modalità**: 1000|  
|**Vincoli CHECK**|Specifica se SSMA deve verificare i vincoli durante l'inserimento di dati in tabelle di SQL Server.<br /><br />**Modalità predefinita**: False<br /><br />**Modalità ottimistica**: False<br /><br />**Modalità**: False|  
|**Attive trigger**|Specifica se SSMA deve attivare i trigger di inserimento durante l'aggiunta di dati in tabelle SQL Server.<br /><br />**Modalità predefinita**: False<br /><br />**Modalità ottimistica**: False<br /><br />**Modalità**: False|  
|**Mantieni valori Identity**|Specifica se SSMA consente di mantenere i valori identity MySQL durante l'aggiunta di dati a SQL Server. Un valore False fa sì che i valori identity per poter essere assegnati dalla destinazione.<br /><br />**Modalità predefinita**: True<br /><br />**Modalità ottimistica**: True<br /><br />**Modalità**: True|  
|**Mantieni valori Null**|Specifica se SSMA consente di mantenere i valori null nei dati di origine durante l'aggiunta di dati a SQL Server, indipendentemente dai valori predefiniti specificati in SQL Server.<br /><br />**Modalità predefinita**: True<br /><br />**Modalità ottimistica**: True<br /><br />**Modalità**: True|  
|**Blocco a livello di tabella**|Specifica se SSMA consente di bloccare le tabelle durante l'aggiunta di dati alle tabelle durante la migrazione dei dati. Ottiene un blocco di aggiornamento bulk per tutta la durata dell'operazione di copia bulk. Se il valore è False, viene impostato un blocco a livello di riga.<br /><br />**Modalità predefinita**: False<br /><br />**Modalità ottimistica**: False<br /><br />**Modalità**: False|  
  
### <a name="data-modification"></a>Modifica dei dati  
  
|Nome|Definizione|  
|--------|--------------|  
|**Migrazione di date non valide**|Specifica come eseguire la migrazione di date non valide con come ' 2007-04-23' o ' 2000-06-31 10:00:00 ' in formati di data e DATETIME.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**Modalità ottimistica**: impostare NULL<br /><br />**Modalità**: impostare NULL|  
|**Valori di tempo negativi migrazione**|Specifica come eseguire la migrazione a valori negativi come '-30:11:00' nelle colonne tempo.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**Modalità ottimistica**: impostare NULL<br /><br />**Modalità**: impostare NULL|  
|**Valori di ora più di 24 ore migrazione**|Specifica come eseguire la migrazione di più di ' 23 i valori di ora: 59:59' nelle colonne tempo.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**Modalità ottimistica**: impostare NULL<br /><br />**Modalità**: impostare NULL|  
|**Troncare i valori binari per rientrare nella colonna**|In caso affermativo, SSMA tronca i valori binari da MySQL che non rientrano nelle colonne della tabella SQL e genera il messaggio di errore appropriato. Se No, la riga provoca un errore<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: No|  
|**Troncare i valori di carattere per rientrare nella colonna**|SSMA tronca i valori di carattere da MySQL che non rientrano nelle colonne della tabella SQL e genera il messaggio di errore appropriato.<br /><br />**Modalità predefinita**: No<br /><br />**Modalità ottimistica**: No<br /><br />**Modalità**: No|  
|**Migrazione zero date**|Specifica come eseguire la migrazione zero date come ' 0000-00-00' o ' 0000-00-00-00:00:00 ' nelle colonne DATE e DATETIME.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**Modalità ottimistica**: impostare NULL<br /><br />**Modalità**: impostare NULL|  
|**Zero nella migrazione di date**|Specifica come eseguire la migrazione di date con zero parti come ' 2009-01-00' o ' 2000-00-00-11:00:00 ' nelle colonne DATE e DATETIME.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**Modalità ottimistica**: impostare NULL<br /><br />**Modalità**: impostare NULL|  
  
### <a name="migration-engine"></a>Modulo di migrazione  
  
|Nome|Definizione|  
|--------|--------------|  
|**Modulo di migrazione**|Specifica il motore di database utilizzato durante la migrazione dei dati. Migrazione dei dati sul lato client fa riferimento al client SSMA recupero dei dati dall'origine e in blocco inserimento di dati in SQL Server. Migrazione dei dati lato server fa riferimento al modulo di migrazione di dati SSMA (programma di copia bulk) in esecuzione nella finestra di SQL Server come un processo SQL Agent, il recupero dei dati dall'origine e inserimento direttamente in SQL Server, evitando in tal modo un ulteriore client-hop (prestazioni).<br /><br />**Modalità predefinita**: modulo di migrazione dei dati sul lato Client<br /><br />**Modalità ottimistica**: modulo di migrazione dei dati sul lato Client<br /><br />**Modalità**: modulo di migrazione dei dati sul lato Client|  
  
> [!IMPORTANT]  
> Quando il **modulo di migrazione** opzione è impostata su **modulo di migrazione dei dati lato Server**, un nuovo progetto opzione **modulo di migrazione dei dati lato Server utilizzare 32 Bit** viene visualizzato. Specifica se l'utilità di programma di copia Bulk (BCP) a 32 bit o a 64 bit viene utilizzato per la migrazione dei dati.  
  
### <a name="misc"></a>Varie  
  
|Nome|Definizione|  
|--------|--------------|  
|**Opzioni di migrazione di dati estesi**|Mostra opzioni di migrazione di dati aggiuntivi per ogni tabella nella scheda Dettagli separato.<br /><br />**Modalità predefinita**: nascondere<br /><br />**Modalità ottimistica**: nascondere<br /><br />**Modalità**: nascondere|  
|**In caso di errore**|Arresta la migrazione dei dati quando si verifica un errore. Sono disponibili tre opzioni:<br /><br />**Interrompere la migrazione:** interrompe l'operazione di migrazione di dati<br /><br />**Passare alla tabella riportata di seguito:** interrompe la migrazione dei dati alla tabella corrente e continua a quella successiva<br /><br />**Procedere al batch successivo:** interrompe la migrazione dei dati per il batch corrente e continua a quella successiva<br /><br />**Modalità predefinita**: procedere con il batch successivo<br /><br />**Modalità ottimistica**: procedere con il batch successivo<br /><br />**Modalità**: procedere con il batch successivo|  
  
### <a name="parallel-data-migration"></a>Migrazione dei dati paralleli  
  
|Nome|Definizione|  
|--------|--------------|  
|**Modalità di migrazione di dati paralleli**|Specifica la modalità utilizzata per il thread di divisione per abilitare la migrazione di dati paralleli. In modalità Auto, SSMA sceglie il numero di thread (10 per impostazione predefinita) duplicato per la migrazione dei dati. In modalità personalizzata, utente può specificare il numero di thread duplicata per la migrazione dei dati (valore minimo è 1 e valore massimo è 100). Modulo di migrazione client solo dati sul lato attualmente supporta la migrazione dei dati paralleli.<br /><br />**Modalità predefinita**: Auto<br /><br />**Modalità ottimistica**: Auto<br /><br />**Modalità**: Auto|  
  
> [!IMPORTANT]  
> Quando il **modalità di migrazione di dati parallelo** opzione è impostata su **personalizzato**, un nuovo progetto, l'impostazione di opzione **conteggio Thread** viene visualizzato. Specifica il numero di thread utilizzati per la migrazione dei dati.  
  
### <a name="spatial-data"></a>Dati spaziali  
  
|Nome|Definizione|  
|--------|--------------|  
|**Gestione degli errori**|Specifica come gestire gli errori nella migrazione di valori di tipi di dati spaziali. Se viene specificati 'Replace con NULL', tutti i valori spaziali causano errori verranno sostituiti con il valore NULL. La sostituzione non viene eseguita in caso contrario.<br /><br />**Modalità predefinita**: genera un errore<br /><br />**Modalità ottimistica**: genera un errore<br /><br />**Modalità**: genera un errore|  
|**Convalida del valore**|Specifica come gestire valori spaziali non validi. Se viene specificato 'Provare a rendere valido', è viene effettuato un tentativo di modificare i valori non validi in modo da renderli validi.<br /><br />**Modalità predefinita**: rendere valida<br /><br />**Modalità ottimistica**: non modificare<br /><br />**Modalità**: rendere valida|  
  

