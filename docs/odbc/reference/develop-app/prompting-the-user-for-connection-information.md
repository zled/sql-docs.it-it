---
title: Chiedere conferma all'utente informazioni di connessione | Documenti Microsoft
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
helpviewer_keywords:
- connecting to data source [ODBC], SqlConnect
- connecting to driver [ODBC], prompting user for information
- connecting to driver [ODBC], SQLConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLConnect function [ODBC], prompting user for connection information
- connecting to data source [ODBC], prompting user for information
- prompting user for connection information [ODBC]
- SQLDriverConnect function [ODBC], prompting user for connection information
ms.assetid: da98e9b9-a4ac-4a9d-bae6-e9252b1fe1e5
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 796713fb12fe2eb70a0e7630ec558a63d7cfec4d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="prompting-the-user-for-connection-information"></a>Chiedere conferma all'utente informazioni di connessione
Se l'applicazione utilizza **SQLConnect** e deve richiedere all'utente le informazioni di connessione, ad esempio un nome utente e una password, è necessario usare la stessa. Mentre in questo modo l'applicazione controllare il "aspetto", potrebbe forzare l'applicazione contenente il codice specifico del driver. Questo errore si verifica quando l'applicazione deve richiedere all'utente le informazioni di connessione specifici del driver. Ciò rappresenta una situazione possibile per le applicazioni generiche, vengono progettati per funzionare con alcuni o tutti i driver, inclusi i driver che non esistono quando l'applicazione viene scritta.  
  
 **SQLDriverConnect** può fornire all'utente le informazioni di connessione. Ad esempio, il programma personalizzato indicato in precedenza può passare la stringa di connessione seguenti per **SQLDriverConnect**:  
  
```  
DSN=XYZ Corp;  
```  
  
 Il driver può quindi visualizzare una finestra di dialogo che richiede gli ID utente e password, simile alla figura seguente.  
  
 ![Finestra di dialogo che richiede gli ID utente e password](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 Il driver può richiedere informazioni di connessione è particolarmente utile per applicazioni generiche e verticale. Queste applicazioni non devono contenere informazioni specifiche del driver, e con la richiesta di driver per le informazioni che necessarie mantiene le informazioni dall'applicazione. Come illustrato negli esempi di due precedenti. Quando l'applicazione passato solo il nome dell'origine dati per il driver, l'applicazione non contiene le informazioni specifiche del driver ed è stata pertanto non è associata a un driver specifico. Quando l'applicazione passata una stringa di connessione completa per il driver, quest'ultima è stata associata al driver che è stato possibile interpretare la stringa.  
  
 Un'applicazione generica potrebbe migliorano ulteriormente questo passaggio e non anche specificare un'origine dati. Quando **SQLDriverConnect** riceve una stringa di connessione vuota, i Driver Manager consente di visualizzare la finestra di dialogo seguente.  
  
 ![Finestra di dialogo Seleziona origine dati](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 Dopo che l'utente seleziona un'origine dati, gestione Driver costruisce una stringa di connessione che specifica che l'origine dati e lo passa al driver. Il driver può quindi richiedere all'utente le informazioni aggiuntive che necessarie.  
  
 Le condizioni in cui il driver richiede all'utente sono controllate dal *DriverCompletion* flag; sono disponibili le opzioni per Chiedi sempre conferma, prompt dei comandi se necessario, visualizzare mai la richiesta. Per una descrizione completa di questo flag, vedere il [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) descrizione della funzione.
