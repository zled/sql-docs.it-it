---
title: Utilizzo del tipo di dati | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-results
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC data types
- ODBC data types, about ODBC data types
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC]
- SQL Server Native Client ODBC driver, data types
- data types [ODBC], about data types
ms.assetid: 4f19b0d6-94ac-4a98-a121-57d38787864c
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 385a12cb44b6f9a6841e1480035edd3de7ee8e59
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="data-type-usage"></a>Utilizzo del tipo di dati
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] imporre l'utilizzo dei tipi di dati seguente.  
  
|Tipo di dati|Limitazione|  
|---------------|----------------|  
|Valori letterali data|Data di valori letterali, viene archiviato in una colonna SQL_TYPE_TIMESTAMP ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati di **datetime** o **smalldatetime**), hanno un valore di 12:00:00.000 AM.|  
|**Money** e **smallmoney**|Solo le parti intere del **money** e **smallmoney** tipi di dati sono significativi. Se la parte decimale di SQL **money** dati vengono troncati durante la conversione di tipi di dati, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client restituisce un avviso, non un errore.|  
|SQL_BINARY (ammette valori Null)|Quando viene eseguita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 6.0 e precedente, se una colonna SQL_BINARY ammette valori Null, i dati archiviati nell'origine dati non possono essere riempiti di zeri. Quando vengono recuperati i dati da una colonna di questo tipo, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client viene riempito di zeri a destra. Nei dati che vengono creati in operazioni eseguite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio la concatenazione, tale riempimento non viene eseguito.<br /><br /> Quando inoltre i dati vengono posizionati in una colonna di questo tipo in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 o versione precedente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tronca i dati a destra, se non entrano nella colonna.<br /><br /> Nota: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 e versioni precedenti.|  
|SQL_CHAR (troncamento)|Quando si esegue la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.0 e versione precedente e i dati vengono inseriti in una colonna SQL_CHAR, se i dati non entrano nella colonna, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] li tronca a destra senza visualizzare alcun avviso.<br /><br /> Nota: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 e versioni precedenti.|  
|SQL_CHAR (ammette valori Null)|Quando viene eseguita una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 6.0 e precedente, se una colonna SQL_CHAR ammette valori Null, i dati archiviati nell'origine dati non possono essere riempiti con spazi. Quando vengono recuperati i dati da una colonna di questo tipo, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client viene riempito con spazi vuoti a destra. Nei dati che vengono creati in operazioni eseguite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio la concatenazione, tale riempimento non viene eseguito.<br /><br /> Nota: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 e versioni precedenti.|  
|SQL_LONGVARBINARY, SQL_LONGVARCHAR, SQL_WLONGVARCHAR|Gli aggiornamenti delle colonne con SQL_LONGVARBINARY, SQL_LONGVARCHAR o SQL_WLONGVARCHAR tipi di dati (tramite una clausola WHERE) che interessano più righe sono completamente supportati quando si è connessi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6. *x* e versioni successive. Quando si è connessi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, un errore S1000, "inserimento o aggiornamento parziale. L'inserimento o l'aggiornamento del testo o delle colonne di immagini non è stato completato", se l'aggiornamento riguarda più di una riga.<br /><br /> Nota: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 e versioni precedenti.|  
|Parametri delle funzioni per i valori stringa|*string_exp* parametri alla stringa di funzioni devono essere di tipo SQL_CHAR o SQL_VARCHAR. I tipi di dati SQL_LONG_VARCHAR non sono supportati nelle funzioni per i valori stringa. Il *conteggio* parametro deve essere minore o uguale a 8.000 perché i tipi di dati SQL_CHAR e SQL_VARCHAR sono limitati a una lunghezza massima di 8.000 caratteri.|  
|Valori letterali ora|I valori letterali, di ora quando archiviati in una colonna SQL_TIMESTAMP ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati di **datetime** o **smalldatetime**), hanno un valore di 1 gennaio 1900.|  
|**timestamp**|Solo un valore NULL è possibile inserire manualmente in un **timestamp** colonna. Tuttavia, poiché **timestamp**colonne vengono aggiornate automaticamente dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un valore NULL viene sovrascritto.|  
|**tinyint**|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tinyint** tipo di dati è senza segno. Oggetto **tinyint** colonna è associata a una variabile di tipo di dati SQL_C_UTINYINT per impostazione predefinita.|  
|Tipi di dati alias|Quando si è connessi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, il driver ODBC aggiunge NULL a una definizione di colonna che non dichiara in modo esplicito l'ammissione di valori null di una colonna. Per questo motivo, il supporto di valori Null che viene archiviato nella definizione di un tipo di dati alias viene ignorato.<br /><br /> Quando si è connessi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4.2*x*, tipo di colonne con tipo di dati alias con dati di base di **char** o **binario** e per cui non è null dichiarato come tipo di dati creati **varchar** o **varbinary**. [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md), e [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) restituiscono SQL_VARCHAR o SQL_VARBINARY come dati di tipo per queste colonne. Ai dati recuperati da queste colonne non viene applicato il riempimento.<br /><br /> Nota: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 e versioni precedenti.|  
|Tipi di dati LONG|*data-at-execution* parametri non sono consentiti per i tipi di dati SQL_LONGVARCHAR e SQL_LONGVARBINARY.|  
|Tipi per valori di grandi dimensioni|Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client esporrà **varchar (max)**, **varbinary (max)**, e **nvarchar (max)** tipi come SQL_VARCHAR, SQL_VARBINARY e SQL _ WVARCHAR (rispettivamente) nei API che accettano o restituiscono tipi di dati ODBC SQL.|  
|Tipo definito dall'utente (UDT)|Le colonne con tipo definito dall'utente vengono mappate come SQL_SS_UDT. Se una colonna con tipo definito dall'utente viene mappata in modo esplicito a un altro tipo nell'istruzione SQL mediante i metodi ToString() o ToXMLString() del tipo definito dall'utente oppure mediante le funzioni CAST/CONVERT, il tipo di colonna nel set di risultati rifletterà il tipo effettivo nel quale è stata convertita la colonna.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client può essere associato solo a una colonna di tipo definito dall'utente in formato binario. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta solamente la conversione tra i tipi di dati SQL_SS_UDT e SQL_C_BINARY.|  
|XML|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verrà automaticamente convertito XML in testo Unicode. Il tipo XML viene mappato come SQL_SS_XML.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elaborazione dei risultati &#40; ODBC &#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
