---
title: Modifica di record esistenti | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 03e720476c8056737e2735ac96c97a7caf190de4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="editing-existing-records"></a>Modifica di record esistenti
Per modificare i record esistenti, passare alla riga che si desidera modificare e inserire il **valore** proprietà dei campi che si desidera modificare. Per ulteriori informazioni sul **campo** dell'oggetto **valore** proprietà, vedere [analisi dei dati](../../../ado/guide/data/examining-data.md). A seconda del tipo di cursore, si utilizzerà **aggiornamento** o **UpdateBatch** per inviare le modifiche all'origine dati. Per ulteriori informazioni, vedere [aggiornamento e il mantenimento dati](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 È in genere più efficiente utilizzare una stored procedure con un oggetto comando per eseguire gli aggiornamenti, nonché altre operazioni, perché una stored procedure non richiede la creazione di un cursore. Per ulteriori informazioni sui cursori, vedere [informazioni sui cursori e blocchi](../../../ado/guide/data/understanding-cursors-and-locks.md).