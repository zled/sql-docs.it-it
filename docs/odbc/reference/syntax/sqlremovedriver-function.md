---
title: Funzione SQLRemoveDriver | Documenti Microsoft
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
ms.topic: conceptual
apiname:
- SQLRemoveDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriver
helpviewer_keywords:
- SQLRemoveDriver function [ODBC]
ms.assetid: 9a3b4f8b-982b-44b9-ade6-754ff026dc90
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efd071b6ffc5652979e78a7d183a8be461eafaeb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLRemoveDriver** viene modificato o eliminato le informazioni sul driver dalla voce Odbcinst nelle informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszDriver*  
 [Input] Il nome del driver registrati nella chiave Odbcinst.ini delle informazioni di sistema.  
  
 *fRemoveDSN*  
 [Input] I valori validi sono:  
  
 TRUE: Rimuovere associato al driver specificato nel DSN *lpszDriver*. FALSE: Non rimuovere associato al driver specificato nel DSN *lpszDriver*.  
  
 *lpdwUsageCount*  
 [Output] Il conteggio di utilizzo del driver dopo la chiamata a questa funzione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore. Se non esiste alcuna voce nelle informazioni di sistema quando questa funzione viene chiamata, la funzione restituisce FALSE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLRemoveDriver** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Componente non trovato nel Registro di sistema|Il programma di installazione non stato possibile rimuovere le informazioni sul driver perché non esiste nel Registro di sistema o non è stata trovata nel Registro di sistema.|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o funzione di conversione non valido|Il *lpszDriver* argomento non valido.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossibile incrementare o decrementare il conteggio di utilizzo del componente|Il programma di installazione non è stato possibile diminuire il conteggio di utilizzo del driver.|  
|ODBC_ERROR_REQUEST_FAILED|Richiesta non riuscita|Il *fRemoveDSN* argomento è vero; tuttavia, non è possibile rimuovere uno o più DSN. La chiamata a **SQLConfigDriver** con la richiesta ODBC_REMOVE_DRIVER non riuscito.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLRemoveDriver** si integra con il [SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md) funzione e gli aggiornamenti contare l'utilizzo di componenti nelle informazioni di sistema. Questa funzione deve essere chiamata solo da un'applicazione di installazione.  
  
 **SQLRemoveDriver** ridurrà il valore di conteggio dell'utilizzo di componente di 1. Se il conteggio di utilizzo del componente è pari a 0, si verificherà quanto segue:  
  
1.  Il **SQLConfigDriver** funzione con l'opzione ODBC_REMOVE_DRIVER verrà chiamato. Se il *fRemoveDSN* opzione è impostata su TRUE, la **ConfigDSN** chiamate di funzione **SQLRemoveDSNFromIni** per rimuovere tutte le origini dati associate con il driver specificato *lpszDriver.* Se il *fRemoveDSN* opzione è impostata su FALSE, le origini dati non verranno eliminate.  
  
2.  Le informazioni di sistema la voce driver verrà rimosso. La voce driver è nel seguente percorso informazioni sistema, sotto il nome del driver:  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **SQLRemoveDriver** non vengono effettivamente rimossi tutti i file. Il programma chiamante è responsabile per l'eliminazione di file e il conteggio di utilizzo di file di gestione. Solo dopo che è stato raggiunto il conteggio di utilizzo del componente sia il conteggio di utilizzo file zero è un file eliminato fisicamente. È possibile eliminare alcuni file in un componente e altri utenti non eliminato, a seconda se i file vengono utilizzati da altre applicazioni che hanno incrementa il conteggio di utilizzo di file.  
  
 **SQLRemoveDriver** nota anche come parte di un processo di aggiornamento. Se un'applicazione rileva che deve eseguire un aggiornamento e il driver è installato in precedenza, il driver debba essere rimossi e reinstallato. **SQLRemoveDriver** deve essere anzitutto chiamata per diminuire il conteggio di utilizzo del componente, quindi **SQLInstallDriverEx** deve essere chiamato per incrementare il conteggio di utilizzo del componente. Il programma di installazione dell'applicazione è necessario sostituire i vecchi file con i nuovi file. Il conteggio di utilizzo del file rimarrà invariato e altre applicazioni che utilizzano i file della versione precedenti utilizzeranno la versione più recente.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un driver|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md) (nel programma di installazione DLL)|  
|Aggiunta, modifica o rimozione di un driver|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installazione del driver|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|
