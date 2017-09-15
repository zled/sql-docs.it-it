---
title: Domande frequenti (FAQ) per Linux ODBC e macOS | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aa835ce2bb9e35191d9c3056dad2f208445c361a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Domande frequenti (FAQ) per Linux ODBC e macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Di seguito sono risposte a domande riguardanti il Driver ODBC per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] su Linux e macOS.
  
## <a name="frequently-asked-questions"></a>Domande frequenti

**Come funzionano le applicazioni ODBC esistenti in Linux o Mac OS con il driver?**  
Dovrebbe essere possibile compilare ed eseguire le applicazioni ODBC la compilazione e in esecuzione in Linux o Mac OS con altri driver. 
  
**Le funzionalità di [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] questa versione del supporto driver?**

Il driver ODBC in Linux e macOS supporta tutte le funzionalità server in [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] ad eccezione del database locale. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] le funzionalità supportate, vedere [linee guida di programmazione](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Il driver supporta l'autenticazione Kerberos?**  
Sì. Se si dispone di un'impostazione dell'ambiente Kerberos esistente, deve essere in grado di connettersi ai server tramite il `Trusted_Connection=Yes` opzione della stringa di connessione o DSN. Per ulteriori informazioni, vedere [Using Integrated Authentication](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Quale codifica Unicode deve essere usata un'applicazione?**  
UTF-8 per i dati SQL_CHAR e UTF-16 per i dati SQL_WCHAR.  

**Sono disponibili esempi ODBC che è possibile scaricare ed eseguire con il driver per sperimentare o valutarlo?**

Per un esempio, vedere l'articolo relativo all' [uso di esempi ODBC C++ di MSDN per il driver ODBC in Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Questo vale anche per il driver ODBC macOS. 

**È il driver ODBC in Linux o open source di macOS?**

No, il driver ODBC in Linux e macOS non sono un prodotto open source.  

## <a name="see-also"></a>Vedere anche
[L'installazione di Microsoft ODBC Driver for SQL Server in Linux e macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

