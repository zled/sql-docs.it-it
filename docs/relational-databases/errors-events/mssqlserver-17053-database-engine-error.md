---
title: MSSQLSERVER_17053 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 09a09ba19aa51777d06f9392c04617f27298693b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver17053"></a>MSSQLSERVER_17053
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17053|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|OS_ERROR|  
|Testo del messaggio|%ls: è stato rilevato l'errore del sistema operativo %ls.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un errore del sistema operativo generico.  Lo stato risultante non è chiaro.  
  
## <a name="user-action"></a>Azione dell'utente  
In genere questo errore si verifica con altri errori e deve essere utilizzato per consentire di diagnosticare gli errori specifici. Alcuni esempi potrebbero essere costituiti da letture o scritture in file di dati o di log non eseguite in modo corretto, da operazioni di lettura o scrittura nel Registro di sistema o da altri errori relativi all'API Win32 non previsti.  
  
