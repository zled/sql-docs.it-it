---
title: Funzioni di copia bulk | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bab3c80749bc7fedb721e7f0a8d776c98a3f312d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425890"
---
# <a name="bulk-copy-functions"></a>Funzioni di copia bulk
  L'estensione API della copia bulk specifica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client consente alle applicazioni client di aggiungere o di estrarre rapidamente righe di dati in una tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Quando si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, è possibile fare riferimento alle funzioni di copia bulk (BCP) in SQLNCLI11.LIB e SQLNCLI.H.  
  
 Un'applicazione in cui vengono utilizzate le chiamate alla funzione API BCP dovrebbe essere collegata alla libreria (con estensione lib) fornita con il driver (con estensione dll) utilizzato dall'applicazione. Un'applicazione BCP non dovrebbe essere collegata a più di una libreria del driver.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [bcp_batch](bcp-batch.md)  
  
-   [bcp_bind](bcp-bind.md)  
  
-   [bcp_colfmt](bcp-colfmt.md)  
  
-   [bcp_collen](bcp-collen.md)  
  
-   [bcp_colptr](bcp-colptr.md)  
  
-   [bcp_columns](bcp-columns.md)  
  
-   [bcp_control](bcp-control.md)  
  
-   [bcp_done](bcp-done.md)  
  
-   [bcp_exec](bcp-exec.md)  
  
-   [bcp_getcolfmt](bcp-getcolfmt.md)  
  
-   [bcp_gettypename](bcp-gettypename.md)  
  
-   [bcp_init](bcp-init.md)  
  
-   [bcp_moretext](bcp-moretext.md)  
  
-   [bcp_readfmt](bcp-readfmt.md)  
  
-   [bcp_sendrow](bcp-sendrow.md)  
  
-   [bcp_setbulkmode](bcp-setbulkmode.md)  
  
-   [bcp_setcolfmt](bcp-setcolfmt.md)  
  
-   [bcp_writefmt](bcp-writefmt.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni del Driver SQL Server](../../database-engine/dev-guide/sql-server-driver-extensions.md)   
 [Esecuzione di operazioni di copia Bulk &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
