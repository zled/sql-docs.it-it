---
title: Notifica del completamento asincrono funzione | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b86f906385341b5b67a51cc60ef702f61dff13ea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915846"
---
# <a name="notification-of-asynchronous-function-completion"></a>Notifica del completamento asincrono (funzione)
In Windows 8 SDK ODBC aggiunto un meccanismo per notificare alle applicazioni quando viene completata un'operazione asincrona, che saranno indicati come "notifica di completamento". (Vedere [esecuzione asincrona (metodo di notifica)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) per ulteriori informazioni.) In questo argomento vengono descritti alcuni dei problemi per gli sviluppatori di driver.  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>L'interfaccia tra il gestore dei Driver e il Driver  
 Gestione Driver viene fornita una funzione di callback [SQLAsyncNotificationCallback funzione](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md). **SQLAsyncNotificationCallback** può essere chiamato solo dal driver, un'applicazione non è possibile chiamare direttamente. Il driver chiama **SQLAsyncNotificationCallback** ogni volta che i nuovi dati ricevuti dal server dopo l'ultimo SQL_STILL_EXECUTING restituzione.  
  
 Gestione Driver fornisce un meccanismo di callback in modo da un driver può inviare una notifica di gestione Driver quando alcuni avanzamento durante l'esecuzione di un'operazione asincrona dopo la funzione corrispondente restituisce SQL_STILL_EXECUTING  
  
 Gestione Driver imposta l'attributo SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK su un handle di connessione del driver con un puntatore a funzione non NULL, che è di tipo SQL_ASYNC_NOTIFICATION_CALLBACK, per il driver in modalità di notifica per qualsiasi asincrona operazioni su tale handle. Analogamente, gestione Driver imposta l'attributo SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK su un handle di istruzione driver con un puntatore a funzione non NULL, che è anche di tipo SQL_ASYNC_NOTIFICATION_CALLBACK, per il driver in modalità di notifica per tutte le operazioni asincrone in tale handle.  
  
 Se un'operazione asincrona viene eseguita su un handle di driver, le funzioni asincrone driver dovrebbero funzionare in uno stile non bloccante. Se l'operazione non completata immediatamente, la funzione di driver deve restituire SQL_STILL_EXECUTING. Questo requisito vale per la modalità di polling e modalità di notifica.  
  
 Se un handle è in modalità asincrona di notifica, il driver deve chiamare la funzione di callback di notifica, il cui indirizzo è il valore dell'attributo SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK o SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK, una volta dopo restituzione SQL_STILL_EXECUTING. In altre parole, uno SQL_STILL_EXECUTING restituzione deve essere abbinato a una singola chiamata di funzione di callback di notifica. Il driver deve utilizzare il valore corrente dell'attributo handle SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT o SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT come valore per il parametro di chiamata di funzione di richiamata *pContext*.  
  
 Il driver non deve chiamare nuovamente nel thread che chiama la funzione di driver. non vi è alcun motivo per notificare lo stato di avanzamento prima che la funzione restituisce. Il driver deve utilizzare il proprio thread al callback. Gestione Driver non usa i thread di callback del driver per l'esecuzione della logica di elaborazione completa.  
  
 Il Driver Manager chiamerà la funzione originale nuovamente dopo che il driver chiama nuovamente. Gestione Driver può utilizzare un thread diverso da un thread dell'applicazione o un thread di driver. Se il driver utilizza alcune informazioni associate al thread (ad esempio, utente o token ID di sicurezza), il driver deve salvare le informazioni necessarie nella chiamata iniziale asincrona e usare il valore salvato prima dell'operazione asincrona intero completa. In genere, solo **SQLDriverConnect**, **SQLConnect**, o **SQLBrowseConnect** necessario utilizzare tale tipo di informazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
