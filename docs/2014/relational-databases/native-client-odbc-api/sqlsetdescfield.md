---
title: SQLSetDescField | Documenti Microsoft
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
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bf61530ccfd142b473da8a5443cc63b16a435d32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062392"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
  SQLSetDescField può essere utilizzato per impostare i campi di descrizione per i parametri con valori di tabella e le colonne dei parametri con valori di tabella. Per informazioni sui campi disponibili, vedere [campi di descrizione dei parametri con valori di tabella](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) e [campi di descrizione per le colonne costitutive dei parametri con valori di tabella](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).  
  
## <a name="remarks"></a>Remarks  
 Le colonne dei parametri con valori di tabella sono disponibili solo quando il campo di intestazione di descrizione SQL_SOPT_SS_PARAM_FOCUS è impostato sul numero ordinale di un record in cui SQL_DESC_TYPE è impostato su SQL_SS_TABLE. Per ulteriori informazioni su SQL_SOPT_SS_PARAM_FOCUS, vedere [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Se viene effettuato un tentativo di impostare SQL_SOPT_SS_PARAM_FOCUS sul numero ordinale di un parametro che non è un parametro con valori di tabella, la funzione SQLSetStmtAttr restituisce SQL_ERROR e viene creato un record di diagnostica con SQLSTATE = HY024 e il messaggio "valore attributo non valido". SQL_SOPT_SS_PARAM_FOCUS non viene modificato al momento della restituzione di SQL_ERROR.  
  
 L'impostazione di SQL_SOPT_SS_PARAM_FOCUS su 0 ripristina l'accesso ai record del descrittore per i parametri.  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>Supporto di SQLSetDescField per le caratteristiche avanzate di data e ora  
 Le caratteristiche di data/ora sono state migliorate in ODBC. Per informazioni sul campo di descrizione fornito per i tipi di nuovo data/ora, vedere [metadati per parametri e risultati](../native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Per altre informazioni, vedere [data e ora miglioramenti &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>Supporto di SQLSetDescField per tipi CLR definiti dall'utente di grandi dimensioni  
 SQLSetDescField supporta grandi CLR tipi definiti dall'utente (UDT). Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>Supporto di SQLSetDescField per colonne di tipo sparse  
 SQLSetDecField può essere utilizzato per impostare SQL_SOPT_SS_NAME_SCOPE nel descrittore di parametri dell'applicazione (APD) sui valori SQL_SS_NAME_SCOPE_EXTENDED e SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.  
  
 Per altre informazioni, vedere [supporto per colonne di tipo Sparse &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLSetDescField](http://go.microsoft.com/fwlink/?LinkId=80705)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  