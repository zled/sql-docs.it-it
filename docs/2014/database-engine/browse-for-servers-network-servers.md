---
title: Cerca server (Server di rete) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 27
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a43e1efc508195b837879305080c7eb6636a2141
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43811627"
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
  
  
