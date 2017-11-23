---
title: 'Passaggio 1: Connettersi all''origine dati | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65c33be649b1c8007eef9e43db44897053a83a42
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="step-1-connect-to-the-data-source"></a>Passaggio 1: Connettersi all'origine dati
Il primo passaggio in qualsiasi applicazione consiste nella connessione all'origine dati. Questa fase, incluse le funzioni che richiesti, è illustrata nella figura seguente.  
  
 ![Connessione all'origine dei dati in un'applicazione ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 È il primo passaggio per la connessione all'origine dati per caricare il Driver Manager e allocare l'handle di ambiente con **SQLAllocHandle**. Per ulteriori informazioni, vedere [allocare l'Handle di ambiente](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 L'applicazione quindi registra la versione di ODBC in cui è conforme chiamando **SQLSetEnvAttr** con l'attributo di ambiente SQL_ATTR_APP_ODBC_VER. Per ulteriori informazioni, vedere [la dichiarazione ODBC versione dell'applicazione](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) e [compatibilità e conformità agli standard](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Successivamente, l'applicazione viene allocato un handle di connessione con **SQLAllocHandle** e si connette all'origine dati con **SQLConnect**, **SQLDriverConnect**, o **SQLBrowseConnect**. Per ulteriori informazioni, vedere [allocare un Handle di connessione](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) e [stabilire una connessione](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 Quindi, l'applicazione imposta gli attributi di connessione, ad esempio se manualmente il commit delle transazioni. Per ulteriori informazioni, vedere [gli attributi di connessione](../../../odbc/reference/develop-app/connection-attributes.md).
