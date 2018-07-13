---
title: Unione Editor trasformazione multipli | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
caps.latest.revision: 25
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb90ad5c378ca80b9e365dca939e3cd3c632d7dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213301"
---
# <a name="union-all-transformation-editor"></a>Editor trasformazione Unione input multipli
  Utilizzare la finestra di dialogo **Editor trasformazione Unione input multipli** per unire diversi set di righe di input in un unico set di righe di output. Includendo la trasformazione Unione input multipli in un flusso di dati è possibile unire dati tratti da più flussi di dati, creare set di dati complessi nidificando più trasformazioni Unione input multipli e unire nuovamente le righe dopo la correzione degli errori nei dati.  
  
 Per ulteriori informazioni sulla trasformazione Unione input multipli, vedere [Union All Transformation](data-flow/transformations/union-all-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Nome colonna di output**  
 Consente di digitare un alias per ogni colonna. Per impostazione predefinita, viene suggerito il nome della colonna del primo input, ovvero l'input di riferimento. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Input unione input multipli 1**  
 Consente di selezionare nell'elenco di colonne di input disponibili nel primo input, ovvero l'input di riferimento. I metadati delle colonne mappate devono corrispondere.  
  
 **Input unione input multipli n**  
 Consente di selezionare nell'elenco di colonne di input disponibili nel secondo input e negli input aggiuntivi. I metadati delle colonne mappate devono corrispondere.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Unire dati tramite l'unione input multipli-trasformazione](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)   
 [Unione-trasformazione](data-flow/transformations/merge-transformation.md)   
 [Trasformazione Merge join](data-flow/transformations/merge-join-transformation.md)  
  
  
