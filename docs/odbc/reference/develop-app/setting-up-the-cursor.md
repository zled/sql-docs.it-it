---
title: Impostazione del cursore | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ae6f687a09658121955f1e1d8b258ae7233657e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912546"
---
# <a name="setting-up-the-cursor"></a>Impostazione del cursore
L'applicazione può specificare il tipo di cursore prima di impostare l'esecuzione di un'istruzione che crea un risultato. Questa operazione viene eseguita con l'attributo SQL_ATTR_CURSOR_TYPE di istruzione. Se l'applicazione non specifica un tipo in modo esplicito, verrà utilizzato un cursore forward-only. Per ottenere un cursore misto, un'applicazione specifica di un cursore gestito da keyset ma dichiara una dimensione del keyset minore di dimensioni del set di risultati.  
  
 Per i cursori keyset e misti, l'applicazione può inoltre specificare la dimensione del keyset. Questa operazione viene eseguita con l'attributo di istruzione SQL_ATTR_KEYSET_SIZE. Se la dimensione del keyset è impostata su 0, ovvero l'impostazione predefinita, la dimensione del keyset è impostata per la dimensione del set di risultati e viene utilizzato un cursore gestito da keyset. È possibile modificare la dimensione del keyset dopo il cursore è stato aperto.  
  
 L'applicazione può inoltre impostare le dimensioni del set di righe. Per ulteriori informazioni, vedere [cursori a blocchi usando](../../../odbc/reference/develop-app/using-block-cursors.md), più indietro in questa sezione.
