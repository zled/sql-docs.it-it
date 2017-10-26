---
title: Schermata della procedura guidata 3, il Driver ODBC per SQL Server, dell'origine dati | Documenti Microsoft
ms.custom: 
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 1bda5a320e399888ed05331b3adbc2d29cf28022
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="data-source-wizard-screen-3"></a>Schermata di creazione guidata origine dati 3

Specificare il database predefinito, le varie opzioni ANSI che devono essere utilizzate dal driver e il nome di un server mirror.

## <a name="options"></a>Opzioni

### <a name="change-the-default-database-to"></a>Modificare il seguente database predefinito

Indica il nome del database predefinito per qualsiasi connessione stabilita utilizzando l'origine dati corrente. Se questa casella viene deselezionata, le connessioni utilizzeranno il database predefinito definito per l'ID di accesso nel server. Se questa casella viene selezionata, verrà utilizzato il database specificato anziché il database predefinito definito per l'ID di accesso. Se il **Associa file di database** casella con il nome di un file primario, il database descritto dal file primario è collegato un database utilizzando il nome del database specificato nella **modificare il database predefinito per**casella.

L'utilizzo del database predefinito per l'ID di accesso è più efficiente rispetto all'impostazione di un database predefinito nell'origine dati ODBC.

### <a name="mirror-server"></a>Server mirror

Indica il nome del partner di failover del database da sottoporre a mirroring. Se un nome di database non è disponibile nella finestra di **modificare il database predefinito per** casella o il nome visualizzato è il database predefinito, **Server Mirror** è inattivo.

Facoltativamente, è possibile specificare un nome SPN per il server mirror. Tale nome verrà utilizzato per l'autenticazione reciproca tra client e server.

### <a name="attach-database-filename"></a>Associa file di database

Indica il nome del file primario di un database a cui è possibile collegarsi. Questo database viene associato e utilizzato come database predefinito per l'origine dati. Specificare il percorso completo e il nome del file primario. Il nome del database specificato nella **modificare il database predefinito per** casella viene utilizzata come nome per il database collegato.

### <a name="use-ansi-quoted-identifiers"></a>Usa identificatori ANSI tra virgolette

Specifica che è necessario impostare QUOTED_IDENTIFIERS quando si connette il driver ODBC per SQL Server. Quando questa casella di controllo è selezionata, SQL Server applica le regole ANSI relative alle virgolette. Le virgolette doppie possono essere utilizzate solo per gli identificatori, ad esempio i nomi delle colonne e delle tabelle. Le stringhe di caratteri devono essere racchiuse tra virgolette singole:

```
SELECT "LastName"
FROM "Person.Contact"
WHERE "LastName" = 'O''Brien'
```

Se questa casella di controllo viene deselezionata, le applicazioni che utilizzano gli identificatori tra virgolette, ad esempio l'utilità Microsoft Query distribuita con Microsoft Excel, provocano errori quando generano istruzioni SQL con identificatori tra virgolette.

### <a name="use-ansi-nulls-paddings-and-warnings"></a>Utilizzare i valori Null ANSI, riempimenti e avvisi

Specifica che è necessario impostare le opzioni ANSI_NULLS, ANSI_WARNINGS e ANSI_PADDINGS quando si connette il Driver ODBC per SQL Server.

Se ANSI_NULLS è impostato, il server applica le regole ANSI relative al confronto delle colonne per individuare i valori NULL. La sintassi ANSI "IS NULL" o "IS NOT NULL" deve essere utilizzata per tutti i confronti di valori NULL. La sintassi Transact-SQL "= NULL" non è supportata.

ANSI_WARNINGS è impostato su, SQL Server inoltra i messaggi di avviso per le condizioni che violano le regole ANSI ma non violino le regole di Transact-SQL. Esempi di tali errori sono il troncamento dei dati durante l'esecuzione di un'istruzione INSERT o UPDATE oppure il rilevamento di un valore Null durante una funzione di aggregazione. 

Con l'opzione ANSI_PADDING è impostata, gli spazi vuoti finali in **varchar** valori e gli zeri finali nei **varbinary** valori non vengono rimossi automaticamente.

### <a name="application-intent"></a>Finalità dell'applicazione

Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.

### <a name="multi-subnet-failover"></a>Failover su più subnet

Se l'applicazione si connette a un a disponibilità elevata disaster recovery (gruppi di disponibilità AlwaysOn) gruppo di disponibilità (AG) in subnet diverse, abilitare **failover su più subnet.** Configura il Driver ODBC per SQL Server fornire un rilevamento più veloce e connessione al server attualmente attivo.

### <a name="transparent-network-ip-resolution"></a>Risoluzione IP di rete Transparent.

Modifica il comportamento della **failover su più subnet** per consentire la riconnessione più veloce durante il failover. Vedere [utilizzando la risoluzione IP di rete Transparent](../../../connect/odbc/using-transparent-network-ip-resolution.md) per ulteriori informazioni.

### <a name="column-encryption"></a>Crittografia di colonna.

Consente la decrittografia automatica e la crittografia dei trasferimenti di dati da e verso le colonne crittografate con la [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) funzionalità disponibili in SQL Server 2016 e versioni successive.

### <a name="next"></a>Avanti

Passare alla schermata successiva della procedura guidata.

### <a name="back"></a>Indietro

Consente di tornare alla schermata precedente della procedura guidata.

## <a name="next-steps"></a>Passaggi successivi

[Schermata di creazione guidata origine dati 2](../../../connect/odbc/windows/dsn-wizard-2.md)

[Schermata di creazione guidata origine dati 4](../../../connect/odbc/windows/dsn-wizard-4.md)

