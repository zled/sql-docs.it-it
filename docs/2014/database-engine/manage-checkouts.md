---
title: Gestione delle estrazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], checkouts
- checkouts [SQL Server Management Studio]
- checking out files
ms.assetid: ddd4adba-d432-4005-9cb2-bb9ee3163d8e
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f2f1d25a1344f395779d084c659fc7a4579f098c
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43813047"
---
# <a name="manage-checkouts"></a>Gestione delle estrazioni
  Dopo aver aggiunto un file al controllo del codice sorgente, prima di poterlo modificare è necessario estrarlo. Quando un file viene estratto dal controllo del codice sorgente, il provider del controllo del codice sorgente crea una copia dell'ultima versione sul disco locale e rimuove l'attributo di sola lettura del file. In alcuni casi potrebbe essere necessario modificare un file senza estrarlo. Per altre informazioni sulla modifica di un file senza estrarlo, vedere [modifica di file](../../2014/database-engine/edit-checked-in-files.md).  
  
 È possibile usare [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per estrarre i file manualmente o automaticamente. Estrarli manualmente, aprire la soluzione che contiene i file nei [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ambiente e quindi scegliendo il **Check Out** comando. Per estrarli automaticamente, è necessario configurare l'ambiente [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 In base alle opzioni impostate dall'amministratore nel provider del controllo del codice sorgente, è possibile estrarre i file anche in modalità esclusiva o condivisa. Quando si estrae un file in modalità esclusiva, solo l'utente che ha eseguito l'estrazione può modificarlo. Il file non può essere estratto da altri utenti finché non viene archiviato. Quando si estrae un file in modalità condivisa, esso può essere estratto da qualsiasi numero di altri utenti. Quando ogni utente archivia il file, il provider del controllo del codice sorgente tenta di unirlo con l'ultima versione del server del file. In caso di conflitto tra la versione che viene archiviata e l'ultima versione, il provider del controllo del codice sorgente chiede all'utente di risolverlo.  
  
 Gli argomenti disponibili in questa sezione sono descritti nella tabella seguente.  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Estrazione di file](../../2014/database-engine/check-out-files.md)|Vengono fornite istruzioni su come estrarre un file per poterlo modificare.|  
|[Annullare estrazioni](../../2014/database-engine/undo-checkouts.md)|Viene spiegato come annullare un'estrazione esistente.|  
|[Estrarre automaticamente i file al momento della modifica](../../2014/database-engine/automatically-check-out-files-upon-edit.md)|Viene spiegato come configurare il controllo del codice sorgente per estrarre un file quando si inizia a modificarlo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle archiviazioni](../../2014/database-engine/manage-checkins.md)   
 [Modificare i file archiviati](../../2014/database-engine/edit-checked-in-files.md)  
  
  
