---
title: Supporto SQLGetInfo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
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
- compatibility [ODBC], SQLGetInfo
- backward compatibility [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], support
ms.assetid: 57326f57-daba-46b6-b0be-6c97213b9ef1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 91f38a5c5ad19d5df6e253ee2fdbf7bf44eec930
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetinfo-support"></a>Supporto SQLGetInfo
Quando un'applicazione ODBC 2. *x* applicazione chiama **SQLGetInfo** per un'applicazione ODBC 3*x* driver, il *InfoType* argomenti nella tabella seguente devono essere supportati.  
  
|*InfoType*|Valori di codice restituiti|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0) **Nota:** questo tipo di informazioni non è deprecato e sono deprecate le maschere di bit nella colonna a destra.|Una maschera di bit SQLINTEGER durante l'enumerazione delle clausole nel **ALTER TABLE** supportati dall'origine dati.<br /><br /> Le maschere di bit seguenti vengono utilizzati per determinare le clausole sono supportate:<br /><br /> SQL_AT_DROP_COLUMN = è supportata la possibilità di eliminare le colonne. Se questo comporta cascade o limitare il comportamento è definito dal driver. (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN = la possibilità di aggiungere più colonne in un'unica istruzione ALTER TABLE è supportata. Questo bit non consente di combinare con gli altri bit SQL_AT_ADD_COLUMN_XXX o bit SQL_AT_CONSTRAINT_XXX. (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> Il tipo di informazioni è stata introdotta in ODBC 1.0; ogni maschera di bit viene etichettato con la versione in cui è stato introdotto.|Maschera di bit SQLINTEGER l'enumerazione delle opzioni di direzione fetch supportata.<br /><br /> Le maschere di bit seguenti vengono utilizzati in combinazione con il flag per determinare quali opzioni sono supportate:<br /><br /> (ODBC 1.0) SQL_FD_FETCH_NEXT SQL_FD_FETCH_FIRST (ODBC 1.0) SQL_FD_FETCH_LAST (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_RELATIVE (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|I tipi di una maschera di bit SQLINTEGER l'enumerazione del blocco supportato per il *gruppo* argomento **SQLSetPos**.<br /><br /> Le maschere di bit seguenti vengono utilizzati in combinazione con il flag per determinare quali tipi di blocco sono supportati:<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|Un valore SQLSMALLINT che indica il livello di conformità di ODBC.<br /><br /> SQL_OAC_NONE = nessuno<br /><br /> SQL_OAC_LEVEL1 = 1 livello supportato<br /><br /> SQL_OAC_LEVEL2 = livello 2 è supportato|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|Un valore SQLSMALLINT che indica la grammatica SQL supportata dal driver. Vedere [grammatica SQL di appendice c:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) per una definizione dei livelli di conformità di SQL.<br /><br /> SQL_OSC_MINIMUM = grammatica minima supportata<br /><br /> SQL_OSC_CORE = supportata la sintassi di base<br /><br /> SQL_OSC_EXTENDED = grammatica estesa supportata|  
|SQL_POS_OPERATIONS (ODBC 2.0)|Una maschera di bit SQLINTEGER enumerazione le operazioni supportate in **SQLSetPos**.<br /><br /> Le maschere di bit seguenti sono utilizzati in abbinamento con il flag per determinare quali opzioni sono supportate:<br /><br /> SQL_POS_POSITION (ODBC 2.0) (ODBC 2.0) SQL_POS_REFRESH SQL_POS_UPDATE (ODBC 2.0) (ODBC 2.0) SQL_POS_DELETE SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|Una maschera di bit SQLINTEGER enumerazione supportati posizionato istruzioni SQL.<br /><br /> Le maschere di bit seguenti vengono utilizzati per determinare quali istruzioni sono supportati:<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|Maschera di bit SQLINTEGER enumerazione le opzioni di controllo della concorrenza è supportate per il cursore.<br /><br /> Le maschere di bit seguenti vengono utilizzati per determinare quali opzioni sono supportate:<br /><br /> SQL_SCCO_READ_ONLY = cursore è di sola lettura. Non sono consentiti aggiornamenti.<br /><br /> SQL_SCCO_LOCK = cursore utilizza il livello più basso di blocco sufficiente a garantire che la riga può essere aggiornata.<br /><br /> SQL_SCCO_OPT_ROWVER = controllo della concorrenza ottimistica utilizza cursori, confrontare le versioni di riga, ad esempio SQLBase ROWID o Sybase TIMESTAMP.<br /><br /> SQL_SCCO_OPT_VALUES = controllo della concorrenza ottimistica utilizza cursori, il confronto di valori.|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|Un'enumerazione di maschera di bit SQLINTEGER se le modifiche apportate da un'applicazione a un cursore statico o basati su keyset tramite **SQLSetPos** o per gli aggiornamenti posizionati o le istruzioni delete possono essere rilevate dall'applicazione.<br /><br /> SQL_SS_ADDITIONS = sono state aggiunte le righe sono visibili per il cursore. il cursore è possibile scorrere a queste righe. In queste righe vengono aggiunte al cursore è dipendente dal driver.<br /><br /> SQL_SS_DELETIONS = eliminate le righe non sono più disponibili fino al cursore e non lasciare un foro"" nel set di risultati. Dopo il cursore passa da una riga eliminata, è possibile tornare alla riga.<br /><br /> SQL_SS_UPDATES = gli aggiornamenti alle righe sono visibili per il cursore. Se il cursore scorre dall'e restituisce una riga aggiornata, i dati restituiti dal cursore sono i dati aggiornati, non i dati originali. Questa opzione si applica solo a cursori o aggiornamenti sui cursori basati su keyset che non si aggiornano la chiave. Questa opzione non è valida per un cursore dinamico o nel caso in cui viene modificata una chiave in un cursore misto.<br /><br /> Se un'applicazione può rilevare le modifiche apportate al set di risultati tramite altri utenti, inclusi altri cursori nella stessa applicazione, varia a seconda del tipo di cursore.|  
  
 Un'applicazione ODBC 3*x* applicazione che utilizza un'applicazione ODBC 3*x* driver non deve chiamare **SQLGetInfo** con il *InfoType* argomenti descritti precedente tabella, ma devono utilizzare ODBC 3*x* *InfoType* gli argomenti riportati nel paragrafo seguente. Non c'è una corrispondenza uno a uno tra *InfoType* argomenti utilizzati in ODBC 2. *x* e quelli utilizzati in ODBC 3*x*. Un'applicazione ODBC 3*x* applicazione che utilizza un ODBC 2. *x* driver, d'altra parte, deve utilizzare il *InfoType* argomenti descritti in precedenza.  
  
 Alcuni dei tipi di informazioni nella tabella precedente sono deprecate a favore dei tipi di informazioni di attributi di cursore. Questi deprecata informazioni tipi sono SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY e SQL_STATIC_SENSITIVITY. I nuovi tipi di attributi del cursore sono SQL_XXX_CURSOR_ATTRIBUTES2 SQL_XXX_CURSOR_ATTRIBUTES1and, dove XXX è uguale a DYNAMIC, FORWARD_ONLY, KEYSET_DRIVEN o statico. Ognuno dei nuovi tipi indica le funzionalità del driver per un tipo di cursore singolo. Per ulteriori informazioni su queste opzioni, vedere il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione della funzione.
