---
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6042f6788352b1dae1e7922c9e3e3ba59eefb91f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1807|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|CANNOT_EX_LOCK|  
|Testo del messaggio|Impossibile ottenere il blocco esclusivo sul database '%.*ls'. Ripetere l'operazione in un secondo momento.|  
  
## <a name="explanation"></a>Spiegazione  
Non è possibile ottenere l'accesso esclusivo al database necessario per l'esecuzione di un'operazione.  
  
## <a name="user-action"></a>Azione dell'utente  
Disconnettere tutte le connessioni al database oppure eseguire nuovamente la query in un secondo momento.  
  
