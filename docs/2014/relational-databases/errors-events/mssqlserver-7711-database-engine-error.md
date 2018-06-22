---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: dab7eb337e5bfc6dacbcdf5fad4ad7b9d640b41e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064046"
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
  
  