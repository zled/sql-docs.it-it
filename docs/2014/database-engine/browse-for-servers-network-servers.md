---
title: Cerca server (Server di rete) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db0e235abb91181ac2090000b9d307181f720768
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155838"
---
# <a name="browse-for-servers-network-servers"></a>Cerca server (Server di rete)
  Se si esegue la connessione a un componente di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] senza conoscere il nome esatto dell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], nella casella **Nome server** fare clic su **Cerca** per aprire la finestra di dialogo **Cerca server**.  
  
 Questa finestra di dialogo verrà popolata automaticamente dal servizio [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser in esecuzione nei computer server. È possibile che il nome di un'istanza non compaia nell'elenco per diverse ragioni:  
  
-   Il servizio [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Browser potrebbe non essere in esecuzione nel computer sul quale è eseguito [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   La porta UDP 1434 potrebbe essere bloccata da un firewall.  
  
-   Il flag **HideInstance** potrebbe non essere impostato.  
  
 Per connettersi a un'istanza che non compare nell'elenco, digitare una stringa di connessione completa per l'istanza, compreso il numero della porta TCP/IP o il nome pipe delle named pipe.  
  
## <a name="options"></a>Opzioni  
 **Selezionare l'istanza di SQL Server in rete con cui stabilire la connessione**  
 Indicare il server a cui si desidera connettersi facendo clic sull'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] visualizzata nell'albero. Per visualizzare o nascondere parti della visualizzazione albero, fare clic sui nodi contrassegnati con un segno **+** o **–** .  
  
  