---
title: MSSQLSERVER_8443 | Microsoft Docs
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
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: d6e7ccc935f09bf69e848ead0a906365eeb5fe2d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167594"
---
# <a name="mssqlserver8443"></a>MSSQLSERVER_8443
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8443|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SB_DIALOG_WO_CONV_GROUP|  
|Testo del messaggio|La conversazione con ID '%.*ls' e Initiator %d fa riferimento al gruppo di conversazione mancante '%.\*ls'. Eseguire DBCC CHECKDB per analizzare e riparare il database.|  
  
## <a name="explanation"></a>Spiegazione  
 Il livello di metadati ha restituito NULL per il gruppo di conversazione. Il database è stato danneggiato in qualche modo. Una possibile causa di danneggiamento è un errore del disco.  
  
## <a name="user-action"></a>Azione dell'utente  
 Eseguire DBCC CHECKDB in modalità di correzione per riportare il database in uno stato consistente. I messaggi potrebbero essere eliminati se necessario per ripristinare la consistenza. Verificare i log degli errori di sistema per vedere se l'errore è stato causato da un altro malfunzionamento del sistema.  
  
  