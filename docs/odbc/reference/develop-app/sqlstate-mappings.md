---
title: Mapping di SQLSTATE | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSTATE
- backward compatibility [ODBC], SQLSTATE
- SQLSTATE [ODBC]
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8226e7fa29cf94b4eff222022d4a94895dcd0e82
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914386"
---
# <a name="sqlstate-mappings"></a>Mapping di SQLSTATE
In questo argomento vengono descritti i valori SQLSTATE per ODBC 2. *x* e ODBC 3. *x*. Per ulteriori informazioni su ODBC 3. *x* valori SQLSTATE, vedere [codici di errore ODBC appendice a:](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 In ODBC 3. *x*HYxxx SQLSTATE restituiti anziché S1xxx e vengono restituiti 42Sxx SQLSTATE anziché S00XX. Questa operazione è stata eseguita per conformità con gli standard Open Group e ISO. In molti casi, il mapping non è univoca perché gli standard hanno ridefinito l'interpretazione di SQLSTATE diversi.  
  
 Quando un'applicazione ODBC 2. *x* applicazione viene aggiornata a un'applicazione ODBC 3. *x* applicazione, l'applicazione deve essere modificato in modo da prevedere ODBC 3. *x* SQLSTATE anziché ODBC 2. *x* SQLSTATE. Nella tabella seguente sono elencati ODBC 3. *x* SQLSTATE che ogni ODBC 2. *x* SQLSTATE è mappata a.  
  
 Quando l'attributo di ambiente SQL_ATTR_ODBC_VERSION è impostato su SQL_OV_ODBC2, il driver invia ODBC 2. *x* SQLSTATE anziché ODBC 3. *x* SQLSTATE quando **SQLGetDiagField** o **SQLGetDiagRec** viene chiamato. Un mapping specifico può essere determinato osservando ODBC 2*x* SQLSTATE, nella colonna 1 della tabella seguente che corrisponde a ODBC 3. *x* SQLSTATE, nella colonna 2.  
  
|ODBC 2. *x* SQLSTATE|ODBC 3. *x* SQLSTATE|Commenti|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24000|07005||  
|37000|42000||  
|70100|HY018||  
|S0001|42S01||  
|S0002|42S02||  
|S0011|42S11||  
|S0012|42S12||  
|S0021|42S21||  
|S0022|42S22||  
|S0023|42S23||  
|S1000|HY000||  
|S1001|HY001||  
|S1002|07009|ODBC 2. *x* S1002 SQLSTATE è mappata a ODBC 3. *x* SQLSTATE 07009 se la funzione sottostante **SQLBindCol**, **SQLColAttribute**, **SQLExtendedFetch**, **SQLFetch** , **SQLFetchScroll**, o **SQLGetData**.|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Restituito per un utilizzo non valido di un puntatore null.|  
|S1009|HY024|Ha restituito un valore di attributo non valido.|  
|S1009|HY092|Restituito per l'aggiornamento o eliminazione di dati da una chiamata a **SQLSetPos**, o aggiunta, aggiornamento o eliminazione di dati da una chiamata a **SQLBulkOperations**, quando la concorrenza è di sola lettura.|  
|S1010|HY007 HY010|SQLSTATE S1010 viene eseguito il mapping di SQLSTATE HY007 quando **SQLDescribeCol** viene chiamato prima di chiamare **SQLPrepare**, **SQLExecDirect**, o una funzione di catalogo per il *StatementHandle*. SQLSTATE S1010 in caso contrario, viene eseguito il mapping di SQLSTATE HY010.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC 3. *x* SQLSTATE 07009 viene eseguito il mapping a ODBC 2. *x* S1093 SQLSTATE se la funzione sottostante **SQLBindParameter** o **SQLDescribeParam**.|  
|S1096|HY096||  
|S1097|HY097||  
|S1098|HY098||  
|S1099|HY099||  
|S1100|HY100||  
|S1101|HY101||  
|S1103|HY103||  
|S1104|HY104||  
|S1105|HY105||  
|S1106|HY106||  
|S1107|HY107||  
|S1108|HY108||  
|S1109|HY109||  
|S1110|HY110||  
|S1111|HY111||  
|S1C00|HYC00||  
|S1T00|HYT00||  
  
> [!NOTE]  
>  ODBC 3. *x* SQLSTATE 07008 viene eseguito il mapping a ODBC 2. *x* SQLSTATE S1000.
