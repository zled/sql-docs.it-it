---
title: MSSQLSERVER_10061 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b77e1d920f97891d173bfdcdcb23ceb6c0acf0c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062221"
---
# <a name="mssqlserver10061"></a>MSSQLSERVER_10061
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10061|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Si è verificato un errore durante il tentativo di stabilire una connessione al server.  Quando ci si connette a SQL Server, è possibile che l'errore sia determinato dal fatto che le impostazioni predefinite di SQL Server non consentono le connessioni remote. (provider: provider TCP, errore: 0 - Impossibile stabilire la connessione. Rifiuto persistente del computer di destinazione.) (Microsoft SQL Server, Errore: 10061)|  
  
## <a name="explanation"></a>Spiegazione  
 Il server non ha risposto alla richiesta del client. Questo errore potrebbe verificarsi poiché il server non è stato avviato.  
  
## <a name="user-action"></a>Azione dell'utente  
 Verificare che il server sia stato avviato.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire il servizio Motore di database](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [Configurazione di protocolli Client](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Protocolli e librerie di rete](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Configurazione di rete dei client](../../database-engine/configure-windows/client-network-configuration.md)   
 [Configurazione di protocolli Client](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
