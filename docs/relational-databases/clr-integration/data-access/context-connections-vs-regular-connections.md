---
title: Visual Studio regolare. Connessioni di contesto | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8758f1e7c680af9d546ba2b9894304388a01e46d
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35696921"
---
# <a name="context-connections-vs-regular-connections"></a>Visual Studio le connessioni di contesto. Connessioni normali
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Se si esegue una connessione a un server remoto, utilizzare sempre connessioni normali anziché connessioni di contesto. Se è necessario connettersi allo stesso server in cui è in esecuzione la stored procedure o la funzione, utilizzare la connessione di contesto nella maggior parte dei casi. Questa connessione offre vantaggi quali l'esecuzione nello stesso spazio della transazione e la non necessità di eseguire una nuova autenticazione.  
  
 L'utilizzo della connessione di contesto, inoltre, consente in genere prestazioni migliori e un minore utilizzo delle risorse. Poiché la connessione di contesto è una connessione solo in-process, può contattare il server "direttamente" ignorando il protocollo di rete e i livelli di trasporto per inviare istruzioni Transact-SQL e ricevere risultati. Viene ignorato anche il processo di autenticazione. La figura seguente illustra i componenti principali del **SqlClient** gestiti provider, nonché come i diversi componenti interagiscono tra loro quando si utilizza una connessione normale e quando si utilizza la connessione di contesto.  
  
 ![Percorsi del codice di un contesto e una connessione normale. ] (../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Percorsi di un contesto e una connessione normale del codice.")  
  
 Poiché la connessione di contesto segue un percorso di codice più corto e interessa un numero minore di componenti, è probabile che le richieste e i risultati vengano trasmessi al e dal server più rapidamente che in una connessione normale. I tempi di esecuzione delle query nel server sono uguali per le connessioni normali e di contesto.  
  
 In alcuni casi, potrebbe essere necessario aprire una connessione normale separata allo stesso server. Ad esempio, esistono alcune restrizioni nella connessione di contesto, descritto nella [restrizioni sulle normali e connessioni di contesto](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione di contesto](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
