---
title: La connessione a un Database SQL di Azure tramite SQL Server Native Client | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 627854372a28762493b3c03b0ee17a8355789e09
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068932"
---
# <a name="connecting-to-a-azure-sql-database-using-sql-server-native-client"></a>Connessione a un database SQL di Azure usando SQL Server Native Client
  Per un esempio che illustra come connettersi a un [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] mediante [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vedere [sviluppo: procedure (Database SQL di Azure)](http://msdn.microsoft.com/library/ee621787.aspx).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Problemi noti correlati alla connessione a un database SQL  
 Di seguito sono elencati i problemi noti che si verificano durante la connessione a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:  
  
-   Una connessione effettuata con `SQLBrowseConnect` può essere rifiutata se `SQLBrowseConnect` viene utilizzato in varie fasi.  Ad esempio, se il nome del driver viene inviato nella prima chiamata, il server e le credenziali (utente e password) inviati nella seconda chiamata, la connessione e l'impostazione di un linguaggio e di un nome di database hanno luogo nella terza chiamata.  Durante la terza chiamata [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client emetterà un'istruzione USE per modificare i database. Poiché l'istruzione USE non è supportata in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], viene generato l'errore seguente:  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  