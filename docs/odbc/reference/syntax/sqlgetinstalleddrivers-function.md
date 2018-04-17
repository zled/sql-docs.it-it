---
title: Funzione SQLGetInstalledDrivers | Documenti Microsoft
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
- SQLGetInstalledDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInstalledDrivers
helpviewer_keywords:
- SQLGetInstalledDrivers function [ODBC]
ms.assetid: a1983a2e-0edf-422e-bd1b-ec5db40a34bc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e8526c90a0fb6ec801b06ce415ff906b6b42c090
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers (funzione)
**Conformità**  
 Introdotta: versione ODBC 1.0  
  
 **Riepilogo**  
 **SQLGetInstalledDrivers** legge la sezione [ODBC Driver] le informazioni di sistema e restituisce un elenco di descrizioni dei driver installati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszBuf*  
 [Output] Elenco di descrizioni dei driver installati. Per informazioni sulla struttura dell'elenco, vedere "Commenti".  
  
 *cbBufMax*  
 [Input] Lunghezza di *lpszBuf*.  
  
 *pcbBufOut*  
 [Output] Numero totale di byte (escluso il byte di terminazione null) restituito in *lpszBuf*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbBufMax*, l'elenco delle descrizioni di driver in *lpszBuf* viene troncato a *cbBufMax* meno il carattere di terminazione null. Il *pcbBufOut* argomento può essere un puntatore null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetInstalledDrivers** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Lunghezza del buffer non valido|Il *lpszBuf* argomento è NULL o non valido, o *cbBufMax* argomento è minore o uguale a 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Componente non trovato nel Registro di sistema|Il programma di installazione non è stato in grado di trovare la sezione [driver ODBC] nel Registro di sistema.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 Ogni descrizione del driver viene terminata con un byte null e l'intero elenco è terminato con un byte null. (Ovvero, due byte null contrassegnano la fine dell'elenco.) Se il buffer allocato non è sufficientemente grande da contenere l'intero elenco, l'elenco viene troncato senza errori. Viene restituito un errore se viene passato un puntatore null come *lpszBuf*.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Restituzione di attributi e le descrizioni di driver|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
