---
title: Matrice di stato di riga | Documenti Microsoft
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
- row status array [ODBC]
- cursors [ODBC], block
- result sets [ODBC], row status array
- block cursors [ODBC]
- result sets [ODBC], block cursors
- rowset status [ODBC]
ms.assetid: 4b69f189-2722-4314-8a02-f4ffecd6dabd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2c45b2dc5ea9326b5ae3b229a17c13207edcabc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912536"
---
# <a name="row-status-array"></a>Matrice di stato di riga
Oltre ai dati, **SQLFetch** e **SQLFetchScroll** può restituire una matrice che fornisce lo stato di ogni riga nel set di righe. Questa matrice viene specificata tramite l'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR. Questa matrice viene allocata dall'applicazione e deve disporre di tutti gli elementi definiti dall'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE. I valori nella matrice vengono impostati **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, e **SQLSetPos.** I valori descrivono lo stato della riga e se lo stato è stato modificato dopo l'ultimo recupero.  
  
|Valore di matrice di stato di riga|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|La riga è stata recuperata correttamente e non è stato modificato dopo l'ultimo recupero.|  
|SQL_ROW_SUCCESS_WITH_INFO|La riga è stata recuperata correttamente e non è stato modificato dopo l'ultimo recupero. Tuttavia, è stato restituito un avviso sulla riga.|  
|SQL_ROW_ERROR|Si è verificato un errore durante il recupero della riga.|  
|SQL_ROW_UPDATED|La riga è stata recuperata correttamente ed è stata aggiornata dopo l'ultimo recupero. Se la riga viene recuperata di nuovo o aggiornata da **SQLSetPos**, lo stato viene modificato per il nuovo stato.<br /><br /> Alcuni driver non è in grado di rilevare le modifiche ai dati e pertanto non può restituire questo valore. Per determinare se un driver è possibile rilevare gli aggiornamenti alle righe refetched, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_ROW_UPDATES.|  
|SQL_ROW_DELETED|La riga è stata eliminata dopo l'ultimo recupero.|  
|SQL_ROW_ADDED|La riga inserita da **SQLBulkOperations**. Se la riga viene recuperata di nuovo o viene aggiornata da **SQLSetPos**, lo stato è SQL_ROW_SUCCESS.<br /><br /> Questo valore non è impostato dal **SQLFetch** o **SQLFetchScroll**.|  
|SQL_ROW_NOROW|Il set di righe sovrapposti la fine del set di risultati ed è stata restituita alcuna riga che corrisponde a questo elemento della matrice di stato di riga.|
