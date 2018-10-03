---
title: MSSQLSERVER_17204 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d8bfda451cda9b27670abc180ded16ceca7d7cab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680009"
---
# <a name="mssqlserver17204"></a>MSSQLSERVER_17204
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17204|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBLKIO_DEVOPENFAILED|  
|Testo del messaggio|%ls: Impossibile aprire il file %ls per il numero di file %d.  Errore del sistema operativo: %ls.|  
  
## <a name="explanation"></a>Spiegazione  
SQL Server non è stato in grado di aprire il file specificato a causa dell'errore indicato.  
  
## <a name="user-action"></a>Azione dell'utente  
Diagnosticare e correggere l'errore del sistema operativo, quindi ripetere l'operazione.  
  
