---
title: SQLSetConnectOption (Driver di accesso) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], Access Driver
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8183c706378493b2fd854019228e429a7cfcc839
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (Driver di accesso)
> [!NOTE]  
>  In questo argomento fornisce informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Commento|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Il parametro fOption SQL_ACCESS_MODE può essere impostato SQL_MODE_READ_ONLY o SQL_MODE_READ_WRITE. Tuttavia, il driver non impedisce l'aggiornamento se SQL_ACCESS_MODE è impostata su SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Quando viene utilizzato il driver Microsoft Access, l'opzione di SQL_AUTOCOMMIT può essere impostata su SQL_AUTOCOMMIT_ON o SQL_AUTOCOMMIT_OFF, perché il driver Microsoft Access supporta le transazioni [1].|  
|SQL_CURRENT_QUALIFIER|Supportato.|  
|SQL_LOGIN_TIMEOUT|Non supportato.|  
|SQL_OPT_TRACE|Supportato.|  
|SQL_OPT_TRACEFILE|Supportato.|  
|SQL_PACKET_SIZE|Non supportato.|  
|SQL_QUIET_MODE|Non supportato.|  
|SQL_TRANSLATE_DLL|Non supportato.|  
|SQL_TRANSLATION_OPTION|Non supportato.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION è sempre SQL_TXN_READ_COMMITTED.|  
  
 [1] transazioni atomiche non sono supportate dal driver Microsoft Access. Quando esegue il commit di una transazione usando il driver Microsoft Access, un ritardo finito esiste tra il momento in cui viene eseguito il commit della transazione e l'ora in cui i valori vengono scritti su disco. Questo ritardo è determinato da un ritardo intrinseco nella gestione di Microsoft Jet. Il timeout di pagina non sarà minore di un valore minimo, anche se è impostata l'opzione PageTimeout di sotto di tale valore. Di conseguenza, vi è alcuna garanzia che è stato eseguito il commit dei dati non è stabile, poiché è possibile apportare modifiche durante il ritardo.
