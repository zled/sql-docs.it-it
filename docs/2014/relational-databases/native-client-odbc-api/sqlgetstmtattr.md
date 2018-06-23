---
title: SQLGetStmtAttr | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5c6f1220685b2e9f72df52ddea9c1f676453b856
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168082"
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client estende SQLGetStmtAttr per esporre attributi di istruzione specifici del driver.  
  
 [SQLSetStmtAttr](sqlsetstmtattr.md) Elenca gli attributi di istruzione che sono sia di lettura e scrittura. In questo argomento vengono elencati gli attributi dell'istruzione di sola lettura.  
  
## <a name="sqlsoptsscurrentcommand"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 L'attributo SQL_SOPT_SS_CURRENT_COMMAND espone il comando corrente di un batch di comandi. Il valore restituito è un numero intero che specifica il percorso del comando nel batch. Il *ValuePtr* valore è di tipo SQLLEN.  
  
## <a name="sqlsoptssnocountstatus"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 L'attributo SQL_SOPT_SS_NOCOUNT_STATUS indica l'impostazione corrente di NOCOUNT opzione che controlla se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] riporta i numeri di righe interessate da un'istruzione quando [SQLRowCount](sqlrowcount.md) viene chiamato. Il *ValuePtr* valore è di tipo SQLLEN.  
  
|valore|Description|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT è OFF. SQLRowCount restituisce numero di righe interessate.|  
|SQL_NC_ON|NOCOUNT è ON. Non viene restituito il numero di righe interessate da SQLRowCount e il valore restituito è 0.|  
  
 Se SQLRowCount restituisce 0, l'applicazione deve testare SQL_SOPT_SS_NOCOUNT_STATUS. Se viene restituito SQL_NC_ON, il valore 0 di SQLRowCount indica solo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non ha restituito un conteggio delle righe. Se viene restituito SQL_NC_OFF, significa che NOCOUNT è disattivato e il valore 0 di SQLRowCount indica che l'istruzione non ha avuto effetto su tutte le righe.  
  
 Le applicazioni non dovrebbero visualizzare il valore di SQLRowCount quando SQL_SOPT_SS_NOCOUNT_STATUS è sql_nc_off. Le stored procedure o i batch di grandi dimensioni possono contenere più istruzioni SET NOCOUNT, pertanto non è possibile presupporre che SQL_SOPT_SS_NOCOUNT_STATUS rimanga costante. Questa opzione deve essere testata ogni volta che SQLRowCount restituisce 0.  
  
## <a name="sqlsoptssquerynotificationmsgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 L'attributo SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT restituisce il testo del messaggio per la richiesta di notifica di query.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr e parametri con valori di tabella  
 SQLGetStmtAttr può essere chiamato per ottenere il valore di SQL_SOPT_SS_PARAM_FOCUS nel descrittore di parametri dell'applicazione (APD) quando si lavora con i parametri con valori di tabella. Per ulteriori informazioni su SQL_SOPT_SS_PARAM_FOCUS, vedere [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLSetStmtAttr](http://go.microsoft.com/fwlink/?LinkId=59370)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  