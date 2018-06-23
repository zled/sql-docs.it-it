---
title: L'aggiornamento dei dati nei set di righe | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a76d76df980297fd0e7b38cc0d7ec65e310c9e46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157460"
---
# <a name="updating-data-in-rowsets"></a>Aggiornamento dei dati dei set di righe
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli aggiornamenti di provider OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati quando un consumer aggiorna un set di righe modificabile che contiene i dati. Viene creato un set di righe modificabile quando il consumer richiede il supporto per uno i **IRowsetChange** oppure **IRowsetUpdate** interfaccia.  
  
 Tutti i [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di righe modificabili del provider OLE DB Native Client utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursori per supportare il set di righe. La proprietà del set di righe DBPROP_LOCKMODE modifica il comportamento di controllo della concorrenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nei cursori e determina il comportamento di recupero delle righe del set di righe e di generazione degli errori di integrità dei dati nei set di righe aggiornabili.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta la sincronizzazione di riga prima o dopo un aggiornamento.  
  
> [!NOTE]  
>  IRowChange::SetColumns è disponibile per l'impostazione dei valori di una o più colonne denominate di un oggetto riga.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Aggiornamento dei dati nei cursori SQL Server](updating-data-in-sql-server-cursors.md)  
  
-   [Risincronizzazione delle righe](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](rowsets.md)  
  
  