---
title: Funzione SQLInstallTranslatorEx | Documenti Microsoft
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
apiname:
- SQLInstallTranslatorEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslatorEx
helpviewer_keywords:
- SQLInstallTranslatorEx function [ODBC]
ms.assetid: a0630602-53c1-4db0-98ce-70d160aedf8d
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0493b2405beef6e400c320528b5eb93aef990a49
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlinstalltranslatorex-function"></a>SQLInstallTranslatorEx (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLInstallTranslatorEx** aggiunge informazioni su una funzione di conversione alla sezione Odbcinst le informazioni di sistema (HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. INI\ODBC traduttori chiave Registro di sistema).  
  
 La funzionalità di **SQLInstallTranslatorEx** accessibili anche con [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLInstallTranslatorEx(  
     LPCSTR    lpszTranslator,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszTranslator*  
 [Input] Questo deve contenere un elenco di terminazione null di coppie valore-parola chiave che descrivono la funzione di conversione. Per ulteriori informazioni sulla sintassi di coppia valore-parola chiave, vedere [traduttore specifica sottochiavi](../../../odbc/reference/install/translator-specification-subkeys.md).  
  
 Il **traduttore** e **installazione** parole chiave devono essere inclusi nel *lpszTranslator* stringa. La traduzione DLL sia elencato con la **traduttore** (parola chiave) e il programma di installazione della funzione di conversione DLL sia elencato con la **installazione** (parola chiave). Ogni coppia è terminato con un byte NULL e l'intero elenco è terminata con un byte NULL. (Ovvero, due byte NULL contrassegnano la fine dell'elenco.) Il formato di *lpszTranslator* è indicato di seguito:  
  
 \0Translator=*traduttore-DLL-filename*\0[Setup=*installazione-DLL-filename*\0]\0  
  
 *lpszPathIn*  
 [Input] Percorso completo di in cui viene installato lo strumento di conversione o un puntatore null. Se *lpszPath* è un puntatore null, i traduttori verranno installati nella directory di sistema.  
  
 *lpszPathOut*  
 [Output] Il percorso della directory di destinazione in cui deve essere installato lo strumento di conversione. Se la funzione di conversione non è mai stato installato, *lpszPathOut* equivale *lpszPathIn*. Se è presente un'installazione precedente di funzione di conversione, *lpszPathOut* è il percorso dell'installazione precedente.  
  
 *cbPathOutMax*  
 [Input] Lunghezza di *lpszPathOut.*  
  
 *pcbPathOut*  
 [Output] Numero totale di byte disponibili per restituire *lpszPathOut*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbPathOutMax*, il percorso di output in *lpszPathOut* viene troncato a *pcbPathOutMax* meno il carattere di terminazione null. Il *pcbPathOut* argomento può essere un puntatore null.  
  
 *trattano*  
 [Input] Tipo di richiesta. *trattano* deve contenere uno dei valori seguenti:  
  
 ODBC_INSTALL_INQUIRY: Richiedere informazioni su dove è possibile installare uno strumento di conversione.  
  
 ODBC_INSTALL_COMPLETE: Completare la richiesta di installazione.  
  
 *lpdwUsageCount*  
 [Output] Il conteggio di utilizzo della funzione di conversione dopo la chiamata a questa funzione.  
  
 Applicazioni non devono impostare il conteggio di utilizzo. ODBC manterrà il conteggio.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLInstallTranslatorEx** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Lunghezza del buffer non valido|Il *lpszPathOut* argomento non è sufficientemente grande da contenere il percorso di output. Il buffer contiene il percorso troncato.<br /><br /> Il *cbPathOutMax* argomento è 0 e *trattano* argomento era ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Tipo di richiesta non valido|Il *trattano* argomento non è uno dei seguenti:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Coppie parola chiave-valore non valido|Il *lpszTranslator* argomento contiene un errore di sintassi.|  
|ODBC_ERROR_INVALID_PATH|Percorso di installazione non valido.|Il *lpszPathIn* argomento contiene un percorso non valido.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Sequenza di parametri non validi|Il *lpszTranslator* argomento non contiene un elenco di coppie valore-parola chiave.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossibile incrementare o decrementare conteggio dell'utilizzo di componenti del Registro di sistema|Il programma di installazione non riuscita incrementare il conteggio di utilizzo della funzione di conversione.|  
  
## <a name="comments"></a>Commenti  
 **SQLInstallTranslatorEx** fornisce un meccanismo per installare solo la funzione di conversione. Questa funzione non copiare effettivamente i file. Il programma chiamante è responsabile della copia dei file di conversione.  
  
 **SQLInstallTranslatorEx** incrementa il conteggio di utilizzi di componente per la funzione di conversione installati di 1. Se esiste già una versione della funzione di conversione, ma il conteggio di utilizzo del componente per la funzione di conversione non esiste, il nuovo valore di conteggio dell'utilizzo di componente è impostato su 2.  
  
 Il programma di installazione dell'applicazione è responsabile per copiare fisicamente il file di conversione e mantenere il conteggio di utilizzo di file. Se il file di conversione non è stato precedentemente installato, il programma di installazione dell'applicazione deve copiare i file e creare i file di conteggio di utilizzo. Se il file è stato installato in precedenza, il programma di installazione semplicemente incrementa il conteggio di utilizzo di file.  
  
 Se una versione precedente del convertitore è stata installata in precedenza dall'applicazione, la funzione di conversione deve essere disinstallato e reinstallato, in modo che il conteggio di utilizzo della funzione di conversione componente è valido. **SQLRemoveTranslator** deve essere chiamato per diminuire il conteggio di utilizzo del componente, quindi **SQLInstallTranslatorEx** deve essere chiamato per incrementare il conteggio di utilizzo del componente. Il programma di installazione dell'applicazione è necessario sostituire il vecchio file o i file con il nuovo file. Il conteggio di utilizzo del file rimarrà invariato e altre applicazioni che utilizzano il file della versione precedente utilizzeranno la versione più recente.  
  
 La lunghezza del percorso in *lpszPathOut* in **SQLInstallTranslatorEx** consente per un processo di installazione in due fasi, in modo da un'applicazione è possibile determinare quali *cbPathOutMax* deve essere chiamando **SQLInstallTranslatorEx** con un *trattano* della modalità ODBC_INSTALL_INQUIRY. Verrà restituito il numero totale di byte disponibili nel *pcbPathOut* buffer. **SQLInstallTranslatorEx** può quindi essere chiamato con un *trattano* di ODBC_INSTALL_COMPLETE e il *cbPathOutMax* argomento impostato sul valore di *pcbPathOut* buffer più il carattere di terminazione null.  
  
 Se si sceglie di non utilizzare il modello a due fasi per **SQLInstallTranslatorEx**, è necessario impostare *cbPathOutMax*, che definisce le dimensioni dello spazio di archiviazione per il percorso della directory di destinazione, per il valore MAX_PATH, come definito in STDLIB. h, per impedire il troncamento.  
  
 Quando *trattano* è ODBC_INSTALL_COMPLETE, **SQLInstallTranslatorEx** non *lpszPathOut* su NULL (o *cbPathOutMax* da 0). Se *trattano* è ODBC_INSTALL_COMPLETE, viene restituito FALSE quando il numero di byte disponibili da restituire è maggiore o uguale a *cbPathOutMax*, con il risultato che il troncamento si verifica.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Restituzione di un'opzione di conversione predefinita|[ConfigTranslator del](../../../odbc/reference/syntax/configtranslator-function.md)|  
|La selezione delle funzioni di conversione|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Rimozione di funzioni di conversione|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
