---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6f9dd9ab3600f51cc44b8678b050e8d61ffb2a63
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414340"
---
# <a name="mssqlserver7711"></a>MSSQLSERVER_7711
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7711|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PRT_RANGE_OVERLAP|  
|Testo del messaggio|L'opzione DATA_COMPRESSION è stata specificata più di una volta per la tabella o per l'indice o per una delle relative partizioni.|  
  
## <a name="explanation"></a>Spiegazione  
 Si è verificato un errore nell'opzione DATA_COMPRESSION di una delle istruzioni seguenti:  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
 Se la tabella o l'indice indicato è partizionato, l'opzione DATA_COMPRESSION è stata elencata più volte per almeno una delle partizioni. Se la tabella o l'indice non è partizionato, l'opzione DATA_COMPRESSION è stata indicata più volte.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per una tabella o un indice partizionato, verificare che l'opzione DATA_COMPRESSION sia specificata solo una volta per ciascuna partizione. Per una tabella o un indice non partizionato, utilizzare l'opzione DATA_COMPRESSION solo una volta nell'istruzione.  
  
  
