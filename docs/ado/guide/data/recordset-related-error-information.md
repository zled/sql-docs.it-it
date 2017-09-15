---
title: Informazioni sugli errori Recordset | Documenti Microsoft
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
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 279fcc0564f433234cbac730465e2af06a7eb5e7
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="recordset-related-error-information"></a>Informazioni sugli errori di recordset
Durante l'elaborazione batch, il **stato** proprietà del **Recordset** oggetto fornisce informazioni relative ai singoli record nel **Recordset**. Prima di un aggiornamento in blocco, il **stato** proprietà del **Recordset** riflette le informazioni sui record aggiunti, modificati ed eliminati. Dopo aver **UpdateBatch** è stato chiamato, il **stato** proprietà indica l'esito positivo o negativo dell'operazione. Quando si sposta da un record a altro **Recordset**, il valore della **stato** le modifiche alle proprietà per descrivere lo stato del record corrente.
