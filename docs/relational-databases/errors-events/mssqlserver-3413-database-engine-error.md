---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a96cecbb38234204b70967e2e99929ffba7ee5a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679819"
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3413|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|MARKDB|  
|Testo del messaggio|ID di database %d. Impossibile contrassegnare il database come sospetto. Analisi Getnext per NC su sys.databases.database_id non riuscita. Per identificare la causa e correggere gli eventuali problemi associati, fare riferimento agli errori precedenti nel log degli errori.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un errore imprevisto durante il tentativo di contrassegnare un database utente come SUSPECT nel catalogo. Lo stato SUSPECT non sarà persistente.  
  
## <a name="user-action"></a>Azione dell'utente  
Vedere gli errori precedenti e risolvere il problema.  
  
