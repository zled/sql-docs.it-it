---
title: MSSQLSERVER_9790 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 30cd74ab6ac78347f571b5c5c5029123a7e34c96
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417400"
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9790|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Testo del messaggio|Impossibile eseguire il routing del messaggio in arrivo. Il database di sistema MSDB contenente le informazioni di routing è in modalità utente singolo.|  
  
## <a name="explanation"></a>Spiegazione  
 Si è verificato un errore durante il tentativo di classificare un messaggio ricevuto fuori collegamento poiché il database MSDB è in modalità utente singolo.  
  
## <a name="user-action"></a>Azione dell'utente  
 Impostare MSDB sulla modalità MULTI USER con il comando ALTER DATABASE.  
  
  
