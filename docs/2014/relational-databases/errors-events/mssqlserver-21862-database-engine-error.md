---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 70e85924e75469ff37e7b4c9fb7a8305ad386602
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427950"
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
    
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
  
  
