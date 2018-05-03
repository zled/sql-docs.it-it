---
title: Modifica di record esistenti | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], existing records
ms.assetid: 17ce1263-5897-452a-9ea5-c7f96b33df65
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6caa67868172118f7e70b1781b7fbb08ec22641
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="editing-existing-records"></a>Modifica di record esistenti
Per modificare i record esistenti, passare alla riga che si desidera modificare e inserire il **valore** proprietà dei campi che si desidera modificare. Per ulteriori informazioni sul **campo** dell'oggetto **valore** proprietà, vedere [analisi dei dati](../../../ado/guide/data/examining-data.md). A seconda del tipo di cursore, si utilizzerà **aggiornamento** o **UpdateBatch** per inviare le modifiche all'origine dati. Per ulteriori informazioni, vedere [aggiornamento e il mantenimento dati](../../../ado/guide/data/updating-and-persisting-data.md).  
  
 È in genere più efficiente utilizzare una stored procedure con un oggetto comando per eseguire gli aggiornamenti, nonché altre operazioni, perché una stored procedure non richiede la creazione di un cursore. Per ulteriori informazioni sui cursori, vedere [informazioni sui cursori e blocchi](../../../ado/guide/data/understanding-cursors-and-locks.md).
