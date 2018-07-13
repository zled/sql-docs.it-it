---
title: MSSQLSERVER_7901 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ea29b3ef2bc08e3451f402f17bed298b982f1bc2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407550"
---
# <a name="mssqlserver7901"></a>MSSQLSERVER_7901
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7901|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Testo del messaggio|L'istruzione di correzione non è stata elaborata. Questo livello di correzione non è supportato quando il database è in modalità di emergenza.|  
  
## <a name="explanation"></a>Spiegazione  
 Il database è in modalità di emergenza ed è stato specificato un livello di correzione diverso da REPAIR_ALLOW_DATA_LOSS. Non è possibile implementare correzioni in modalità di emergenza a meno che non venga specificata l'opzione REPAIR_ALLOW_DATA_LOSS.  
  
## <a name="user-action"></a>Azione dell'utente  
 Eseguire nuovamente il comando e specificare l'opzione REPAIR_ALLOW_DATA_LOSS.  
  
  
