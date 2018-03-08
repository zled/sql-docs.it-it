---
title: Impostazione delle opzioni del pool di connessioni ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection pooling [ODBC]
- ODBC data source administrator [ODBC], connection pooling options
- ODBC data source administrator [ODBC], performance monitoring
ms.assetid: 037e2f78-f204-40f4-b4ab-d9cdf562012b
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 939ac623b62b4b079e81a5c3f12df804e0b6171c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="setting-odbc-connection-pooling-options"></a>Impostazione delle opzioni del pool di connessioni ODBC
Il pool di connessioni consente a un'applicazione di utilizzare una connessione da un pool di connessioni che non è necessario essere ristabilita per ogni utilizzo. È possibile utilizzare il **pool di connessioni** scheda della finestra di **Amministrazione origine dati ODBC** la finestra di dialogo per abilitare e disabilitare il monitoraggio delle prestazioni. Fare doppio clic su un nome di driver per impostare il periodo di timeout di connessione.  
  
 A livello di driver, il pool di connessioni è abilitato per il valore del Registro di sistema CPTimeout. Questa attivazione selettivo driver consente a un amministratore di sistema abilitare il pool di connessioni per ottenere solo i driver che supportano questo valore. Si è eseguito impostando il valore predefinito di CPTimeout durante il programma di installazione del driver. Fare doppio clic su un nome di driver per impostare il periodo di timeout di connessione.  
  
 Per ulteriori informazioni sui pool di connessioni, vedere [pool di connessioni ODBC](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="performance-monitoring"></a>Monitoraggio delle prestazioni  
 Il monitoraggio delle prestazioni tiene traccia delle prestazioni della connessione mediante la registrazione di un'ampia gamma di statistiche. Tali statistiche possono essere personalizzate dallo sviluppatore per includere gli elementi seguenti:  
  
|Contatore|Definizione|  
|-------------|----------------|  
|Contatore di disco rigido di connessione ODBC al secondo|Il numero di connessioni effettive al secondo che vengono apportate al server. La prima volta che l'ambiente comporta un carico elevato, questo contatore verrà salire molto rapidamente. Dopo alcuni secondi, verrà eliminato a zero. Si tratta della situazione normale quando il pool di connessioni è attivo. Quando sono state stabilite le connessioni al server, essi verrà utilizzati e inseriti nel pool per il riutilizzo.|  
|Disco rigido ODBC disconnettere contatore al secondo|Il numero di disco rigido disconnessioni al secondo inviata al server. Si tratta di connessioni effettive al server che vengono rilasciate dal pool di connessioni. Questo valore verrà aumentati da zero quando si arresta tutti i client nel sistema e avviare le connessioni al timeout.|  
|Contatore di software di connessione ODBC al secondo|Il numero di connessioni soddisfatti dal pool al secondo, in altre parole, le connessioni dal pool di che sono stata presentate agli utenti. Questo contatore indica se il pool è in esecuzione. A seconda del carico sul server, non è insolito per questo oggetto visualizzare le connessioni software 40-60 al secondo.|  
|Contatore di disconnessione Soft ODBC al secondo|Il numero di disconnessioni al secondo emesso dalle applicazioni. Quando l'applicazione rilascia o disconnette, la connessione viene inserita nuovamente nel pool.|  
|Contatore connessione attiva corrente di ODBC|Il numero di connessioni nel pool che sono attualmente in uso.|  
|Contatore di connessione correnti ODBC|Numero corrente di connessioni disponibili disponibile nel pool. Si tratta di connessioni in tempo reale che sono disponibili per l'utilizzo.|  
|Pool di applicazioni attualmente attive|Il numero di pool attualmente attivo. Questo contatore è stato aggiunto in Windows 8, per i driver che gestiscono le connessioni nel pool di connessioni. Per ulteriori informazioni, vedere [Driver-Aware Connection Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|Pool creati|Il numero di pool attivo, inclusi i pool attivo ed è stato rimosso. Questo contatore è stato aggiunto in Windows 8, per i driver che gestiscono le connessioni nel pool di connessioni. Per ulteriori informazioni, vedere [Driver-Aware Connection Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
  
 È necessario specificare i parametri di monitoraggio personalizzati. Esempi per il monitoraggio delle prestazioni sono stati inclusi con questa versione di ODBC.
