---
title: Connettersi a Oracle (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23a48cb6-ff30-49bb-b4a7-603ebcab336f
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d685be15fb8d0c6fea21d539e3370b3377316324
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="connect-to-oracle-oracletosql"></a>Connettersi a Oracle (OracleToSQL)
Utilizzare il **Connect to Oracle** la finestra di dialogo per la connessione al database Oracle che si desidera eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **Connect to Oracle**. Se in precedenza si è connessi, il comando è **Riconnetti a Oracle**.  
  
## <a name="options"></a>Opzioni  
**Provider**  
Selezionare il provider di accesso ai dati per la connessione al database Oracle. I provider disponibili sono il Provider Client Oracle e il Provider OLE DB. Il valore predefinito è il Provider Client Oracle.  
  
**Mode**  
Selezionare la modalità Standard, TNSNAME o stringa di connessione.  
  
-   In modalità Standard, immettere o selezionare i valori per il provider, nome del server, porta del server, Oracle SID, nome utente e password.  
  
-   In modalità TNSNAME, immettere l'identificatore di connessione (alias TNS) del database Oracle, nome utente e password.  
  
-   In modalità di stringa di connessione, si fornisce una stringa di connessione.  
  
    > [!IMPORTANT]  
    > Non è consigliabile utilizzare la modalità di stringa di connessione perché il testo potrebbe includere le password, e vengono inviato come testo non crittografato.  
  
Il valore predefinito è la modalità Standard.  
  
**Nome server**  
Immettere il nome del server Oracle. Il nome del server predefinito è lo stesso nome del computer. Questa è un'opzione di modalità Standard.  
  
**Porta server**  
Se si utilizza un numero di porta diverso da 1521 (impostazione predefinita) per le connessioni a Oracle, immettere il numero di porta. Questa è un'opzione di modalità Standard.  
  
**Identificatore di connessione**  
Immettere il Oracle connettersi identificatore. Questo è l'alias del database, come definito nel file tnsnames.ora locale.  
  
Questa è un'opzione di modalità TNSNAME.  
  
**SID Oracle**  
Immettere il SID per il database. Il SID è un identificatore che distingue i database Oracle in un computer. Il valore predefinito di SID per un database è i primi otto caratteri del nome del database.  
  
Questa è un'opzione di modalità Standard.  
  
**Nome utente**  
Immettere il nome utente utilizzato per connettersi al database Oracle SSMA.  
  
**Password**  
Immettere la password associata al nome utente.  
  
**Stringa di connessione**  
> [!IMPORTANT]  
> Non è consigliabile utilizzare la modalità di stringa di connessione perché il testo potrebbe includere le password, e vengono inviato come testo non crittografato.  
  
Se si utilizza la modalità di stringa di connessione, immettere la stringa di connessione completa per la connessione a Oracle.  
  
Le stringhe di connessione è costituito da coppie nome / valore di parametro.  
  
-   Per informazioni sulla stringa di connessione OLE DB, vedere [il Provider Microsoft OLE DB per Oracle](http://go.microsoft.com/fwlink/?LinkId=85640) articolo in MSDN Library.  
  
Per le stringhe di connessione di SSMA sempre includere il parametro del Provider. Inoltre, assicurarsi di includere il parametro Port quando ci si connette a Oracle.  
  

