---
title: Installazione di SQLXML non inclusa in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ee759b9c94f2bbc8a7f0c8cb1595600f29959a87
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>Installazione di SQLXML non inclusa in SQL Server
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Prima di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], SQLXML 4.0 veniva rilasciato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e faceva parte dell'installazione predefinita di tutte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versioni, ad eccezione di [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], la versione più recente di SQLXML (SQLXML 4.0 SP1) non è più inclusa in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per installare SQLXML 4.0 SP1, scaricarlo da [Install Location for SQLXML 4.0 SP1](https://www.microsoft.com/en-us/download/details.aspx?id=30403).  
  
 Se un'applicazione eseguita su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiesto SQLXML 4.0, è necessario scaricare e installare SQLXML 4.0 SP1.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Comportamento di SQLXML 4.0 SP1 con i nuovi tipi di dati quando si utilizzano il provider OLE DB di SQL Server Native Client e SQLOLEDB  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]introdotti i seguenti tipi di dati, gli sviluppatori utilizzando SQLXML potrebbero voler usare:  
  
-   **Data**  
  
-   **Time**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 Quando si utilizza SQLXML 4.0 SP1 con entrambi SQLOLEDB o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], questi tipi vengono visualizzati come stringhe a uno sviluppatore. I quattro nuovi tipi di dati verranno abilitati come tipi scalari predefiniti quando si utilizza SQLXML 4.0 SP1 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Provider Client OLE DB nativo 11.0 o versioni successive. Se non si scarica SQLXML 4.0 SP1, l'esecuzione del mapping di questi tipi ai tipi non stringa può causare il troncamento dei dati. Ad esempio, il mapping **DateTime2** a **xsd: date** dati viene troncato a causa di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime** precisione di 3,33 millisecondi.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi alla programmazione SQLXML 4.0](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
