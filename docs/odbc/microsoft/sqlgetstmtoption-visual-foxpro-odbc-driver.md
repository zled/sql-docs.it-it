---
title: SQLGetStmtOption (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd943c877c9fcd99c230e3d791758cbc7d0661d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903986"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Un livello  
  
 Restituisce l'impostazione corrente di un'opzione di istruzione.  
  
|*fOption*|Valori di codice restituiti|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|valore intero a 32 bit che rappresenta il segnalibro per il numero di record corrente|  
|SQL_ROW_NUMBER|intero a 32 bit che specifica la posizione della riga corrente all'interno il risultato è impostato|  
|SQL_TRANSLATE_DLL|Errore: "Driver non valido"|  
  
 Il Driver ODBC di Visual FoxPro non dispone di alcuna conversione DLL.  
  
 Per ulteriori informazioni, vedere [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) nel *riferimento per programmatori ODBC*.
