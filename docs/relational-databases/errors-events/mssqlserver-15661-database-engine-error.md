---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aff56976620f444c707850138185165fe4a82a4e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver15661"></a>MSSQLSERVER_15661
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|15661|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum15661|  
|Testo del messaggio|Impossibile utilizzare la stored procedure sp_estimate_data_compression_savings per le tabelle temporanee.|  
  
## <a name="explanation"></a>Spiegazione  
Una tabella temporanea è stata usata come argomento per la stored procedure sp_estimate_data_compression_savings. Sebbene la compressione delle tabelle temporanee sia supportata, non è possibile usare sp_estimate_data_compression_savings per stimare il risparmio in caso di compressione.  
  
## <a name="user-action"></a>Azione dell'utente  
Rimuovere la tabella temporanea come argomento per sp_estimate_data_compression_savings.  
  
