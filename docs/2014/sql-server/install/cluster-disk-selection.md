---
title: Selezione dischi cluster | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ce08658fe769a356e4cd24e29ed094692892e48f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067323"
---
# <a name="cluster-disk-selection"></a>Selezione dischi cluster
  Usare la pagina **Selezione dischi cluster** dell'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per selezionare la risorsa disco del cluster condiviso per il cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il disco del cluster è l'unità in cui verranno memorizzati i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Un disco cluster condiviso non è un requisito per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] le installazioni di cluster. Un file server SMB è un archivio supportato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] failover le installazioni di cluster e può essere specificato tramite il **motore di Database-directory dati** pagina prima del completamento dell'installazione.  
  
> [!WARNING]  
>  Se si è scelto di installare Analysis Services, è necessario specificare un disco del cluster condiviso.  
>   
>  Se si intende abilitare FILESTREAM in questa istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario specificare un disco del cluster condiviso.  
  
## <a name="options"></a>Opzioni  
 **Dischi condivisi**  
 Selezionare un singolo disco dall'elenco. Il disco del cluster è l'unità in cui verranno memorizzati i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 È possibile specificare un solo disco. Se si seleziona il gruppo contenente la risorsa quorum del cluster, verrà visualizzato un messaggio di avviso. È consigliabile non installare la risorsa quorum del cluster.  
  
 **Dischi condivisi disponibili**  
 Visualizza un elenco dei dischi disponibili, una descrizione di ogni risorsa disco e l'indicazione se ciascun disco è qualificato come disco fisso.  
  
  