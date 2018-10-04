---
title: Impostazioni (migrazione) (MySQLToSQL) del progetto | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b3ed99d33147d055328f133702923687e0803c0a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750859"
---
# <a name="project-settings-migration-mysqltosql"></a>Impostazioni del progetto (migrazione) (MySQLToSQL)
La pagina di migrazione del **impostazioni del progetto** nella finestra di dialogo contiene impostazioni che consentono di personalizzare la modalità SSMA viene eseguita la migrazione dei dati da MySQL a SQL Server.  
  
Nel riquadro di migrazione è disponibile nel **impostazioni del progetto** e **impostazioni di progetto predefinite** finestre di dialogo.  
  
-   Per specificare le impostazioni per tutti i progetti SSMA, il **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto in **versione di destinazione della migrazione** elenco a discesa di che si desidera accedere alle impostazioni, fare clic su **generali** nella parte inferiore del riquadro a sinistra e quindi fare clic su **migrazione**.  
  
-   Per specificare le impostazioni per il progetto corrente, il **strumenti** dal menu **le impostazioni del progetto**, fare clic su **generale** nella parte inferiore del riquadro di sinistra e quindi fare clic su **Migrazione**.  
  
## <a name="options"></a>Opzioni  
  
### <a name="bulk-copy"></a>Copia bulk  
  
|Nome|Definizione|  
|--------|--------------|  
|**Dimensioni del batch**|Specifica il batch di dimensioni usate durante la migrazione dei dati.<br /><br />**Modalità predefinita**: 1000<br /><br />**La modalità ottimistico**: 1000<br /><br />**Modalità intero**: 1000|  
|**Vincoli CHECK**|Specifica se SSMA deve verificare i vincoli durante l'inserimento dei dati in tabelle SQL Server.<br /><br />**Modalità predefinita**: False<br /><br />**La modalità ottimistico**: False<br /><br />**Modalità intero**: False|  
|**Attive trigger**|Specifica se SSMA deve attivare i trigger di inserimento quando aggiunge dati alle tabelle di SQL Server.<br /><br />**Modalità predefinita**: False<br /><br />**La modalità ottimistico**: False<br /><br />**Modalità intero**: False|  
|**Mantieni valori Identity**|Specifica se SSMA consente di mantenere i valori identity MySQL durante l'aggiunta di dati a SQL Server. Il valore False fa sì che i valori identity da assegnare alla destinazione.<br /><br />**Modalità predefinita**: True<br /><br />**La modalità ottimistico**: True<br /><br />**Modalità intero**: True|  
|**Mantieni valori Null**|Specifica se SSMA consente di mantenere i valori null nei dati di origine durante l'aggiunta di dati in SQL Server, indipendentemente dai valori predefiniti che vengono specificati in SQL Server.<br /><br />**Modalità predefinita**: True<br /><br />**La modalità ottimistico**: True<br /><br />**Modalità intero**: True|  
|**Blocco a livello di tabella**|Specifica se SSMA consente di bloccare le tabelle durante l'aggiunta di dati alle tabelle durante la migrazione dei dati. Ottiene un blocco di aggiornamento bulk per la durata dell'operazione di copia bulk. Se il valore è False, viene impostato un blocco a livello di riga.<br /><br />**Modalità predefinita**: False<br /><br />**La modalità ottimistico**: False<br /><br />**Modalità intero**: False|  
  
### <a name="data-modification"></a>Modifica dei dati  
  
|Nome|Definizione|  
|--------|--------------|  
|**Migrazione di date non valide**|Specifica come eseguire la migrazione di date non valide con, ad esempio ' 2007-04-23' o ' 2000-06-31 10:00:00 "in formati di data e data/ora.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**La modalità ottimistico**: impostare NULL<br /><br />**Modalità intero**: impostare NULL|  
|**Valori di tempo negativi migrazione**|Specifica come eseguire la migrazione di valori negativi, ad esempio '-30:11:00' nelle colonne dell'ora.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**La modalità ottimistico**: impostare NULL<br /><br />**Modalità intero**: impostare NULL|  
|**Valori di ora più di 24 ore la migrazione**|Specifica come eseguire la migrazione di valori di ora di più di ' 23: 59:59' nelle colonne dell'ora.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**La modalità ottimistico**: impostare NULL<br /><br />**Modalità intero**: impostare NULL|  
|**Troncare i valori binari per rientrare nella colonna**|In caso affermativo, SSMA tronca i valori binari da MySQL che non rientrano nelle colonne della tabella SQL e genera il messaggio di errore appropriato. Se No, la riga causa un errore<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: No|  
|**Troncare i valori di carattere per rientrare nella colonna**|SSMA tronca i valori dei caratteri MySQL che non rientrano nelle colonne della tabella SQL e genera il messaggio di errore appropriato.<br /><br />**Modalità predefinita**: No<br /><br />**La modalità ottimistico**: No<br /><br />**Modalità intero**: No|  
|**Migrazione zero date**|Specifica come eseguire la migrazione zero date, ad esempio ' 0000-00: 00' o ' 0000-00: 00 00:00:00 "nelle colonne DATE e DATETIME.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**La modalità ottimistico**: impostare NULL<br /><br />**Modalità intero**: impostare NULL|  
|**Zero nella migrazione di date**|Specifica come eseguire la migrazione di date con zero parti, ad esempio "2009-01-00' o ' 2000-00: 00 11:00:00 ' nelle colonne DATE e DATETIME.<br /><br />**Modalità predefinita**: impostare NULL<br /><br />**La modalità ottimistico**: impostare NULL<br /><br />**Modalità intero**: impostare NULL|  
  
### <a name="migration-engine"></a>Modulo di migrazione  
  
|Nome|Definizione|  
|--------|--------------|  
|**Modulo di migrazione**|Specifica il motore di database utilizzato durante la migrazione dei dati. Migrazione dei dati lato client fa riferimento al client SSMA recupero dei dati dall'origine e inserimento bulk che i dati in SQL Server. Migrazione dei dati lato server fa riferimento al motore di migrazione di dati SSMA (programma di copia bulk) in esecuzione nella finestra di SQL Server come un processo SQL Agent, il recupero dei dati dall'origine e inserimento direttamente in SQL Server, evitando in tal modo un ulteriore client-hop (prestazioni).<br /><br />**Modalità predefinita**: motore di migrazione dei dati lato Client<br /><br />**La modalità ottimistico**: motore di migrazione dei dati lato Client<br /><br />**Modalità intero**: motore di migrazione dei dati lato Client|  
  
> [!IMPORTANT]  
> Quando la **modulo di migrazione** opzione è impostata su **modulo di migrazione dei dati lato Server**, un nuovo progetto, impostare l'opzione **modulo di migrazione dei dati lato Server utilizzare 32 Bit** viene visualizzato . Specifica se l'utilità di Strumentazione gestione Windows (BCP, Bulk Copy Program) a 32 bit o a 64 bit viene utilizzato per la migrazione dei dati.  
  
### <a name="misc"></a>Varie  
  
|Nome|Definizione|  
|--------|--------------|  
|**Opzioni di migrazione dati estesi**|Mostra le opzioni di migrazione dati aggiuntivi per ogni tabella nella scheda Dettagli separato.<br /><br />**Modalità predefinita**: nascondere<br /><br />**La modalità ottimistico**: nascondere<br /><br />**Modalità intero**: nascondere|  
|**In caso di errore**|Interrompe la migrazione dei dati quando si verifica un errore. Sono disponibili tre opzioni:<br /><br />**Interrompere la migrazione:** interrompe l'operazione di migrazione dati<br /><br />**Passare alla tabella riportata di seguito:** interrompe la migrazione dei dati alla tabella corrente e procede a quella successiva<br /><br />**Passare al batch successivo:** interrompe la migrazione dei dati per il batch corrente e procede a quella successiva<br /><br />**Modalità predefinita**: procedere al batch successivo<br /><br />**La modalità ottimistico**: procedere al batch successivo<br /><br />**Modalità intero**: procedere al batch successivo|  
  
### <a name="parallel-data-migration"></a>Migrazione parallela dei dati  
  
|Nome|Definizione|  
|--------|--------------|  
|**Modalità di migrazione dati paralleli**|Specifica la modalità usata per i thread fork per abilitare la migrazione di dati paralleli. In modalità Auto, SSMA sceglie il numero di thread (10 per impostazione predefinita) duplicato per la migrazione dei dati. Nella modalità personalizzata, utente può specificare il numero di thread forked per eseguire la migrazione dei dati (valore minimo è 1 e valore massimo è 100). Modulo di migrazione client solo i dati sul lato supporta attualmente la migrazione dei dati parallelo.<br /><br />**Modalità predefinita**: automatica<br /><br />**La modalità ottimistico**: automatica<br /><br />**Modalità intero**: automatica|  
  
> [!IMPORTANT]  
> Quando il **paralleli in modalità di migrazione dati** opzione è impostata su **Custom**, un nuovo progetto, impostare l'opzione **conteggio dei Thread** viene visualizzato. Numero di thread usati per la migrazione dei dati specifica.  
  
### <a name="spatial-data"></a>Dati spaziali  
  
|Nome|Definizione|  
|--------|--------------|  
|**Gestione degli errori**|Specifica come gestire gli errori nella migrazione di valori di tipi di dati spaziali. Se viene specificati 'Sostituire con un valore NULL', tutti valori spaziali causando errori verranno sostituiti con un valore NULL. In caso contrario, non viene eseguita alcuna sostituzione.<br /><br />**Modalità predefinita**: generare un errore<br /><br />**La modalità ottimistico**: generare un errore<br /><br />**Modalità intero**: generare un errore|  
|**Convalida del valore**|Specifica come gestire valori spaziali non validi. Se 'Provare a rendere validi' è specificato, è in corso effettuato un tentativo di modificare i valori non validi in modo da renderli validi.<br /><br />**Modalità predefinita**: rendere valida<br /><br />**La modalità ottimistico**: non modificare<br /><br />**Modalità intero**: rendere valida|  
  
