---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3abf49fbbf0a41ffe5e8e25995ea6900c8f2f00f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|MSSQLSERVER|  
|ID evento|21862|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum21862|  
|Testo del messaggio|Impossibile pubblicare le colonne FILESTREAM in una pubblicazione con metodo di sincronizzazione 'database snapshot' o 'database snapshot character'.|  
  
## <a name="explanation"></a>Spiegazione  
Poiché non è possibile accedere ai dati FILESTREAM tramite uno snapshot del database, l'agente snapshot non sarà in grado di leggere dati FILESTREAM se viene specificato il parametro *database snapshot* o *database_snapshot_character* per il metodo di sincronizzazione della pubblicazione.  
  
## <a name="user-action"></a>Azione dell'utente  
Impostare il metodo di sincronizzazione di pubblicazione su un valore diverso da *database snapshot* o *database_snapshot_character* oppure escludere la colonna FILESTREAM dalla pubblicazione.  
  
