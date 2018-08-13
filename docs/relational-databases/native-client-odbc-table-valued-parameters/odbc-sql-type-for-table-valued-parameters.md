---
title: Tipo SQL ODBC per i parametri con valori di tabella | Documenti di Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 8353afa21266fdcb0e9a04e03cedee7113d634c2
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39542071"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>Tipo SQL ODBC per parametri con valori di tabella
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il supporto per i parametri con valori di tabella viene fornito da un nuovo tipo ODBC SQL, SQL_SS_TABLE.  
  
## <a name="remarks"></a>Note  
 SQL_SS_TABLE non può essere convertito in un altro tipo di dati ODBC o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se SQL_SS_TABLE viene utilizzato come un tipo di dati C il *ValueType* viene effettuata parametro SQLBindParameter, o un tentativo di impostare SQL_DESC_TYPE in un record descrittore (APD) parametro per SQL_SS_TABLE, viene restituito SQL_ERROR e un record di diagnostica viene generato con SQLSTATE = HY003, "tipo di buffer dell'applicazione non valida".  
  
 Se SQL_DESC_TYPE è impostato su SQL_SS_TABLE in un record IPD e il record del descrittore del parametro dell'applicazione corrispondente non è SQL_C_DEFAULT, viene restituito SQL_ERROR e viene generato un record di diagnostica con SQLSTATE=HY003, "Tipo di buffer dall'applicazione non valido". Questo problema può verificarsi con il *ParameterType* di SQLSetDescField, SQLSetDescRec o SQLBindParameter.  
  
 Se il *TargetType* parametro SQL_SS_TABLE durante la chiamata di SQLGetData, SQL_ERROR viene restituito e viene generato un record di diagnostico con SQLSTATE = HY003, "tipo di buffer dell'applicazione non valida".  
  
 Non è possibile associare una colonna di parametri con valori di tabella come tipo SQL_SS_TABLE. Se **SQLBindParameter** con *ParameterType* impostato su SQL_SS_TABLE, viene restituito SQL_ERROR e viene generato un record di diagnostico con SQLSTATE = HY004, "Tipo di dati SQL non valida". Ciò può verificarsi anche con SQLSetDescField e SQLSetDescRec.  
  
 I valori della colonna di parametri con valori di tabella presentano le stesse opzioni di conversione dei dati dei parametri e delle colonne dei risultati.  
  
 Un parametro con valori di tabella può essere solo un parametro di input in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o versioni successive. Se si tenta di impostare SQL_DESC_PARAMETER_TYPE su un valore diverso da SQL_PARAM_INPUT tramite la funzione SQLBindParameter o SQLSetDescField, viene restituito SQL_ERROR e viene aggiunto un record di diagnostico per l'istruzione con SQLSTATE = HY105 e il messaggio "parametro non valido digitare".  
  
 Colonne di parametri con valori di tabella è possono utilizzare SQL_DEFAULT_PARAM in *StrLen_or_IndPtr*, in quanto i valori predefiniti per riga non sono supportati con parametri con valori di tabella. È invece possibile impostare l'attributo della colonna SQL_CA_SS_COL_HAS_DEFAULT_VALUE su 1. Ciò significa che per tutte le righe della colonna saranno disponibili valori predefiniti. Se *StrLen_or_IndPtr* è impostata su SQL_DEFAULT_PARAM, SQLExecute o SQLExecDirect restituisce SQL_ERROR e verrà aggiunto un record di diagnostico per l'istruzione con SQLSTATE = HY090 e il messaggio "Non valido stringa o buffer length".  
  
## <a name="see-also"></a>Vedere anche  
 [I parametri con valori di tabella &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
