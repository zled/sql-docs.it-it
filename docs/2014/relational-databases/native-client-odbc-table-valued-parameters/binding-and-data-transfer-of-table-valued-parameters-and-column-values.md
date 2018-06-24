---
title: Associazione e trasferimento dati della tabella con valori di parametri e valori di colonna | Documenti Microsoft
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
helpviewer_keywords:
- table-valued parameters (ODBC), binding and data transfer
ms.assetid: 0a2ea462-d613-42b6-870f-c7fa086a6b42
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 088eaca337654ef4c8f67fc8014bee0bbcf9de85
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064670"
---
# <a name="binding-and-data-transfer-of-table-valued-parameters-and-column-values"></a>Associazione e trasferimento dati di valori di colonna e parametri con valori di tabella
  Analogamente agli altri parametri, i parametri con valori di tabella devono essere associati prima di poter essere passati al server. L'applicazione associa i parametri con valori di tabella esattamente associa gli altri parametri: utilizzando SQLBindParameter o chiamate equivalenti a SQLSetDescField o SQLSetDescRec. Il tipo di dati del server per un parametro con valori di tabella è SQL_SS_TABLE. Il tipo C può essere specificato come SQL_C_DEFAULT o SQL_C_BINARY.  
  
 In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o versioni successive, sono supportati solo parametri con valori di tabella di input. Qualsiasi tentativo di impostare SQL_DESC_PARAMETER_TYPE su un valore diverso da SQL_PARAM_INPUT restituirà, pertanto, SQL_ERROR con SQLSTATE = HY105 e il messaggio "Tipo di parametro non valido".  
  
 È possibile assegnare valori predefiniti a intere colonne dei parametri con valori di tabella utilizzando l'attributo SQL_CA_SS_COL_HAS_DEFAULT_VALUE. Valori di colonna singolo parametro con valori di tabella, tuttavia, non è possibile assegnare valori predefiniti utilizzando SQL_DEFAULT_PARAM in *StrLen_or_IndPtr* con SQLBindParameter. I parametri con valori di tabella nel suo complesso non possono essere impostati su un valore predefinito utilizzando SQL_DEFAULT_PARAM in *StrLen_or_IndPtr* con SQLBindParameter. Se queste regole non vengono seguite, SQLExecute o SQLExecDirect restituirà SQL_ERROR. Verrà generato un record di diagnostica con SQLSTATE = 07S01 e il messaggio "utilizzo non valido del parametro predefinito per il parametro \<p >", dove \<p > è il numero ordinale di TVP nell'istruzione della query.  
  
 Dopo avere associato il parametro con valori di tabella, dovrà essere associata anche ogni colonna del parametro. A tale scopo, innanzitutto l'applicazione chiama la funzione SQLSetStmtAttr per impostare SQL_SOPT_SS_PARAM_FOCUS sul numero ordinale di un parametro con valori di tabella. Quindi l'applicazione associa le colonne del parametro con valori di tabella dalle chiamate alle routine seguenti: SQLBindParameter SQLSetDescRec e SQLSetDescField. L'impostazione di SQL_SOPT_SS_PARAM_FOCUS su 0 Ripristina l'effetto tipico di SQLBindParameter SQLSetDescRec e SQLSetDescField sui regolari parametri di livello superiore.  
  
 La ricezione e l'invio di dati effettivi non riguardano il parametro con valori di tabella stesso ma ognuna delle colonne che lo costituiscono. Poiché il parametro con valori di tabella è una pseudo colonna, i parametri per SQLBindParameter vengono utilizzati per fare riferimento ad attributi diversi dagli altri tipi di dati, come indicato di seguito:  
  
|Parametro|Attributo correlato per i tipi di parametro non con valori di tabella, incluse le colonne|Attributo correlato per i parametri con valori di tabella|  
|---------------|--------------------------------------------------------------------------------|----------------------------------------------------|  
|*InputOutputType*|SQL_DESC_PARAMETER_TYPE in IPD.<br /><br /> Per le colonne dei parametri con valori di tabella, deve corrispondere all'impostazione per il parametro con valori di tabella stesso.|SQL_DESC_PARAMETER_TYPE in IPD.<br /><br /> Deve essere SQL_PARAM_INPUT.|  
|*ValueType*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in APD.|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in APD.<br /><br /> Deve essere SQL_C_DEFAULT o SQL_C_BINARY.|  
|*ParameterType*|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in IPD.|SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE in IPD.<br /><br /> Deve essere SQL_SS_TABLE.|  
|*ColumnSize*|SQL_DESC_LENGTH o SQL_DESC_PRECISION in IPD.<br /><br /> Ciò dipende dal valore di *ParameterType*.|SQL_DESC_ARRAY_SIZE<br /><br /> Può essere impostato anche utilizzando SQL_ATTR_PARAM_SET_SIZE quando lo stato attivo del parametro è impostato sul parametro con valori di tabella.<br /><br /> Per un parametro con valori di tabella, è il numero di righe nei buffer delle colonne dei parametri con valori di tabella.|  
|*DecimalDigits*|SQL_DESC_PRECISION o SQL_DESC_SCALE in IPD.|Non utilizzato. Deve essere 0.<br /><br /> Se questo parametro non verrà SQLBindParameter 0, verranno generati restituito SQL_ERROR e un record di diagnostica con SQLSTATE = HY104 e il messaggio "non valida precisione o scala".|  
|*ParameterValuePtr*|SQL_DESC_DATA_PTR in APD.|SQL_CA_SS_TYPE_NAME.<br /><br /> Questo parametro è facoltativo per le chiamate di stored procedure ed è possibile specificare NULL se non è richiesto. Deve essere specificato per le istruzioni SQL che non sono chiamate di stored procedure.<br /><br /> Questo parametro serve anche come valore univoco utilizzabile dall'applicazione per identificare il parametro con valori di tabella quando viene utilizzata l'associazione variabile di righe. Per ulteriori informazioni, vedere la sezione "Associazione variabile di righe di parametri con valori di tabella" più avanti n questo argomento.<br /><br /> Quando in una chiamata a SQLBindParameter viene specificato un nome di tipo di parametro con valori di tabella, deve essere specificata come valore Unicode, anche nelle applicazioni compilate come applicazioni ANSI. Il valore utilizzato per il parametro *StrLen_or_IndPtr* deve essere SQL_NTS o la lunghezza della stringa del nome moltiplicata per sizeof (WCHAR).|  
|*BufferLength*|SQL_DESC_OCTET_LENGTH in APD.|Lunghezza del nome del tipo di parametro con valori di tabella espressa in byte.<br /><br /> Può essere SQL_NTS, se il nome del tipo è con terminazione Null oppure 0 se il nome del tipo di parametro con valori di tabella non è richiesto.|  
|*StrLen_or_IndPtr*|SQL_DESC_OCTET_LENGTH_PTR in APD.|SQL_DESC_OCTET_LENGTH_PTR in APD.<br /><br /> Per i parametri con valori di tabella è un conteggio di righe anziché una lunghezza di dati.|  
  
 Sono supportate due modalità di trasferimento dati per i parametri con valori di tabella: associazione di righe fissa e variabile.  
  
## <a name="fixed-table-valued-parameter-row-binding"></a>Associazione fissa di righe di parametri con valori di tabella  
 Per l'associazione fissa di righe, un'applicazione alloca i buffer (o le matrici di buffer) di dimensioni sufficienti a contenere tutti i possibili valori delle colonne di input. L'applicazione effettua quanto segue:  
  
1.  Associa tutti i parametri mediante chiamate SQLBindParameter, SQLSetDescRec o SQLSetDescField.  
  
    1.  Imposta SQL_DESC_ARRAY_SIZE sul numero massimo di righe che possono essere trasferite per ogni parametro con valori di tabella. Questa operazione può essere eseguita nella chiamata di SQLBindParameter.  
  
2.  Chiama la funzione SQLSetStmtAttr per impostare SQL_SOPT_SS_PARAM_FOCUS sul numero ordinale di ogni parametro con valori di tabella.  
  
    1.  Per ogni parametro con valori di tabella, associa le colonne dei parametri con valori di tabella mediante chiamate SQLBindParameter, SQLSetDescRec o SQLSetDescField.  
  
    2.  Per ogni colonna di parametri con valori di tabella che deve avere valori predefiniti, chiama SQLSetDescField per impostare SQL_CA_SS_COL_HAS_DEFAULT_VALUE su 1.  
  
3.  Chiama la funzione SQLSetStmtAttr per impostare SQL_SOPT_SS_PARAM_FOCUS su 0. Questa operazione deve essere eseguita prima SQLExecute o SQLExecDirect viene chiamata. In caso contrario, viene restituito SQL_ERROR e vengono generati un record di dati diagnostici con SQLSTATE=HY024 e il messaggio "Valore attributo non valido, SQL_SOPT_SS_PARAM_FOCUS (deve essere zero in fase di esecuzione)."  
  
4.  Set *StrLen_or_IndPtr* o SQL_DESC_OCTET_LENGTH_PTR su SQL_DEFAULT_PARAM per un parametro con valori di tabella senza righe o il numero di righe da trasferire sulla chiamata successiva di SQLExecute o SQLExecDirect se i valori di tabella parametro contiene righe. *StrLen_or_IndPtr* o SQL_DESC_OCTET_LENGTH_PTR può essere impostato su SQL_NULL_DATA per un parametro con valori di tabella come parametri con valori di tabella non sono nullable (anche se le colonne che costituiscono parametri con valori di tabella possono essere nullable). Se è impostato su un valore non valido, SQLExecute o SQLExecDirect restituisce SQL_ERROR e viene generato un record di diagnostica con SQLSTATE = SQLSTATE=hy090 e il messaggio "lunghezza di stringa o di buffer non valida per il parametro \<p >", dove p è il numero di parametro.  
  
5.  Chiama SQLExecute o SQLExecDirect.  
  
 Valori di colonna parametro con valori di tabella possono essere passati in parti se di input *StrLen_or_IndPtr* è impostato su SQL_LEN_DATA_AT_EXEC (*lunghezza*) o SQL_DATA_AT_EXEC per la colonna. Si tratta di una procedura analoga a quella utilizzata per passare i valori in parti quando vengono utilizzate matrici di parametri. Come con tutti i parametri data-at-execution, SQLParamData non indicano quale riga della matrice il driver richiede dati; l'applicazione deve prestare attenzione di questo oggetto. L'applicazione non può prevedere l'ordine con il quale il driver richiederà i valori.  
  
## <a name="variable-table-valued-parameter-row-binding"></a>Associazione variabile di righe di parametri con valori di tabella  
 Per l'associazione variabile di righe, le righe vengono trasferite in batch in fase di esecuzione e l'applicazione passa le righe al driver su richiesta. Si tratta di una procedura simile al data-at-execution per i valori di parametri singoli. Per l'associazione variabile di righe, l'applicazione effettua quanto segue:  
  
1.  Associa i parametri e le colonne di parametri con valori di tabella come descritto nei passaggi da 1 a 3 della sezione precedente, "Associazione fissa di righe di parametri con valori di tabella".  
  
2.  Set *StrLen_or_IndPtr* o SQL_DESC_OCTET_LENGTH_PTR per i parametri con valori di tabella che devono essere passati in fase di esecuzione a SQL_DATA_AT_EXEC. Se non sono impostati valori, il parametro verrà elaborato come descritto nella sezione precedente.  
  
3.  Chiama SQLExecute o SQLExecDirect. Verrà restituito SQL_NEED_DATA se sono presenti parametri SQL_PARAM_INPUT o SQL_PARAM_INPUT_OUTPUT da gestire come parametri data-at-execution. In questo caso, l'applicazione effettua quanto segue:  
  
    -   Chiama la funzione SQLParamData. Restituisce il *ParameterValuePtr* valore per un parametro data-at-execution e un codice restituito di SQL_NEED_DATA. Quando tutti i dati del parametro è stato passato al driver, SQLParamData restituisce SQL_SUCCESS, SQL_SUCCESS_WITH_INFO o SQL_ERROR. Per i parametri data-at-execution *ParameterValuePtr*, che corrisponde al descrittore di campo SQL_DESC_DATA_PTR, può essere considerato come un token in modo da identificare un parametro per il quale è necessario specificare un valore. Tale "token" viene passato dall'applicazione al driver in fase di associazione, quindi viene passato nuovamente all'applicazione in fase di esecuzione.  
  
4.  Per inviare dati di riga di parametro con valori di tabella per i parametri con valori di tabella null, se il parametro con valori di tabella non è presenti righe, un'applicazione chiama SQLPutData con *StrLen_or_Ind* impostato su SQL_DEFAULT_PARAM.  
  
     Per i TVP non Null, un'applicazione:  
  
    -   Set *Str_Len_or_Ind* per tutte le colonne di parametri con valori di tabella sui valori appropriati e popola i buffer di dati per le colonne dei parametri con valori di tabella che non devono essere parametri data-at-execution. È possibile utilizzare la funzionalità data-at-execution per le colonne di parametri con valori di tabella seguendo procedure analoghe a quelle necessarie per passare in parti i parametri ordinari al driver.  
  
    -   Chiama SQLPutData con *Str_Len_or_Ind* impostato sul numero di righe da inviare al server. I valori esterni all'intervallo compreso tra 0 e SQL_DESC_ARRAY_SIZE o SQL_DEFAULT_PARAM sono un errore e restituiranno SQLSTATE HY090, con il messaggio "Lunghezza di stringa o di buffer non valida". 0 indica che tutte le righe sono state inviate e non sono più disponibili dati per un parametro con valori di tabella (come indicato nel secondo punto elenco). SQL_DEFAULT_PARAM può essere utilizzato solo la prima volta che il driver richiede dati per un parametro con valori di tabella (come descritto nel primo punto elenco).  
  
5.  Quando tutte le righe sono state inviate, chiama SQLPutData per il parametro con valori di tabella con una *Str_Len_or_Ind* pari a 0, quindi procede con il passaggio 3a.  
  
6.  Chiama la funzione SQLParamData nuovamente. Se sono presenti parametri data-at-execution tra le colonne di parametri con valori di tabella, questi verranno identificati dal valore *ValuePtrPtr* restituito da SQLParamData. Quando tutti i valori di colonna sono disponibili, SQLParamData restituirà nuovamente il *ParameterValuePtr* ricomincia valore per il parametro con valori di tabella e l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued Parameters &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  