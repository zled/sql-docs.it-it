---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 963267a102c16b57860d5859a6600a34781ca2c8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413800"
---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3619|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SYS_NOLOG|  
|Testo del messaggio|Impossibile scrivere un record di checkpoint nel database con ID %d perché nel log non è disponibile spazio. Rivolgersi all'amministratore di sistema per troncare il log o per allocare più spazio per i file dei log del database.|  
  
## <a name="explanation"></a>Spiegazione  
 Lo spazio nel log delle transazioni è esaurito.  
  
## <a name="user-action"></a>Azione dell'utente  
 Troncare il log per liberare spazio oppure allocare ulteriore spazio per il log. Per ulteriori informazioni, vedere "Risoluzione dei problemi relativi a un log delle transazioni pieno (Errore 9002)" nella documentazione online di SQL Server.  
  
  
