---
title: SQL Server Native Client Support for LocalDB | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 127569d1-a9f7-49bf-a561-c084986a8871
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 460d048e175fa28e9ebdc1f576ec8c03af183efc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="sql-server-native-client-support-for-localdb"></a>Supporto SQL Server Native Client per il database locale
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  A partire da [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], sarà disponibile una versione lightweight di SQL Server, chiamato Database locale. In questo argomento viene discussa la modalità di connessione a un database in un'istanza del database locale.  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sul database locale inclusa la modalità di installazione del database locale e di configurazione della relativa istanza, vedere:  
  
-   [Riferimento al database locale SQL Server Express](../../../relational-databases/sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2016 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 Riepilogando, il database locale consente di:  
  
-   Utilizzare **sqllocaldb.exe è** per individuare il nome dell'istanza predefinita.  
  
-   Utilizzare il **AttachDBFilename** parola chiave di stringa di connessione per specificare quale file di database il server deve essere connesso. Quando si utilizza **AttachDBFilename**, se non si specifica il nome del database con il **Database** parola chiave di stringa di connessione, verrà rimosso dal database dell'istanza del database locale quando l'applicazione chiude.  
  
-   Specificare un'istanza del database locale nella stringa di connessione:  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 Se necessario, è possibile creare un'istanza del database locale con sqllocaldb.exe. È possibile utilizzare anche sqlcmd.exe per aggiungere e modificare i database in un'istanza del database locale. Ad esempio, **sqlcmd -S (localdb) \v11.0**.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
