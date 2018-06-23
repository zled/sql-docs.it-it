---
title: SQLPutData | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: abce5378b6df9bcce36bf6e1a2c9ed884f977824
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156451"
---
# <a name="sqlputdata"></a>SQLPutData
  Le restrizioni seguenti si applicano quando si utilizza SQLPutData per inviare oltre 65.535 byte di dati (per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 4.21a) o 400 KB di dati (per SQL Server versione 6.0 e versioni successive) per un SQL_LONGVARCHAR (`text`), SQL_WLONGVARCHAR (`ntext`) o SQL_LONGVARBINARY (`image`) colonna:  
  
-   Il parametro di riferimento può essere il *insert_value* in un'istruzione INSERT.  
  
-   Il parametro di riferimento può essere un' *espressione* nella clausola SET di un'istruzione UPDATE.  
  
 Annullamento di una sequenza di chiamate SQLPutData che forniscono dati in blocchi a un server che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provoca un aggiornamento parziale del valore della colonna quando si usa versione 6.5 o versione precedente. Il `text`, `ntext`, o `image` colonna di riferimento quando è stato chiamato SQLCancel è impostata su un valore di segnaposto intermedio.  
  
> [!NOTE]  
>  Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client non supporta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 e versioni precedenti.  
  
## <a name="diagnostics"></a>Diagnostica  
 È presente un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLSTATE specifico di Native Client per SQLPutData:  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|22026|Lunghezza dei dati non corrispondente.|Se la lunghezza dei dati in byte da inviare è stata specificata da un'applicazione, ad esempio con SQL_LEN_DATA_AT_EXEC (*n*) in cui *n* è maggiore di 0, il numero totale di byte fornito dall'applicazione tramite SQLPutData deve corrispondere alla lunghezza specificata.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData e parametri con valori di tabella  
 SQLPutData è utilizzato da un'applicazione quando si utilizza l'associazione variabile di righe con parametri con valori di tabella. Il *StrLen_Or_Ind* parametro indica che è pronto per il driver raccogliere dati per la riga o le righe di dati del parametro con valori di tabella, o che non più sono disponibili righe:  
  
-   Un valore maggiore di 0 indica che è disponibile il set di valori di riga successivo.  
  
-   Il valore 0 indica che non sono disponibili altre righe da inviare.  
  
-   Qualsiasi valore minore di 0 rappresenta un errore e restituisce un record di diagnostica registrato con SQLState HY090 e il messaggio "Lunghezza di stringa o di buffer non valida".  
  
 Il *DataPtr* parametro viene ignorato, ma deve essere impostata su un valore non NULL. Per altre informazioni, vedere la sezione sull'associazione di righe TVP variabili nelle [associazione e Data Transfer of Table-Valued parametri e valori di colonna](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Se *StrLen_Or_Ind* contenga un valore diverso da SQL_DEFAULT_PARAM o un numero compreso tra 0 e SQL_PARAMSET_SIZE (vale a dire, il *ColumnSize* parametro di SQLBindParameter), è corretto. A causa di questo errore, SQLPutData restituisce SQL_ERROR: SQLSTATE=HY090, "Lunghezza di stringa o di buffer non valida".  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Supporto di SQLPutData per le caratteristiche avanzate di data e ora  
 I valori dei parametri di tipi di data/ora vengono convertiti come descritto in [le conversioni da C a SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Per altre informazioni, vedere [data e ora miglioramenti &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Supporto di SQLPutData per i tipi CLR definiti dall'utente di grandi dimensioni  
 `SQLPutData` supporta i tipi CLR definiti dall'utente di grandi dimensioni. Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLPutData-funzione](http://go.microsoft.com/fwlink/?LinkId=59365)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  