---
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3ba40eba38d4659f100dd5aa9671e87f51b366b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758069"
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|5554|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|FS_MINIVER_OVERFLOW|  
|Testo del messaggio|È stato raggiunto il limite massimo di versioni totali per un singolo supportato dal file system.|  
  
## <a name="explanation"></a>Spiegazione  
In scenari MARS (Multiple Active Result Set) o con presenza di trigger, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa la miniversione specificata dal sistema operativo.  
  
## <a name="user-action"></a>Azione dell'utente  
Tentare di evitare aggiornamenti ripetuti ai dati nella stessa transazione.  
  
