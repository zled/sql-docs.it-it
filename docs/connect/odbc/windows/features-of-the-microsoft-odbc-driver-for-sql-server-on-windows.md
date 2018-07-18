---
title: Funzionalità di Microsoft ODBC Driver for SQL Server in Windows | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e2b7c107a40a60a1da5ed891d7a26a7c85011db
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32856336"
---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Funzionalità di Microsoft ODBC Driver for SQL Server in Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>Microsoft ODBC Driver 13.1 for SQL Server in Windows

ODBC Driver 13.1 for SQL Server contiene tutte le funzionalità della versione precedente (11) e aggiunge il supporto per l'autenticazione di Always Encrypted e Azure Active Directory utilizzato in combinazione con Microsoft SQL Server 2016.  
  
Always Encrypted consente ai client di eseguire la crittografia dei dati sensibili all'interno delle applicazioni client e non rivelare le chiavi di crittografia di SQL Server. Un driver abilitato Always Encrypted installato nel computer client fa tutto questo eseguendo automaticamente la crittografia e la decrittografia dei dati sensibili nell'applicazione client di SQL Server. Il driver esegue la crittografia dei dati in colonne riservate prima di passare i dati a SQL Server e riscrive automaticamente le query in modo da mantenere la semantica per l'applicazione. Analogamente, il driver esegue in modo trasparente la decrittografia dei dati archiviati in colonne crittografate del database contenute nei risultati della query. Per ulteriori informazioni, vedere [uso di Always Encrypted con il Driver ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md).
 
Azure Active Directory consente agli utenti, gli amministratori di database e i programmatori di applicazioni di utilizzare l'autenticazione di Azure Active Directory come un meccanismo di connessione al Database SQL di Microsoft Azure e Microsoft SQL Server 2016 usando le identità in Azure Active Directory (Azure AD ). Per ulteriori informazioni, vedere [tramite Azure Active Directory con il Driver ODBC](../../../connect/odbc/using-azure-active-directory.md), e [la connessione al Database SQL o Data Warehouse da usando Azure Active Directory l'autenticazione di SQL](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/).   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Microsoft ODBC Driver 11 for SQL Server in Windows  

ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] contiene tutte le funzionalità del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client fornito con [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]. Per altre informazioni, vedere [Programmazione in SQL Server Native Client](http://msdn.microsoft.com/library/ms130892.aspx). Il driver ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client è basato sul driver ODBC fornito con il sistema operativo Windows. Per altre informazioni, vedere [Windows Data Access Components SDK](http://msdn.microsoft.com/library/aa968814(VS.85).aspx).  
  
Questa versione di Driver ODBC for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] contiene le nuove funzionalità seguenti:  
  
### <a name="bcpexe-l-option-for-specifying-a-login-timeout"></a>opzione – l bcp.exe consente di specificare un timeout di accesso
 
L'opzione – l Specifica il numero di secondi prima che un `bcp.exe` account di accesso [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] timeout quando si tenta di connettersi a un server. Il timeout di accesso predefinito è 15 secondi. Il timeout di accesso deve essere un numero compreso tra 0 e 65534. Se il valore specificato non è numerico o non è compreso in tale intervallo, `bcp.exe` genera un messaggio di errore. Il valore 0 specifica un timeout infinito. Il timeout di accesso di minore di (circa) a 10 secondi non è affidabile.  
  
### <a name="driver-aware-connection-pooling"></a>Pool di connessioni compatibile con il driver  
Il Driver ODBC per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] supporta [Driver-Aware Connection Pooling](http://msdn.microsoft.com/library/hh405031(VS.85).aspx). Per altre informazioni, vedere [Driver-Aware Connection Pooling in the ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).  
  
### <a name="asynchronous-execution-notification-method"></a>Esecuzione asincrona (metodo di notifica)  
Il Driver ODBC per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] supporta [esecuzione asincrona (metodo di notifica)](http://msdn.microsoft.com/library/hh405038(VS.85).aspx). Per un esempio di utilizzo, vedere [esecuzione asincrona &#40;metodo di notifica&#41; esempio](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md).  
  
### <a name="connection-resiliency"></a>Resilienza della connessione
Per garantire che le applicazioni rimangano connesse a un database SQL di Microsoft Azure, il driver ODBC in Windows può ripristinare le connessioni inattive. Per altre informazioni, vedere [Connection Resiliency in the Windows ODBC Driver](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).  
  
## <a name="behavior-changes"></a>Differenze di funzionamento

In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client, il `-y0` opzione `sqlcmd.exe` ha generato l'output può essere troncato a 1 MB se la larghezza di visualizzazione è 0.
  
A partire da ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], senza alcun limite sulla quantità di dati che possono essere recuperati in un'unica colonna quando `–y0` è specificato. `sqlcmd.exe` ora trasmette colonne di dimensioni pari a 2 GB ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] massimo per tipo di dati).  
  
Un'altra differenza è che se si specifica sia `-h` e `-y0` ora genera un errore di reporting, le opzioni sono incompatibili. `-h`, che specifica il numero di righe da stampare tra le intestazioni di colonna e non è mai stato compatibile con `-y0`, anche se non venivano stampate intestazioni è stato ignorato.
  
Si noti che `-y0` potrebbe causare gravi problemi di prestazioni sia nel server di rete, a seconda delle dimensioni dei dati restituiti.

## <a name="see-also"></a>Vedere anche  
[Microsoft ODBC Driver for SQL Server in Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
