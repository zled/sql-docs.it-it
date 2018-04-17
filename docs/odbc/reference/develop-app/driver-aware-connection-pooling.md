---
title: Il pool di connessioni compatibile con il driver | Documenti Microsoft
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
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87d323d75fbbdb0166ced03156a9e7510652f344
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="driver-aware-connection-pooling"></a>Pool di connessioni compatibile con il driver
Il pool di connessioni compatibile con il driver è una nuova funzionalità di gestione Driver in Windows 8. Il pool di connessioni compatibile con il driver consente agli autori di driver di personalizzare il comportamento nel driver ODBC di pool di connessioni.  
  
> [!NOTE]  
>  Il pool di connessioni compatibile con il driver non è supportato con libreria di cursori. Un'applicazione verrà visualizzato il messaggio di errore se tenta di abilitare la libreria di cursori tramite SQLSetConnectAttr, quando il pool di connessioni compatibile con il driver è attivato.  
  
 Connessione tramite driver compatibile con il pool di indirizzi i seguenti problemi relativi al pool di connessioni di gestione Driver:  
  
 **Frammentazione del pool** The Driver Manager restituirà solo una connessione dal pool se è una corrispondenza esatta con la stringa di connessione di una nuova richiesta di connessione.  Uno dei motivi per Driver Manager per richiedere una corrispondenza esatta è che in Gestione Driver non riconosce qualsiasi parola chiave stringa di connessione specifici del driver e il relativo valore.  Tuttavia, alcuni valori di parola chiave di stringa di connessione (ad esempio il nome del database) non richiedono una corrispondenza esatta, poiché il driver è possibile modificare il database in meno rispetto al tempo necessario per aprire una nuova connessione (la differenza di ora esatta dipende dall'origine dati). E le differenze in alcuni attributi di connessione (ad esempio SQL_ATTR_CURRENT_CATALOG) possono richiedere più tempo per modificare più le differenze negli altri attributi (ad esempio SQL_ATTR_LOGIN_TIMEOUT). Questa operazione, troppo, possibile impedire gestione Driver utilizzando la connessione più basso costo e riutilizzabile dal pool. Quando si dispone di un driver creare molte nuove connessioni, possono ridurre le prestazioni dell'applicazione e può ridurre la scalabilità di origine dati. È possibile ridurre la frammentazione di pool con il pool di connessioni compatibile con il driver poiché un driver migliore possibile stimare il costo di riutilizzare una connessione nel pool per una richiesta di connessione.  
  
 **Nessuna considerazione della preferenza applicazione** alcune origini dati in modo efficiente possano aprire nuove connessioni (in rapporto alla reimpostazione alcuni attributi), pertanto, un'applicazione può essere preferibile aprire una nuova connessione anziché tentare di riutilizzare un leggermente non corrispondenti connessione dal pool e reimpostazione alcuni valori (anche se ciò può essere più lento durante la frase di inizializzazione del pool di connessione). Tuttavia, alcune applicazioni possono mantenere il carico del server più piccoli e aprire meno connessioni, anche se potrebbero essere presenti un costo maggiore correggere le mancate corrispondenze per il corretto comportamento. Senza il pool di connessioni compatibile con il driver, è possibile specificare questo tipo di preferenza in modo efficiente, perché Gestione Driver non riconosce tutti gli attributi di connessione specifici del driver. Il pool di connessioni compatibile con il driver consente al driver ottenere le preferenze dell'utente (con un attributo specifico del driver di SQLSetConnectAttr) in modo che meglio può stimare il costo di riutilizzare una connessione dal pool in base alle preferenze dell'utente.  
  
 Per ulteriori informazioni sui pool di connessioni compatibile con il driver, vedere [consapevolezza Pool di connessioni lo sviluppo di un Driver ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
## <a name="determining-driver-support"></a>Determinare il supporto di Driver  
 Il pool di connessioni compatibile con il driver è una funzionalità facoltativa che non supportano un driver. Per determinare se un driver supporta, utilizzare il SQL_DRIVER_AWARE_POOLING_SUPPORTED *InfoType* di [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>Come abilitare il pool di connessioni compatibile con il Driver  
 Un'applicazione può usare il riconoscimento di pool di connessioni patente impostando l'attributo SQL_ATTR_CONNECTION_POOLING su SQL_CP_DRIVER_AWARE con [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Se un driver non supporta il riconoscimento di pool di connessioni, il pool di connessioni di gestione Driver verrà utilizzato (stesso come se fosse stato specificato SQL_CP_ONE_PER_HENV, anziché SQL_CP_DRIVER_AWARE). Le applicazioni ODBC 2. x e 3. x è possono abilitare questa funzionalità.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un driver ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
