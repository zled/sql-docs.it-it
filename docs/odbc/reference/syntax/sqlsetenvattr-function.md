---
title: Funzione SQLSetEnvAttr | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f99a9d8a572653be31e74cab00de918f1f51e16
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetenvattr-function"></a>SQLSetEnvAttr Function
**Conformità**  
 Introdotta: versione ODBC 3.0 aderenza: 92 ISO  
  
 **Riepilogo**  
 **SQLSetEnvAttr** imposta gli attributi che controllano gli aspetti degli ambienti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>Argomenti  
 *EnvironmentHandle*  
 [Input] Handle di ambiente.  
  
 *Attribute*  
 [Input] Attributo da impostare, elencati in "Commenti".  
  
 *ValuePtr*  
 [Input] Puntatore al valore da associare a *attributo*. A seconda del valore di *attributo*, *ValuePtr* verranno un valore integer a 32 bit o puntare a una stringa di caratteri con terminazione null.  
  
 *StringLength*  
 [Input] Se *ValuePtr* punta a una stringa di caratteri o di un buffer binario, la lunghezza di questo argomento deve essere **ValuePtr*. Per i dati di stringa di caratteri, questo argomento deve contenere il numero di byte nella stringa.  
  
 Se *ValuePtr* è un numero intero, *StringLength* viene ignorato.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLSetEnvAttr** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valore SQLSTATE associato possono essere ottenuti chiamando **SQLGetDiagRec** con un *HandleType* di SQL _ HANDLE_ENV e *gestire* di *EnvironmentHandle*. Nella tabella seguente sono elencati i valori SQLSTATE normalmente restituiti dal **SQLSetEnvAttr** e illustra ognuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituiti da Gestione Driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, se non diversamente specificato. Se un driver non supporta un attributo di ambiente, l'errore può essere restituito solo durante la fase di connessione.  
  
|SQLSTATE|Errore|Description|  
|--------------|-----------|-----------------|  
|01000|Avviso generico.|Messaggio informativo specifici del driver. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|01S02|Valore di opzione modificato|Il driver non supportava il valore specificato *ValuePtr* e sostituito con un valore analogo. (Funzione restituisce SQL_SUCCESS_WITH_INFO).|  
|HY000|Errore generale|Si è verificato un errore per cui si è verificato alcun errore SQLSTATE specifico e per cui è stato definito alcun SQLSTATE specifici dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel * \*MessageText* buffer viene descritto l'errore e la relativa causa.|  
|HY001|Errore di allocazione della memoria|Il driver è stato in grado di allocare la memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY009|Utilizzo non valido del puntatore null|L'argomento dell'attributo identificato un attributo di ambiente che hanno richiesto un valore stringa, e *ValuePtr* argomento è un puntatore null.|  
|HY010|Errore nella sequenza (funzione)|(DM) è stato allocato un handle di connessione in *EnvironmentHandle*.<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION** non è stata impostata con **SQLSetEnvAttr** e *attributo* non è uguale a **SQL_ATTR_ODBC_VERSION**. Non è necessario impostare **SQL_ATTR_ODBC_VERSION** in modo esplicito se si utilizza **SQLAllocHandleStd**.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché gli oggetti di memoria sottostante non è accessibile, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY024|Valore dell'attributo non valido|Ha specificato *attributo* valore, in cui è stato specificato un valore non valido *ValuePtr*.|  
|HY090|Lunghezza di stringa o di buffer non valida|Il *StringLength* argomento è minore di 0 ma non è stato SQL_NTS.|  
|HY092|Identificatore di attributo/opzione non valida|(DM) il valore specificato per l'argomento *attributo* non valido per la versione di ODBC supportati dal driver.|  
|HY117|Connessione viene sospesa a causa dello stato di transazione sconosciuto. Solo disconnettersi e sono consentite funzioni di sola lettura.|(DM) per ulteriori informazioni sullo stato sospeso, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata.|Il valore specificato per l'argomento *attributo* è un attributo di ambiente ODBC valido per la versione di ODBC supportati dal driver, ma non è supportata dal driver.<br /><br /> (DM) il *attributo* argomento era SQL_ATTR_OUTPUT_NTS, e *ValuePtr* stato SQL_FALSE.|  
  
## <a name="comments"></a>Commenti  
 Un'applicazione può chiamare **SQLSetEnvAttr** solo se nessun handle di connessione è stato allocato all'ambiente. Tutti gli attributi di ambiente impostati correttamente dall'applicazione per l'ambiente mantenuta fino al **SQLFreeHandle** viene chiamato sull'ambiente. Più di un handle di ambiente può essere allocato contemporaneamente in ODBC 3*x*.  
  
 Imposta il formato delle informazioni tramite *ValuePtr* dipende specificato *attributo*. **SQLSetEnvAttr** accetterà informazioni sugli attributi in uno dei due formati: una stringa di caratteri con terminazione null o un valore integer a 32 bit. Il formato di ogni viene indicato nella descrizione dell'attributo.  
  
 Non sono presenti attributi di ambiente specifiche del driver.  
  
 Impossibile impostare gli attributi di connessione da una chiamata a **SQLSetEnvAttr**. Tentativo di eseguire questa operazione restituirà SQLSTATE HY092 (identificatore di attributo/opzione non valida).  
  
|*Attribute*|*ValuePtr* contenuto|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|Valore a 32 bit SQLUINTEGER che abilita o disabilita il pool di connessioni a livello di ambiente. Vengono utilizzati i valori seguenti:<br /><br /> SQL_CP_OFF = connessione pool è stato disattivata. Impostazione predefinita.<br /><br /> SQL_CP_ONE_PER_DRIVER = un singolo pool di connessioni è supportato per tutti i driver. Ogni connessione in un pool è associata a un driver.<br /><br /> SQL_CP_ONE_PER_HENV = un singolo pool di connessioni è supportato per ogni ambiente. Ogni connessione in un pool è associata a un ambiente.<br /><br /> SQL_CP_DRIVER_AWARE = utilizzano la funzionalità di riconoscimento del pool di connessioni del driver, se disponibile. Se il driver non supporta il riconoscimento di pool di connessioni, SQL_CP_DRIVER_AWARE viene ignorato e viene utilizzato SQL_CP_ONE_PER_HENV. Per ulteriori informazioni, vedere [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md). In un ambiente in cui alcuni driver supportano e alcuni driver non supportano la consapevolezza di pool di connessioni, SQL_CP_DRIVER_AWARE possono abilitare la funzionalità di riconoscimento di pool di connessioni su quelli che supportano il driver, ma è equivalente all'impostazione di SQL_CP_ONE_PER_HENV in i driver che non supportano la funzionalità di riconoscimento di pool di connessioni.<br /><br /> Il pool di connessioni è abilitato per la chiamata **SQLSetEnvAttr** per impostare l'attributo SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER o SQL_CP_ONE_PER_HENV. Deve essere chiamato prima che l'applicazione alloca ambiente condiviso per la connessione che il pool è necessario abilitare. L'handle di ambiente nella chiamata a **SQLSetEnvAttr** è impostato su null, che rende SQL_ATTR_CONNECTION_POOLING un attributo a livello di processo. Dopo che il pool di connessioni è abilitato, quindi l'applicazione esegue l'allocazione di un ambiente condiviso implicito chiamando **SQLAllocHandle** con il *InputHandle* argomento impostato su SQL_HANDLE_ENV.<br /><br /> Dopo che il pool di connessioni è stato abilitato ed è stato selezionato un ambiente condiviso per un'applicazione, SQL_ATTR_CONNECTION_POOLING non è possibile reimpostare l'ambiente, in quanto **SQLSetEnvAttr** viene chiamato con un ambiente null gestire quando si imposta questo attributo. Se questo attributo è impostato, mentre il pool di connessioni è già abilitato in un ambiente condiviso, l'attributo influisce solo ambienti condivisi allocati successivamente.<br /><br /> È inoltre possibile abilitare il pool di connessioni in un ambiente. Si noti quanto segue sui pool di connessioni di ambiente:<br /><br /> -Abilitazione del pool di connessioni su un handle NULL è un attributo a livello di processo. Ambienti allocati successivamente saranno un ambiente condiviso ed erediteranno il livello di processo del pool impostazione.<br />-Dopo aver allocato un ambiente, un'applicazione può ancora modificare l'impostazione del pool di connessione.<br />-Se il pool di connessioni di ambiente è abilitato e driver della connessione utilizza il pool di driver, il pool di ambiente ha preferenza.<br /><br /> SQL_ATTR_CONNECTION_POOLING viene implementato all'interno di gestione Driver. Un driver non è necessario implementare SQL_ATTR_CONNECTION_POOLING. ODBC 2.0 e 3.0 applicazioni possono impostare l'attributo di ambiente.<br /><br /> Per ulteriori informazioni, vedere [pool di connessioni ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|Valore SQLUINTEGER 32 bit che determina la modalità di scelta di una connessione da un pool di connessioni. Quando **SQLConnect** o **SQLDriverConnect** viene chiamato, gestione Driver determina quale connessione viene riutilizzata dal pool. Gestione Driver tenta di far corrispondere le opzioni di connessione in cui la chiamata e gli attributi di connessione impostati dall'applicazione per le parole chiave e gli attributi di connessione delle connessioni nel pool. Il valore di questo attributo determina il livello di precisione dei criteri di corrispondenza.<br /><br /> Per impostare il valore di questo attributo, vengono utilizzati i valori seguenti:<br /><br /> SQL_CP_STRICT_MATCH = solo le connessioni che corrispondono esattamente le opzioni di connessione nella chiamata e la connessione vengono riutilizzati attributi impostati dall'applicazione. Impostazione predefinita.<br /><br /> SQL_CP_RELAXED_MATCH = connessioni con la stringa di connessione è possono utilizzare parole chiave corrispondenti. Devono corrispondere a parole chiave, ma non tutti gli attributi di connessione devono corrispondere.<br /><br /> Per ulteriori informazioni sulla modalità di gestione Driver esegue la corrispondenza per la connessione a una connessione in pool, vedere [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md). Per ulteriori informazioni sui pool di connessioni, vedere [pool di connessioni ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_ODBC_VERSION (ODBC 3.0)|Intero a 32 bit che determina se determinate funzionalità presenta ODBC 2*x* comportamento o ODBC 3*x* comportamento. Per impostare il valore di questo attributo, vengono utilizzati i valori seguenti:<br /><br /> SQL_OV_ODBC3_80 = il Driver Manager e il comportamento di presentano il seguente ODBC 3.8 driver:<br /><br /> -Il driver restituisce e non prevede ODBC 3. *x* codici per date, time e timestamp.<br />-Il driver restituisce ODBC 3. *x* quando i codici SQLSTATE **SQLError**, **SQLGetDiagField**, o **SQLGetDiagRec** viene chiamato.<br />-La *CatalogName* argomento in una chiamata a **SQLTables** accetta un criterio di ricerca.<br />-Gestione Driver supporta l'estendibilità del tipo di dati C. Per ulteriori informazioni sulle estendibilità di tipo di dati C, vedere [tipi di dati C in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).<br /><br /> Per ulteriori informazioni, vedere [novità di ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).<br /><br /> SQL_OV_ODBC3 = la gestione di Driver e allegato driver ODBC 3 seguenti*x* comportamento:<br /><br /> -Il driver restituisce e prevede ODBC 3*x* codici per date, time e timestamp.<br />-Il driver restituisce ODBC 3*x* quando i codici SQLSTATE **SQLError**, **SQLGetDiagField**, o **SQLGetDiagRec** viene chiamato.<br />-La *CatalogName* argomento in una chiamata a **SQLTables** accetta un criterio di ricerca.<br />-Gestione Driver non supporta l'estendibilità del tipo di dati C.<br /><br /> SQL_OV_ODBC2 = la gestione di Driver e allegato driver ODBC 2 seguenti*x* comportamento. Ciò è particolarmente utile per un'API ODBC 2*x* applicazione che utilizza un'applicazione ODBC 3*x* driver.<br /><br /> -Il driver restituisce e prevede ODBC 2*x* codici per date, time e timestamp.<br />-Il driver restituisce 2 di ODBC*x* quando i codici SQLSTATE **SQLError**, **SQLGetDiagField**, o **SQLGetDiagRec** viene chiamato.<br />-La *CatalogName* argomento in una chiamata a **SQLTables** non accetta un criterio di ricerca.<br />-Gestione Driver non supporta l'estendibilità del tipo di dati C.<br /><br /> Un'applicazione deve impostare l'attributo di ambiente prima di chiamare qualsiasi funzione che dispone di un argomento SQLHENV o la chiamata restituisce SQLSTATE HY010 (funzione di errore nella sequenza). È specifico del driver esistenza di comportamento aggiuntive per questi flag di ambiente.<br /><br /> -Per ulteriori informazioni, vedere [la dichiarazione ODBC versione dell'applicazione](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) e [modifiche del comportamento](../../../odbc/reference/develop-app/behavioral-changes.md).|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|Intero a 32 bit che determina come il driver restituisce dati di tipo stringa. Se SQL_TRUE, il driver restituisce i dati di stringa con terminazione null. Se SQL_FALSE, il driver non restituisce dati di tipo stringa con terminata null.<br /><br /> Questo attributo viene impostato su SQL_TRUE. Una chiamata a **SQLSetEnvAttr** impostarlo su SQL_TRUE restituisce SQL_SUCCESS. Una chiamata a **SQLSetEnvAttr** impostare restituisce SQL_FALSE SQL_ERROR e SQLSTATE HYC00 (funzionalità facoltativa non implementata).|  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Allocazione di un handle|[Funzione SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Restituisce l'impostazione di un attributo di ambiente|[Funzione SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Novità in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)

