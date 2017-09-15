---
title: Esecuzione di procedure | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], executing
ms.assetid: a75e497a-4661-438a-a10e-f598c65f81be
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fa215150c483776f9188ed16044b59500cb257e7
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="executing-procedures"></a>Esecuzione di procedure
ODBC definisce una sequenza di escape standard per l'esecuzione delle procedure. Per la sintassi di questa sequenza e un esempio di codice che lo utilizza, vedere [chiamate di procedura](../../../odbc/reference/develop-app/procedure-calls.md).  
  
 Per eseguire una routine, un'applicazione esegue le azioni seguenti:  
  
1.  Imposta i valori dei parametri. Per ulteriori informazioni, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md), più avanti in questa sezione.  
  
2.  Chiamate **SQLExecDirect** e lo passa a una stringa contenente l'istruzione SQL che esegue la procedura. Questa istruzione è possibile utilizzare la sequenza di escape definita dalla sintassi ODBC o specifici del DBMS; le istruzioni che utilizzano la sintassi specifici del DBMS non sono interoperativi.  
  
3.  Quando **SQLExecDirect** viene chiamato, il driver:  
  
    -   Recupera i valori di parametro corrente e li converte in base alle esigenze. Per ulteriori informazioni, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md), più avanti in questa sezione.  
  
    -   Chiama la routine nell'origine dati e lo invia i valori di parametro convertito. Come il driver chiama la routine è specifico del driver. Ad esempio, è possibile modificare l'istruzione SQL per utilizzare la grammatica SQL dell'origine dati e inviare questa istruzione per l'esecuzione o è possibile chiamare la routine direttamente tramite un meccanismo di chiamata RPC (Remote Procedure) che è definito nel protocollo di flusso di dati del sistema DBMS.  
  
    -   Restituisce i valori di parametri di output o input/output o il valore restituito dalla routine, presupponendo che la procedura ha esito positivo. Questi valori potrebbero non essere disponibili solo dopo l'elaborazione di tutti gli altri risultati (conteggio delle righe e set di risultati) generati dalla procedura. Se la procedura ha esito negativo, il driver restituisce eventuali errori.
