---
title: MSSQLSERVER_11001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "12001"
helpviewer_keywords:
- 11001 (Database Engine error)
ms.assetid: 53d4d63a-61e3-441f-bfe9-9d44f7a05fd4
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 28b1886bdea4063aff6b78dba8e707f75e77abf6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171018"
---
# <a name="mssqlserver11001"></a>MSSQLSERVER_11001
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|11001|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Si è verificato un errore durante il tentativo di stabilire una connessione al server.  Quando ci si connette a SQL Server, è possibile che l'errore sia determinato dal fatto che le impostazioni predefinite di SQL Server non consentono le connessioni remote. (provider: provider TCP, errore: 0 - Host sconosciuto.) (provider di dati SqlClient .Net)|  
  
## <a name="explanation"></a>Spiegazione  
 Non è possibile stabilire la connessione tra il client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il server. L'errore potrebbe verificarsi poiché il client non è in grado di risolvere il nome del server oppure il nome del server non è corretto.  
  
## <a name="user-action"></a>Azione dell'utente  
 Verificare di avere immesso il nome corretto del server sul client e che dal client sia possibile risolvere il nome del server. Per verificare la risoluzione dei nomi TCP/IP, con il sistema operativo Windows è possibile usare il comando **ping**.  
  
## <a name="see-also"></a>Vedere anche  
 [Protocolli e librerie di rete](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Configurazione di rete dei client](../../database-engine/configure-windows/client-network-configuration.md)   
 [Configurazione di protocolli Client](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  