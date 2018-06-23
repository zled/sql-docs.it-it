---
title: SQLGetCursorName | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6262c913a0b7f3060b0c48f9061cab90345f99ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063339"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
  Se l'applicazione non specifica un nome di cursore, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client ne genera uno al momento della generazione del cursore. L'applicazione può utilizzare **SQLGetCursorName** per recuperare il nome del cursore definito dal driver per le istruzioni UPDATE e DELETE posizionata. L'applicazione non è necessario chiamare **SQLSetCursorName** per poter sfruttare posizionato le istruzioni di manipolazione dei dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLGetCursorName](http://go.microsoft.com/fwlink/?LinkId=59349)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  