---
title: La connessione a un Database SQL di Azure usando SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 797df7fad55e55b38fcfd2ed78a308b1eb7ac9d1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413065"
---
# <a name="connecting-to-a-windows-azure-sql-database-using-sql-server-native-client"></a>Connessione a un database SQL di Windows Azure utilizzando SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Per un esempio che illustra come connettersi a un [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] usando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vedere [sviluppo: procedure (Database SQL di Azure)](http://msdn.microsoft.com/library/ee621787.aspx).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Problemi noti correlati alla connessione a un database SQL  
 Di seguito sono elencati i problemi noti che si verificano durante la connessione a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:  
  
-   Una connessione effettuata con **SQLBrowseConnect** può essere rifiutata se **SQLBrowseConnect** viene usato in più fasi.  Ad esempio, se il nome del driver viene inviato nella prima chiamata, il server e le credenziali (utente e password) inviati nella seconda chiamata, la connessione e l'impostazione di un linguaggio e di un nome di database hanno luogo nella terza chiamata.  Durante la terza chiamata [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client emetterà un'istruzione USE per modificare i database. Poiché l'istruzione USE non è supportata in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], viene generato l'errore seguente:  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
