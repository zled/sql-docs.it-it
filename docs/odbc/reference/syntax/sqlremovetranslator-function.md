---
title: Funzione SQLRemoveTranslator | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLRemoveTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveTranslator
helpviewer_keywords:
- SQLRemoveTranslator function [ODBC]
ms.assetid: c6feda49-0359-4224-8de9-77125cf2397b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9b076c209964110d2253681d97252ece25610ff
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlremovetranslator-function"></a>SQLRemoveTranslator (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLRemoveTranslator** rimuove una funzione di conversione di informazioni dalla sezione Odbcinst.ini delle informazioni di sistema e decrementa conteggio di utilizzo della funzione di conversione componente di 1.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLRemoveTranslator(  
     LPCSTR    lpszTranslator,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszTranslator*  
 [Input] Il nome di funzione di conversione registrato nella chiave Odbcinst.ini delle informazioni di sistema.  
  
 *lpdwUsageCount*  
 [Output] Il conteggio di utilizzo della funzione di conversione dopo la chiamata a questa funzione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore. Se non esiste alcuna voce nelle informazioni di sistema quando questa funzione viene chiamata, la funzione restituisce FALSE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLRemoveTranslator** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Componente non trovato nel Registro di sistema|Il programma di installazione non è riuscito a rimuovere le informazioni di conversione perché non esiste nel Registro di sistema o non è stata trovata nel Registro di sistema.|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o funzione di conversione non valido|Il *lpszTranslator* argomento non valido.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossibile incrementare o decrementare il conteggio di utilizzo del componente|Il programma di installazione non è stato possibile diminuire il conteggio di utilizzo del driver.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLRemoveTranslator** integra il [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md) funzione e gli aggiornamenti di utilizzo di componenti conteggio nelle informazioni di sistema. Questa funzione deve essere chiamata solo da un'applicazione di installazione.  
  
 **SQLRemoveTranslator** ridurrà il conteggio di utilizzo del componente di 1. Se il conteggio di utilizzo del componente è pari a 0, verrà rimossa la voce di funzione di conversione nelle informazioni di sistema. La voce di funzione di conversione è nel seguente percorso nelle informazioni di sistema, sotto il nome della funzione di conversione:  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
 **SQLRemoveTranslator** non vengono effettivamente rimossi tutti i file. Il programma chiamante è responsabile per l'eliminazione di file e mantenendo il conteggio di utilizzo di file. Solo dopo che è stato raggiunto il conteggio di utilizzo del componente sia il conteggio di utilizzo file zero è un file eliminato fisicamente. È possibile eliminare alcuni file in un componente e altri utenti non eliminato, a seconda se i file vengono utilizzati da altre applicazioni che hanno incrementa il conteggio di utilizzo di file.  
  
 **SQLRemoveTranslator** è nota anche come parte di un processo di aggiornamento. Se un'applicazione rileva che deve eseguire un aggiornamento e il driver è installato in precedenza, il driver debba essere rimossi e reinstallato. **SQLRemoveTranslator** deve innanzitutto essere chiamato per diminuire il conteggio di utilizzo del componente, quindi **SQLInstallTranslatorEx** deve essere chiamato per incrementare il conteggio di utilizzo del componente. Il programma di installazione dell'applicazione necessario fisicamente sostituire i vecchi file con i nuovi file. Il conteggio di utilizzo del file rimarrà invariato e altre applicazioni che utilizzano i file della versione precedenti utilizzeranno la versione più recente.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|L'installazione di una funzione di conversione|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|
