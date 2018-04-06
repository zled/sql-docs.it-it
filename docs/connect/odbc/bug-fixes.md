---
title: Elenco dei bug corretti | Documenti Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
caps.latest.revision: 69
author: v-makouz
ms.author: genemi
manager: kenvh
ms.workload: Active
ms.openlocfilehash: dc71f74ca8e81f370037b82e42fd78957e096775
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/05/2018
---
# <a name="list-of-bugs-fixed"></a>Elenco di bug risolti

Questa pagina contiene un elenco di bug in ogni versione, a partire da [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17 Driver ODBC per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversionmdmd"></a>Correzioni di bug nel [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17.1 Driver ODBC per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

- Fisso da 1 secondo ritardo quando si chiama la funzione SQLFreeHandle con MARS abilitato e attributo di connessione "Encrypt = yes"
- Fissa un arresto anomalo del sistema errore 22003 in SQLGetData quando le dimensioni del buffer passato sono minore, i dati recuperati (Windows)
- Messaggi di errore ADAL troncati fissa
- Correzione di un bug raro in Windows a 32 bit quando la conversione mobile numero a virgola in un intero
- Non risolto un problema in cui verrebbe inserimento double nel campo decimale con crittografia sempre attiva in alcun errore di troncamento di dati restituito
- Fissa un avviso nel programma di installazione MacOS

### <a name="bug-fixes-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd"></a>Correzioni di bug nel [!INCLUDE[msCoName](../../includes/msconame_md.md)] 17 Driver ODBC per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]

- Fisso l'invio di stato non corretto a SQL Server durante il tentativo di ripristino della sessione quando resilienza di connessione sia il pool di connessioni sono abilitati, causando sessione da eliminare dal Server
- Correzione di un bug in quando si utilizza l'autenticazione Kerberos, bulk insert potrebbe non riuscire con errore "accesso negato"
- Soluzione alternativa rimosso per un bug unixODBC presente nella versione precedente a 2.3.1 (driver raddoppiato le dimensioni di alcuni buffer passato a unixODBC)
- Fissa resilienza delle connessioni (riconnessione) sporgente quando si utilizza ColumnEncryption = abilitata
- Correzione di bug di creazione DSN, in cui quando utilizza "L'autenticazione di Active Directory interattivo" l'opzione autenticazione di Azure finestra potrebbe diventare non risponde (Windows)
- Fissa un arresto anomalo del sistema rari durante l'arresto ODBC quando è abilitata l'esecuzione asincrona (si è verificato durante la cancellazione di handle di connessione)
- Risolto un problema in cui il Driver SQL causato elevato della CPU durante l'esecuzione prolungata stored procedure
- Fisso impossibilità di recuperare i dati in una colonna varbinary (max) crittografata senza conversione
- Risolto un problema in cui dopo un varchar (max) null colonna crittografata viene recuperata mediante SQLGetData() su un cursore statico, la colonna seguente viene annullata anche anche se dispone di dati
- Risolto un problema con il recupero di campo varbinary (max) con crittografia sempre attiva in
- Risolto un problema di setlocale non funziona con crittografia sempre attiva
- Risolto un problema con SQLDescribeParam() restituzione errore quando viene chiamato nel parametro di routine di tipo XML archiviato con crittografia sempre attiva su
- Caratteri di sottolineatura con caratteri di escape predefiniti non funziona in SQLTables
- Correzione di un bug in cui i dati ebraici (varchar) viene troncati se viene restituito come caratteri "wide" in Linux
- Risolto un problema con l'esecuzione di query con codificata Shift-JIS char/varchar dall'applicazione UTF-8
- Correzione del bug in cui la chiamata a SQLGetInfo con parametro SQL_DRIVER_NAME restituito filename Linux-style su MacOS
- Risolto un problema in cui il caricamento di dati di tipo carattere Windows-1252, utilizzando l'input file maggiore di 32 KB byte in colonne VARCHAR tramite l'utilità BCP darà errori
