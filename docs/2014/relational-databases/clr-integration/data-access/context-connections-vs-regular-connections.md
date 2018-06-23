---
title: Visual Studio regolare. Connessioni di contesto | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c2966244c8b23f58bf0762ae758ab298cc26c76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070066"
---
# <a name="regular-vs-context-connections"></a>Visual Studio regolare. Connessione di contesto:
  Se si esegue una connessione a un server remoto, utilizzare sempre connessioni normali anziché connessioni di contesto. Se è necessario connettersi allo stesso server in cui è in esecuzione la stored procedure o la funzione, utilizzare la connessione di contesto nella maggior parte dei casi. Questa connessione offre vantaggi quali l'esecuzione nello stesso spazio della transazione e la non necessità di eseguire una nuova autenticazione.  
  
 L'utilizzo della connessione di contesto, inoltre, consente in genere prestazioni migliori e un minore utilizzo delle risorse. Poiché la connessione di contesto è una connessione solo in-process, può contattare il server "direttamente" ignorando il protocollo di rete e i livelli di trasporto per inviare istruzioni Transact-SQL e ricevere risultati. Viene ignorato anche il processo di autenticazione. Nella figura seguente vengono illustrati i componenti principali del provider gestito `SqlClient`, nonché l'interazione reciproca dei diversi componenti quando si utilizza una connessione normale e quando si utilizza una connessione di contesto.  
  
 ![Percorsi del codice di un contesto e una connessione normale. ] (../../../database-engine/dev-guide/media/clrintdataaccess.gif "Percorsi di un contesto e una connessione normale del codice.")  
  
 Poiché la connessione di contesto segue un percorso di codice più corto e interessa un numero minore di componenti, è probabile che le richieste e i risultati vengano trasmessi al e dal server più rapidamente che in una connessione normale. I tempi di esecuzione delle query nel server sono uguali per le connessioni normali e di contesto.  
  
 In alcuni casi, potrebbe essere necessario aprire una connessione normale separata allo stesso server. Ad esempio, esistono alcune restrizioni nella connessione di contesto, descritto nella [restrizioni sulle normali e connessioni di contesto](context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione di contesto](context-connection.md)  
  
  