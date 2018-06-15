---
title: Schermata della procedura guidata 4, il Driver ODBC per SQL Server, dell'origine dati | Documenti Microsoft
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f53180976b3a4778f687ef8a83d9438ea858c05
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32855892"
---
# <a name="data-source-wizard-screen-4"></a>Schermata di creazione guidata origine dati 4

Specificare la lingua da utilizzare per i messaggi di SQL Server, il set di caratteri, conversione e se il driver ODBC per SQL Server deve utilizzare impostazioni internazionali. È inoltre possibile controllare la registrazione di query con esecuzione prolungata e le impostazioni delle statistiche del driver.

## <a name="options"></a>Opzioni

### <a name="change-the-language-of-sql-server-system-messages-to"></a>Visualizza i messaggi di sistema di SQL Server in

Ogni istanza di SQL Server può avere più set di messaggi di sistema, con ogni set in una lingua diversa (ad esempio, inglese, spagnolo, francese e così via). Se un'origine dati è definita rispetto a un server che dispone di più set di messaggi di sistema, è possibile specificare quale lingua si desidera utilizzare per i messaggi di sistema. Selezionare la lingua desiderata nell'elenco. Questa opzione è disponibile se solo una lingua è installata in SQL Server.

### <a name="use-strong-encryption-for-data"></a>Usa crittografia avanzata per i dati

Se questa opzione è selezionata, i dati passati tramite connessioni stabilite utilizzando il DSN corrente saranno crittografati. Gli account di accesso sono crittografati per impostazione predefinita, anche se questa casella di controllo è deselezionata.

### <a name="trust-server-certificate"></a>Certificato server attendibile

Questa opzione è applicabile solo quando **Usa crittografia avanzata per i dati** è abilitata. Se selezionata, il certificato del server non verrà convalidato con il nome host corretto del server, essere emesso da un'autorità di certificazione. 

### <a name="perform-translation-for-character-data"></a>Converti dati caratteri

Quando questa casella di controllo è selezionata, il driver ODBC per SQL Server converte le stringhe ANSI inviate tra il computer client e SQL Server utilizzando Unicode. Il driver ODBC in alcuni casi esegue la conversione tra la tabella codici del Server SQL e Unicode nel computer client. Ciò richiede che la tabella codici utilizzata da SQL Server sia una delle tabelle codici disponibili nel computer client.

Se questa casella di controllo è deselezionata, la conversione dei caratteri estesi in stringhe di caratteri ANSI non viene eseguita quando tali caratteri vengono inviati tra l'applicazione client e il server. Se il client utilizza una tabella codici ANSI (ACP) diversa dalla tabella codici SQL Server, i caratteri estesi nelle stringhe di caratteri ANSI potrebbero essere interpretata erroneamente. Se il client utilizza la stessa tabella codici per la tabella codici ANSI che utilizza SQL Server, i caratteri estesi vengono interpretati correttamente.

### <a name="use-regional-settings-when-outputting-currency-numbers-dates-and-times"></a>Usa le impostazioni internazionali del sistema per visualizzare simboli di valuta, numeri, data e ora

Indica che il driver utilizza le impostazioni internazionali del computer client per la formattazione di valuta, numeri, date e ore nelle stringhe di caratteri di output. Vengono utilizzate le impostazioni internazionali predefinite per l'account di accesso dell'utente che si connette tramite l'origine dati. Selezionare questa opzione per le applicazioni che effettuano solo la visualizzazione dei dati, non per quelle che consentono di elaborare i dati.

### <a name="save-long-running-queries-to-the-log-file"></a>Salva query a lunga esecuzione nel seguente file di log

Specifica che il driver registra qualsiasi query che richiede più tempo di **durata query lunghe** valore. Le query con esecuzione prolungata sono registrate nel file specificato. Per specificare un file di log, digitare il percorso completo e nome file nella casella oppure fare clic su **Sfoglia** per selezionare un file di log mediante l'esplorazione directory dei file esistenti.

### <a name="long-query-time-milliseconds"></a>Durata query lunghe (millisecondi)

Indica un valore soglia, espresso in millisecondi, per la registrazione delle query con esecuzione prolungata. Qualsiasi query con una durata superiore a questo numero di millisecondi viene registrata.

### <a name="log-odbc-driver-statistics-to-the-log-file"></a>Salva statistiche del driver ODBC nel seguente file di log

Indica che le statistiche verranno registrate nel file specificato. Per specificare un file di log, digitare il nome di file e percorso completo nella casella oppure fare clic su **Sfoglia** per selezionare un file di log mediante l'esplorazione directory dei file esistenti.

Il log delle statistiche è un file delimitato da tabulazioni che può essere analizzato in Microsoft Excel o in qualsiasi altra applicazione in grado di supportare i file delimitati da tabulazioni.

### <a name="connect-retry-count"></a>Numero di tentativi di connessione

Specifica il numero di tentativi di un tentativo di connessione non riuscito.

### <a name="connect-retry-interval-seconds"></a>Connettere l'intervallo tra tentativi (secondi)

Specifica il numero di secondi tra ogni tentativo di connessione. Per ulteriori informazioni sul funzionamento di questo e **conteggio tentativi di connessione** opzioni, vedere [resilienza delle connessioni nel Driver ODBC di Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).

### <a name="back"></a>Indietro

Fare clic su questo pulsante per tornare alla pagina precedente della procedura guidata.

### <a name="finish"></a>Fine

Se le informazioni specificate in questa schermata sono state complete, è possibile fare clic su **fine**. Il DSN viene creato utilizzando tutti gli attributi specificati in questa e altre schermate della procedura guidata e viene fornita la possibilità di testare il DSN appena creato.

## <a name="next-steps"></a>Passaggi successivi

[Schermata di creazione guidata origine dati 3](../../../connect/odbc/windows/dsn-wizard-3.md)
