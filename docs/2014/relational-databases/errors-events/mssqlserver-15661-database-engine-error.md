---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7b407f652dc2ef9bcca807c359120166d5f31f89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054998"
---
# <a name="mssqlserver15661"></a>MSSQLSERVER_15661
    
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
  
  