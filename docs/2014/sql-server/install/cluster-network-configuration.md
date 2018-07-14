---
title: La configurazione di rete del cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- cluster network selection, Setup
- cluster network selection
ms.assetid: 579482ef-a023-45b2-9176-b4a4188adf9d
caps.latest.revision: 13
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 74d2e7dd3d29777d21a21c4a9b403bc04e6dcb0a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274637"
---
# <a name="cluster-network-configuration"></a>Configurazione di rete cluster
  Utilizzare la pagina **Selezione rete cluster** per specificare le risorse di rete per l'istanza del cluster di failover.  
  
## <a name="options"></a>Opzioni  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Nome di rete cluster di failover di** : nome usato per identificare l'istanza del cluster di failover nella rete.  
  
 **Impostazioni di rete** : specificare il tipo e l'indirizzo IP per l'istanza del cluster di failover.  
  
 Durante le operazioni di aggiunta e rimozione dei noti, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene visualizzato un elenco di sola lettura degli indirizzi IP esistenti per il cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Installazione integrata:  
  
    -   Se si aggiunge un nodo che supporta un set identico di subnet di rete supportate dai nodi esistenti nel cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , non sarà possibile aggiungere ulteriori indirizzi IP. L'impostazione della dipendenza rimane invariata.  
  
    -   Se si aggiunge un nodo che supporta un subset di subnet supportate dai nodi esistenti nel cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , non sarà possibile aggiungere ulteriori risorse indirizzo IP. La dipendenza della risorsa indirizzo IP viene impostata su OR per riflettere il fatto che tutti gli indirizzi IP specificati non sono validi su tutti i nodi del cluster.  
  
    -   Se si aggiunge un nodo che supporta subnet oltre a quelle già supportate dai nodi esistenti nel cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , si avrà la possibilità di aggiungere nuovi indirizzi IP validi. Se vengono specificati nuovi indirizzi IP, la dipendenza della risorsa indirizzo IP viene impostata su OR per riflettere il fatto che tutti gli indirizzi IP specificati non sono validi su tutti i nodi del cluster.  
  
    -   Se si aggiunge un nodo che supporta subnet di rete aggiuntive, ma nessuna delle subnet supportate dai nodi esistenti nel cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , verrà richiesto di aggiungere ulteriori indirizzi IP. La dipendenza della risorsa indirizzo IP viene impostata su OR per riflettere il fatto che tutti gli indirizzi IP specificati non sono validi su tutti i nodi del cluster.  
  
-   Installazione avanzata: durante il passaggio di completamento dell'installazione specificare l'indirizzo IP per tutti i nodi e le subnet dell'istanza del cluster di failover. È possibile specificare più indirizzi IP per un cluster di failover su più subnet, tuttavia è supportato un solo indirizzo IP per subnet. Ogni nodo preparato deve essere proprietario di almeno un indirizzo IP. Se si dispone di più subnet nel cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , viene richiesto di impostare la dipendenza della risorsa indirizzo IP su OR.Rimozione nodo:  
  
    -   Se gli indirizzi IP restanti sono supportati su tutti i nodi restanti, viene richiesto di impostare la dipendenza della risorsa indirizzo IP su AND.  
  
    -   Se gli indirizzi IP restanti non sono supportati su tutti i nodi restanti, la dipendenza della risorsa indirizzo IP rimane impostata su OR.  
  
  
