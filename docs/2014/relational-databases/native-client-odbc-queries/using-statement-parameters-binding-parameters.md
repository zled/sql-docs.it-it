---
title: Associazione di parametri | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f117cf02f863eb2c5d3dae602ce4503e71b885e1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423040"
---
# <a name="binding-parameters"></a>Associazione di parametri
  Ogni marcatore di parametro in un'istruzione SQL deve essere associato a una variabile nell'applicazione prima di eseguire l'istruzione. Questa operazione viene eseguita chiamando il [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) (funzione). **SQLBindParameter** descrive la variabile di programma (indirizzo, tipo di dati C e così via) al driver. La funzione identifica inoltre il marcatore di parametro specificandone il valore ordinale e quindi descrive le caratteristiche dell'oggetto SQL rappresentato (tipo di dati SQL, precisione e così via).  
  
 I marcatori di parametro possono essere associati o riassociati in qualunque momento prima di eseguire un'istruzione. Un'associazione di parametri rimane effettiva fino a quando non si verifica uno dei casi seguenti:  
  
-   Una chiamata a [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) con il *opzione* parametro impostato su SQL_RESET_PARAMS rilascia tutti i parametri associati all'handle di istruzione.  
  
-   Una chiamata a **SQLBindParameter** con *ParameterNumber* set per il numero ordinale di un marcatore di parametro associato rilascia automaticamente l'associazione precedente.  
  
 Un'applicazione può inoltre associare parametri a matrici di variabili di programma per elaborare un'istruzione SQL in batch. Sono disponibili due tipi diversi di associazione di matrici:  
  
-   L'associazione per colonna viene eseguita quando ogni singolo parametro viene associato alla relativa matrice di variabili.  
  
     L'associazione per colonna viene specificata chiamando [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) con *attributo* impostato su SQL_ATTR_PARAM_BIND_TYPE e *ValuePtr* impostato su SQL_PARAM_BIND_BY_COLUMN.  
  
-   L'associazione per riga viene eseguita quando tutti i parametri nell'istruzione SQL vengono associati come unità a una matrice di strutture contenente le singole variabili per i parametri.  
  
     L'associazione per riga viene specificata chiamando **SQLSetStmtAttr** con *attributo* impostato su SQL_ATTR_PARAM_BIND_TYPE e *ValuePtr* impostata sulle dimensioni dell'azienda struttura il variabili di programma.  
  
 Quando la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client Invia carattere o stringa binaria con parametri al server, aggiunge i valori alla lunghezza specificata **SQLBindParameter** *ColumnSize* parametro. Se un'applicazione ODBC 2.x specifica 0 per *ColumnSize*, il driver aggiunge il valore del parametro alla precisione del tipo di dati. La precisione è 8000 in caso di connessione a server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 255 in caso di connessione a versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *ColumnSize* è espressa in byte per le colonne variant.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta la definizione di nomi per parametri delle stored procedure. Anche in ODBC 3.5 è stato introdotto il supporto per parametri denominati utilizzati per chiamare stored procedure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo supporto può essere utilizzato per effettuare le operazioni seguenti:  
  
-   Chiamare una stored procedure e fornire valori per un subset dei parametri definiti per la stored procedure.  
  
-   Specificare i parametri in un ordine diverso nell'applicazione rispetto all'ordine specificato alla creazione della stored procedure.  
  
 I parametri denominati sono supportati solo quando si usa la [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` istruzione o la sequenza di escape ODBC CALL per eseguire una stored procedure.  
  
 Se per un parametro della stored procedure è impostato `SQL_DESC_NAME`, sarà necessario impostare `SQL_DESC_NAME` anche per tutti gli altri parametri della stored procedure nella query.  Se i valori letterali vengono usati nelle chiamate a stored procedure, in cui i parametri hanno `SQL_DESC_NAME` impostato, i valori letterali devono utilizzare il formato *' nome*=*valore*', dove *nome* è il nome di parametro della stored procedure (ad esempio, @p1). Per altre informazioni, vedere [Binding Parameters by Name (Named Parameters)](http://go.microsoft.com/fwlink/?LinkId=167215).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso dei parametri di un'istruzione](using-statement-parameters.md)  
  
  
