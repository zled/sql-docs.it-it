---
title: Connettersi a Sybase (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 524f95ef-10bd-497c-84ca-c06a0ae794fb
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2152c6a02a7c02d7aea5fb5ab01c2aa5b74dfad4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-sybase-sybasetosql"></a>Connettersi a Sybase (SybaseToSQL)
Utilizzare il **Connetti Sybase** finestra di dialogo per connettersi all'istanza di Sybase Adaptive Server Enterprise (ASE) che si desidera eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **Connetti Sybase**. Se in precedenza si è connessi, il comando è **riconnessione per Sybase**.  
  
## <a name="options"></a>Opzioni  
**Provider**  
Selezionare una qualsiasi del Provider installato nel computer per la connessione al Server di Sybase.  
  
**Mode**  
Selezionare entrambe le modalità di connessione standard o avanzata. In modalità standard, immettere o selezionare i valori per il nome del server, porta, nome utente e password. Nella modalità avanzata è fornire una stringa di connessione.  
  
**Nome server**  
Immettere o selezionare il nome o indirizzo IP del Server adattivo. Il nome del server predefinito è lo stesso nome del computer. Questa è un'opzione di modalità standard.  
  
**Porta server**  
Se si utilizza una porta non predefinita per le connessioni a ASE, immettere il numero di porta. Il numero di porta predefinito è 5000. Questa è un'opzione di modalità standard.  
  
**Nome utente**  
Immettere il nome utente utilizzato per connettersi a ASE. Questa è un'opzione di modalità standard.  
  
**Password**  
Immettere la password associata al nome utente. Questa è un'opzione di modalità standard.  
  
**Stringa di connessione**  
Immettere la stringa di connessione completa per la connessione di base.  
  
Le stringhe di connessione è costituito da coppie nome / valore di parametro. I nomi dei parametri variano con il provider in uso.  
  
**Parametri di connessione per diversi provider sono i seguenti:**  
  
1.  Parametri di connessione per **Provider OLE DB**  
  
    |Impostazione|Parametro Sybase 12,5|Parametro Sybase 15|  
    |-----------|-------------------------|-----------------------|  
    |Nome server|Nome server|Server|  
    |Porta|Indirizzo di porta del server|Porta|  
    |Nome utente|ID utente|ID utente|  
    |Password|Password|Password|  
    |Provider|Provider|Provider|  
  
    Per Sybase ASE 12,5, una stringa di connessione di esempio è la seguente:  
  
    `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
    Per Sybase ASE 15, una stringa di connessione di esempio è la seguente:  
  
    `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=ASEOLEDB;Port=5000;`  
  
2.  Parametri di connessione per **Provider ODBC**  
  
    |Impostazione|Parametro Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nome del driver|Driver|  
    |Nome server|Server|  
    |Nome utente|Uid|  
    |Password|Pwd|  
    |Numero di porta|Porta|  
  
    Per Sybase ASE 12,5 o 15, una stringa di connessione di esempio è la seguente:  
  
    `driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
3.  Parametri di connessione per **Provider ADO.NET**  
  
    |Impostazione|Parametro Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nome server|Server|  
    |Nome utente|Uid|  
    |Password|Pwd|  
    |Numero di porta|Porta|  
  
    Un esempio di stringa di connessione per il Provider ADO.NET è come segue:  
  
    `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
Per ulteriori informazioni, vedere la documentazione di base.  
  
Si tratta di un'opzione di modalità avanzata.  
  
