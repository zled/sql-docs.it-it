---
title: MSSQLSERVER_4064 | Microsoft Docs
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
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 38494142ea13c7e756c3d856c8828b5dbe03bf9b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170130"
---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|4064|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DB_UFAIL_FATAL|  
|Testo del messaggio|Impossibile aprire il database utente predefinito. Accesso non riuscito.|  
  
## <a name="explanation"></a>Spiegazione  
 L'account di accesso di SQL Server non è in grado di connettersi a causa di un problema con il relativo database predefinito. Il database non è valido oppure l'account di accesso non dispone dell'autorizzazione CONNECT per il database.  
  
## <a name="user-action"></a>Azione dell'utente  
 Utilizzare ALTER LOGIN per modificare il database predefinito dell'account di accesso. Concedere l'autorizzazione CONNECT all'account di accesso.  
  
  