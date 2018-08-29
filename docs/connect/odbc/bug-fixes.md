---
title: Elenco dei bug corretti | Microsoft Docs
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
caps.latest.revision: 69
author: v-makouz
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 6ef479b95e62c2f489b06905b33318a877a60ad5
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785475"
---
# <a name="list-of-bugs-fixed"></a>Elenco dei bug corretti

Questa pagina contiene un elenco dei bug corretti in ogni versione, a partire da [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd"></a>Correzioni di bug nel [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.2 Driver ODBC per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Risolto un messaggio di errore sull'autenticazione di Azure Active Directory
- Correzione del rilevamento codifica quando le variabili di ambiente locali sono impostate in modo diverso
- Fissa un arresto anomalo del sistema al momento disconnettere con ripristino della connessione in corso
- Correzione del rilevamento di attività di connessione
- Correzione del rilevamento corretto di socket chiuso
- Correzione di un'attesa infinita quando si prova a un handle di istruzione di rilascio durante il ripristino non riuscito
- Corretto il comportamento di disinstallazione non corretto quando entrambe le versioni 13 e 17 sono installati in Windows
- Comportamento di decrittografia fisso sulla piattaforma Windows meno recente (Windows 7, 8 e Server 2012)
- Risolto un problema di cache quando si usa l'autenticazione ADAL in Windows
- Risolto un problema che è stato blocco e la sovrascrittura di traccia dei log da Windows

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd"></a>Correzioni di bug nel [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.1 Driver ODBC per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Risolto da 1 secondo ritardo quando si chiama la funzione SQLFreeHandle con MARS abilitato e attributo di connessione "Encrypt = yes"
- Corretto un arresto anomalo errore 22003 in SQLGetData quando la dimensione del buffer passato è inferiore, i dati recuperati (Windows)
- Correzione di messaggi di errore ADAL troncati
- Risolto un bug raro in Windows a 32 bit quando la conversione mobile numero a virgola a un integer
- Risolto un problema in cui l'inserimento di double nel campo di decimale con Always Encrypted in restituirebbe errore di troncamento dei dati
- Risolto un messaggio di avviso nel programma di installazione di MacOS
- L'invio corretto stato fisso per SQL Server durante il tentativo di ripristino della sessione quando resilienza della connessione e il pool di connessioni entrambe sono abilitate, causando sessione da eliminare dal Server

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd"></a>Correzioni di bug nel [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Risolto un bug in cui quando si usa l'autenticazione Kerberos, bulk insert può avere esito negativo con errore "accesso negato"
- Soluzione alternativa rimosso per un bug unixODBC presente nella versione sotto 2.3.1 (driver raddoppiato le dimensioni di alcuni buffer passato a unixODBC)
- Risolto resilienza della connessione (riconnessione) blocca quando si usa ColumnEncryption = abilitata
- Correzione di bug di creazione DSN, in cui quando utilizza "Autenticazione interattiva di Active Directory" l'opzione autenticazione di Azure finestra potrebbe diventare non risponde (Windows)
- Risolto un arresto anomalo raro durante l'arresto ODBC quando è abilitata l'esecuzione asincrona (si è verificato durante la cancellazione di handle di connessione)
- Risolto un problema in cui il Driver SQL causato utilizzo elevato di CPU durante l'esecuzione prolungata stored procedure
- Risolta l'impossibilità di recuperare i dati in una colonna varbinary (max) crittografati senza conversione
- Risolto un problema in cui dopo un null varchar (max) colonna crittografata viene recuperata usando SQLGetData() su un cursore statico, la colonna seguente viene annullata anche anche se dispone di dati
- Risolto un problema con il recupero di campi varbinary (max) con crittografia sempre attiva in
- Risolto un problema di setlocale non funziona con crittografia sempre attiva
- Risolto un problema con SQLDescribeParam() restituzione errore quando viene chiamato sul parametro di routine di tipo XML archiviato con crittografia sempre attiva in
- Caratteri di sottolineatura con caratteri di escape predefiniti non funziona in SQLTables
- Risolto un bug in cui i dati ebraici (varchar) viene troncati se viene restituito come caratteri wide in Linux
- Risolto un problema con l'esecuzione di query con codificata Shift-JIS char/varchar dall'applicazione UTF-8
- Correzione del bug in cui chiamando SQLGetInfo con parametro SQL_DRIVER_NAME restituito filename basato su Linux in MacOS
- Risolto un problema in cui il caricamento di dati di tipo carattere Windows-1252, utilizzando l'input file maggiore di 32 KB byte in colonne VARCHAR con l'utilità BCP potrebbero comportare errori
