---
title: SQLExtendedFetch (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b28af112-fb47-4143-b11e-3b743b2ae1b8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 25a9e0b16551ca27a6818fcfd890e56aeabfb44b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 2  
  
 Simile a [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) ma restituisce più righe utilizzando una matrice per ogni colonna. Il set di risultati forward-scorrevole e può essere effettuato con le versioni precedenti scorrevole se il cursore è definito come non forward-only, statici.  
  
 Per impostazione predefinita, il Driver ODBC di Visual FoxPro non restituisce righe contrassegnate come eliminate in una tabella FoxPro. Le righe contrassegnate per l'eliminazione ma non ancora rimossi da una tabella non sono inclusi nel cursore del set di risultati. È possibile modificare questo comportamento utilizzando la [impostare eliminato](../../odbc/microsoft/set-deleted-command.md) comando.  
  
 Per ulteriori informazioni, vedere [SQLExtendedFetch](../../odbc/reference/syntax/sqlextendedfetch-function.md) nel *riferimento per programmatori ODBC*.

