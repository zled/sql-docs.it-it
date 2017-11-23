---
title: La connessione a DB2 (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9d485fd0-ab5d-402a-a59a-e9982a61b7de
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ecdb36c546d04421f30573bd4b34ae60467e7f64
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="connect-to-db2-db2tosql"></a>La connessione a DB2 (DB2ToSQL)
Utilizzare il **connessione a DB2** la finestra di dialogo per la connessione al database DB2 che si desidera eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **connessione a DB2**. Se in precedenza si è connessi, il comando è **Riconnetti a DB2**.  
  
## <a name="options"></a>Opzioni  
**Provider**  
Selezionare il provider di accesso ai dati per la connessione al database DB2. I provider disponibili sono il Provider Client DB2 e il Provider OLE DB. Il valore predefinito è il Provider Client DB2.  
  
**Mode**  
Selezionare la modalità Standard, TNSNAME o stringa di connessione.  
  
-   In modalità Standard, immettere o selezionare i valori per il provider, nome del server, porta del server, DB2 SID, nome utente e password.  
  
-   In modalità TNSNAME, immettere l'identificatore di connessione (alias TNS) del database DB2, nome utente e password.  
  
-   In modalità di stringa di connessione, si fornisce una stringa di connessione.  
  
    > [!IMPORTANT]  
    > Non è consigliabile utilizzare la modalità di stringa di connessione perché il testo potrebbe includere le password, e vengono inviato come testo non crittografato.  
  
Il valore predefinito è la modalità Standard.  
  
**Nome server**  
Immettere il nome del server DB2. Il nome del server predefinito è lo stesso nome del computer. Questa è un'opzione di modalità Standard.  
  
**Porta server**  
Se si utilizza un numero di porta diverso da 1521 (impostazione predefinita) per le connessioni a DB2, immettere il numero di porta. Questa è un'opzione di modalità Standard.  
  
**Identificatore di connessione**  
Immettere DB2 connect identificatore. Questo è l'alias del database, come definito nel file tnsnames.ora locale.  
  
Questa è un'opzione di modalità TNSNAME.  
  
**DB2 SID**  
Immettere il SID per il database. Il SID è un identificatore che distingue i database di DB2 in un computer. Il valore predefinito di SID per un database è i primi otto caratteri del nome del database.  
  
Questa è un'opzione di modalità Standard.  
  
**User name**  
Immettere il nome utente utilizzato per connettersi al database DB2 SSMA.  
  
**Password**  
Immettere la password associata al nome utente.  
  
**Stringa di connessione**  
> [!IMPORTANT]  
> Non è consigliabile utilizzare la modalità di stringa di connessione perché il testo potrebbe includere le password, e vengono inviato come testo non crittografato.  
  
Se si utilizza la modalità di stringa di connessione, immettere la stringa di connessione completa per la connessione a DB2.  
  
Le stringhe di connessione è costituito da coppie nome / valore di parametro.  
  
-   Per informazioni sulla stringa di connessione OLE DB, vedere [il Provider Microsoft OLE DB per DB2](http://go.microsoft.com/fwlink/?LinkId=85640) articolo in MSDN Library.  
  
Per le stringhe di connessione di SSMA sempre includere il parametro del Provider. Inoltre, assicurarsi di includere il parametro Port quando ci si connette a DB2.  
  
