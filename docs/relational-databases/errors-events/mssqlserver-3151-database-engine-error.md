---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 80c5c4c20c1cadbbe4114e589c8143fec9ed828e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3151|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LDDB_MASTER_LOAD_FAILED|  
|Testo del messaggio|Impossibile ripristinare il database master. SQL Server verrà chiuso. Controllare i log degli errori e ricompilare il database master. Per ulteriori informazioni sulla ricompilazione del database master, vedere la documentazione online di SQL Server.|  
  
## <a name="explanation"></a>Spiegazione  
Si tratta di un messaggio di errore generale che indica vari problemi relativi al database **master**.  
  
## <a name="user-action"></a>Azione dell'utente  
Per ulteriori informazioni esaminare i log degli errori. Per creare un database **master** utilizzabile, eseguire Setup.exe con l'opzione REBUILDDATABASE. Per ulteriori informazioni, vedere "Procedura: Installazione di SQL Server dal prompt dei comandi" nella documentazione online di SQL Server.  
  
