---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 16bfbb544023813698e33c0490e7ccb8d08754d3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418350"
---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
    
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
  
  
