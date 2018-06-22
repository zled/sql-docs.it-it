---
title: Attività Riorganizza indice | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d14a348e0cf86c04e66afb1d008085877b63ab19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156042"
---
# <a name="reorganize-index-task"></a>Attività Riorganizza indice
  L'attività Riorganizza indice consente di riorganizzare indici nelle tabelle e nelle viste dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per altre informazioni sulla gestione degli indici, vedere [Riorganizzare e ricompilare gli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 Tramite l'attività Riorganizza indice un pacchetto può riorganizzare indici in uno o più database. Se si utilizza l'attività per riorganizzare gli indici di un singolo database, sarà possibile scegliere le viste e le tabelle di cui riorganizzare gli indici. L'attività Riorganizza indice include anche un'opzione per la compattazione dei dati oggetto di grandi dimensioni. I dati LOB sono dati con il `image`, `text`, `ntext`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, o `xml` tipo di dati. Per altre informazioni, vedere [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
 L'attività Riorganizza indice incapsula l'istruzione Transact-SQL ALTER INDEX. Se si sceglie di compattare i dati oggetto di grandi dimensioni, l'istruzione utilizzerà la clausola REORGANIZE WITH (LOB_COMPACTION = ON), in caso contrario tale clausola verrà impostata su OFF. Per altre informazioni, vedere [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
  
> [!IMPORTANT]  
>  Il tempo richiesto dall'attività per creare l'istruzione Transact-SQL da eseguire è proporzionale al numero degli indici da riorganizzare. Se l'attività è configurata per la riorganizzazione degli indici in tutte le tabelle e le viste di un database con un numero elevato di indici oppure per la riorganizzazione degli indici in più database, la generazione dell'istruzione Transact-SQL potrebbe richiedere una quantità di tempo considerevole.  
  
## <a name="configuration-of-the-reorganize-index-task"></a>Configurazione dell'attività Riorganizza indice  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della **casella degli strumenti** di Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Per informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)], fare clic sull'argomento seguente:  
  
-   [Attività Riorganizza indice &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Per altre informazioni su come impostare queste proprietà nella finestra di Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , vedere [Impostazione delle proprietà di un'attività o di un contenitore](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Integration Services](integration-services-tasks.md)   
 [Flusso di controllo](control-flow.md)  
  
  
