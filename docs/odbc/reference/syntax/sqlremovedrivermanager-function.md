---
title: Funzione SQLRemoveDriverManager | Documenti Microsoft
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
- SQLRemoveDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriverManager
helpviewer_keywords:
- SQLRemoveDriverManager function function [ODBC]
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5a26c787458509256a005f978d5d3a766a69bdec
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager (funzione)
**Conformità**  
 Versione introdotto: ODBC 3.0: deprecati in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 e sistemi operativi successivi.  
  
 **Riepilogo**  
 **SQLRemoveDriverManager** modifica o rimuove la voce Odbcinst.ini nelle informazioni di sistema di informazioni sui componenti principali di ODBC.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>Argomenti  
 *pdwUsageCount*  
 [Output] Il conteggio di utilizzi di gestione Driver dopo la chiamata a questa funzione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore. Se non esiste alcuna voce nelle informazioni di sistema quando questa funzione viene chiamata, la funzione restituisce FALSE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLRemoveDriverManager** restituisce FALSE, un oggetto associato * \*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i * \*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Componente non trovato nel Registro di sistema|Il programma di installazione non è riuscito a rimuovere le informazioni di gestione Driver perché non esiste nel Registro di sistema o non è stata trovata nel Registro di sistema.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossibile incrementare o decrementare il conteggio di utilizzo del componente|Il programma di installazione non è stato possibile diminuire il conteggio di utilizzo di gestione Driver.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLRemoveDriverManager** integra il **SQLInstallDriverManager** funzione e le informazioni di sistema l'utilizzo del componente di conteggio aggiornamenti. Questa funzione deve essere chiamata solo da un'applicazione di installazione.  
  
 **SQLRemoveDriverManager** ridurrà il conteggio degli utilizzi principali componenti di 1. Se il conteggio di utilizzo del componente è pari a 0, vengono rimosse le informazioni di sistema della voce. La voce di componente di base è nel seguente percorso nelle informazioni di sistema, sotto il titolo "ODBC Core":  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  Un'applicazione non rimuovere fisicamente i file di Driver Manager quando il conteggio di utilizzo del componente e il conteggio di utilizzo file raggiunge zero.  
  
 **SQLRemoveDriverManager** non vengono effettivamente rimossi tutti i file. Il programma chiamante è responsabile per l'eliminazione di file e mantenere l'utilizzo del file vengono contati. File di Gestione driver non deve tuttavia, essere rimossi quando sia il conteggio di utilizzo del componente e il conteggio di utilizzo di file hanno raggiunto lo zero, poiché questi file possono essere utilizzati da altre applicazioni che non hanno incrementato il conteggio di utilizzo di file.  
  
 **SQLRemoveDriverManager** viene chiamata come parte del processo di disinstallazione. Disinstallazione di componenti di base ODBC (che includono gestione Driver, libreria di cursori, programma di installazione, libreria di lingua, amministratore, file thunk e così via) nel suo complesso. I file seguenti non vengono rimossi quando **SQLRemoveDriverManager** viene chiamata come parte del processo di disinstallazione:  
  
|||  
|-|-|  
|ODBC32DLL|ODBCCP32. DLL|  
|ODBCCR32. DLL|ODBC16GT. DLL|  
|ODBCCU32. DLL|ODBC32GT. DLL|  
|ODBCINT. DLL|DS16GT. DLL|  
|ODBCTRAC. DLL|DS32GT. DLL|  
|MSVCRT40. DLL|ODBCAD32. FILE EXE|  
|ODBCCP32. NEL PANNELLO DI CONTROLLO||  
  
 **SQLRemoveDriverManager** è nota anche come parte di un processo di aggiornamento. Se un'applicazione rileva che deve eseguire un aggiornamento e il driver è installato in precedenza, il driver debba essere rimossi e reinstallato.  
  
 **SQLRemoveDriverManager** deve innanzitutto essere chiamato per diminuire il conteggio di utilizzo del componente. **SQLInstallDriverEx** deve quindi essere chiamato per incrementare il conteggio di utilizzo del componente. Il programma di installazione dell'applicazione è necessario sostituire i file dei componenti di base precedente con i nuovi file. Il conteggio degli utilizzi il file rimarrà invariato e altre applicazioni che utilizzano i file di componente principale della versione precedenti utilizzeranno i file della versione più recenti.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|L'installazione di una gestione Driver|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|

