---
title: SQLGetConnectOption (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
helpviewer_keywords: SQLGetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5703eb39-f3b2-4f3a-8676-a5625ae29a41
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 41fdb44589b0a788591b6d31ee8ff03de965cd37
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: parziale  
  
 Conformità di API ODBC: Livello 1  
  
 Restituisce l'impostazione corrente dell'opzione di connessione. Questa funzione è supportata parzialmente: il driver supporta tutti i valori per il *fOption* argomento ma non supporta alcune *vParam* valori per il *fOption* argomento SQL_TXN_ISOLATION.  
  
 Nella tabella seguente vengono descritti solo gli argomenti con il comportamento specifico per l'implementazione di Visual FoxPro il Driver ODBC di **SQLGetConnectOption**.  
  
|*fOption*|Osservazioni|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Se si sceglie SQL_AUTOCOMMIT_OFF, l'applicazione deve esplicitamente eseguire il commit o il rollback delle transazioni con [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); il Driver ODBC di Visual FoxPro non esegue automaticamente il commit un'istruzione transactable dopo il completamento. Se l'istruzione è transactable, il driver iniziare una transazione.|  
|SQL_CURRENT_QUALIFIER|Può essere un nome completo del database (file DBC) o il percorso completo alla directory contenente zero o più tabelle (file con estensione dbf).|  
|SQL_LOGINTIMEOUT|Restituisce l'errore "Driver non possono essere".|  
|SQL_CURSORS|Restituisce l'errore "Driver non possono essere".|  
|SQL_PACKET_SIZE|Restituisce l'errore "Driver non possono essere".|  
|SQL_TXN_ISOLATION|Il driver consente solo SQL_TXN_READ_COMMITTED.<br /><br /> Nell'esempio *vParam*s non sono supportati:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Per ulteriori informazioni, vedere [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md) nel *riferimento per programmatori ODBC*.
