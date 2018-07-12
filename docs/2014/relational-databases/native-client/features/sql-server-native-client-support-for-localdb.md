---
title: SQL Server Native Client Support for LocalDB | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c62b4a7c6db2bc7a53c616079d75110ff8c3ad95
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414050"
---
# <a name="sql-server-native-client-support-for-localdb"></a>Supporto SQL Server Native Client per il database locale
  A partire da [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], sarà disponibile una versione lightweight di SQL Server, chiamato Database locale. In questo argomento viene discussa la modalità di connessione a un database in un'istanza del database locale.  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sul database locale inclusa la modalità di installazione del database locale e di configurazione della relativa istanza, vedere:  
  
-   [Riferimento SQL Server Express LocalDB](../../sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2014 Express Local DB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 Riepilogando, il database locale consente di:  
  
-   utilizzare `sqllocaldb.exe i` per rilevare il nome dell'istanza predefinita.  
  
-   utilizzare la parola chiave della stringa di connessione `AttachDBFilename` per specificare a quale file di database il server si deve collegare. Quando si usa `AttachDBFilename`, se non si specifica il nome del database con il **Database** parola chiave di stringa di connessione, il database verrà rimosso dall'istanza di LocalDB alla chiusura dell'applicazione.  
  
-   Specificare un'istanza del database locale nella stringa di connessione:  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 Se necessario, è possibile creare un'istanza del database locale con sqllocaldb.exe. È possibile utilizzare anche sqlcmd.exe per aggiungere e modificare i database in un'istanza del database locale. Ad esempio, `sqlcmd -S (localdb)\v11.0`.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](sql-server-native-client-features.md)  
  
  
