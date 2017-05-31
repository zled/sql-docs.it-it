---
title: Cerca server (Server di rete) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0dfaef0364cf72e994b0fe5de778adc8a18bd715
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="browse-for-servers-network-servers"></a>Cerca server (Server di rete)
Se si esegue la connessione a un componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] senza conoscere il nome esatto dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], nella casella **Nome server** fare clic su **Cerca** per aprire la finestra di dialogo **Cerca server**.  
  
Questa finestra di dialogo verrà popolata automaticamente dal servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser in esecuzione nei computer server. È possibile che il nome di un'istanza non compaia nell'elenco per diverse ragioni:  
  
-   Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser potrebbe non essere in esecuzione nel computer sul quale è eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   La porta UDP 1434 potrebbe essere bloccata da un firewall.  
  
-   Il flag **HideInstance** potrebbe non essere impostato.  
  
Per connettersi a un'istanza che non compare nell'elenco, digitare una stringa di connessione completa per l'istanza, compreso il numero della porta TCP/IP o il nome pipe delle named pipe.  
  
## <a name="options"></a>Opzioni  
**Selezionare l'istanza di SQL Server in rete con cui stabilire la connessione**  
Indicare il server a cui si desidera connettersi facendo clic sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] visualizzata nell'albero. Per visualizzare o nascondere parti della visualizzazione albero, fare clic sui nodi contrassegnati con un segno **+** o **–** .  
  

