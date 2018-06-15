---
title: SQLExtendedFetch (libreria di cursori) | Documenti Microsoft
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
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e7b84c5dd3c39d31b94cfb12e6b116dd44963a0e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907376"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLExtendedFetch** funzione nella libreria di cursori. Per informazioni generali su **SQLExtendedFetch**, vedere [funzione SQLExtendedFetch](../../../odbc/reference/syntax/sqlextendedfetch-function.md).  
  
 La libreria di cursori implementa **SQLExtendedFetch** chiamando ripetutamente **SQLFetch** nel driver.  
  
 La libreria di cursori supporta la chiamata **SQLExtendedFetch** con un *FetchOrientation* impostato su sql_fetch_bookmark.  
  
 Quando si utilizza la libreria di cursori, le chiamate a **SQLExtendedFetch** ReadContentAsBinHex con chiamate a **SQLFetchScroll** o **SQLFetch**.
