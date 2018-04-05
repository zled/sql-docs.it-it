---
title: Funzione SQLInstallDriverManager | Documenti Microsoft
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
- SQLInstallDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverManager
helpviewer_keywords:
- SQLInstallDriverManager function [ODBC]
ms.assetid: aebc439b-fffd-4d98-907a-0163f79aee8d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7d1769b4951662f99cd50709b498891540fd4b9c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlinstalldrivermanager-function"></a>SQLInstallDriverManager (funzione)
**Conformità**  
 Versione introdotto: ODBC 1.0: deprecati in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 e versioni successive  
  
 **Riepilogo**  
 **SQLInstallDriverManager** restituisce il percorso della directory di destinazione per l'installazione dei componenti principali di ODBC. Il programma chiamante deve effettivamente copiare i file di gestione Driver nella directory di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszPath*  
 [Output] Percorso della directory di destinazione dell'installazione.  
  
 *cbPathMax*  
 [Input] Lunghezza di *lpszPath*. Deve essere almeno byte MAX_PATH.  
  
 *pcbPathOut*  
 [Output] Numero totale di byte (escluso il byte di terminazione null) restituito in *lpszPath*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbPathMax*, il percorso in *lpszPath* viene troncato a *cbPathMax* meno la terminazione null carattere. Il *pcbPathOut* argomento può essere un puntatore null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLInstallDriverManager** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Lunghezza del buffer non valido|Il *lpszPath* argomento non è sufficientemente grande da contenere il percorso di output. Il buffer contiene il percorso troncato.<br /><br /> Il *cbPathMax* argomento è inferiore a MAX_PATH.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossibile incrementare o decrementare il conteggio di utilizzo del componente|Il programma di installazione non riuscita incrementare il conteggio di utilizzo ODBC core componente.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLInstallDriverManager** viene chiamata per restituire il percorso per i componenti principali di ODBC e incremento l'utilizzo del componente conteggio nelle informazioni di sistema. Se esiste già una versione di gestione Driver, ma il conteggio di utilizzo del componente per il driver non esiste, il nuovo valore di conteggio dell'utilizzo di componente è impostato su 2.  
  
 Il programma di installazione dell'applicazione è responsabile per copiare fisicamente i file dei componenti di base e mantenendo l'utilizzo del file vengono contati. Se un file di componente di base non è stato precedentemente installato, il programma di installazione dell'applicazione deve copiare il file e creare il conteggio di utilizzo di file. Se il file è stato installato in precedenza, il programma di installazione semplicemente incrementa il conteggio di utilizzo di file.  
  
 Se una versione precedente di gestione Driver è stato precedentemente installata dal programma di installazione dell'applicazione, i componenti di base devono essere disinstallati e reinstallati, in modo che il conteggio di utilizzo core componente è valido. **SQLRemoveDriverManager** deve innanzitutto essere chiamato per diminuire il conteggio di utilizzo del componente. **SQLInstallDriverManager** deve quindi essere chiamato per incrementare il conteggio di utilizzo del componente. Il programma di installazione dell'applicazione è necessario sostituire i file dei componenti di base precedente con i nuovi file. Il conteggio degli utilizzi il file rimarrà invariato e altre applicazioni che utilizzano i file di componente principale della versione precedenti utilizzeranno i file della versione più recenti.  
  
 In una nuova installazione dei componenti di base ODBC, driver e funzioni di conversione, il programma di installazione dell'applicazione deve chiamare le funzioni seguenti nella sequenza: **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLConfigDriver** (con un *trattano* di ODBC_INSTALL_DRIVER), quindi **SQLInstallTranslatorEx**. In una disinstallazione dei componenti di base, driver e funzioni di conversione, il programma di installazione dell'applicazione deve chiamare le funzioni seguenti nella sequenza: **SQLRemoveTranslator**, **SQLRemoveDriver**e quindi **SQLRemoveDriverManager**. Queste funzioni devono essere chiamate in questa sequenza. In un aggiornamento di tutti i componenti, tutte le funzioni di disinstallazione devono essere chiamate in sequenza e quindi tutte le funzioni di installazione devono essere chiamate in sequenza.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un driver|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installazione del driver|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|L'installazione di una funzione di conversione|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|Rimozione di un driver|[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|Rimozione di gestione Driver|[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|Rimozione di una funzione di conversione|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
