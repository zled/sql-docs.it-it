---
title: Utilizzo delle transazioni | Documenti Microsoft
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
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2c132ac199fb6af9e0349c463d5b30954acbf8bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166344"
---
# <a name="using-transactions"></a>Utilizzo di transazioni
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), l'elaborazione delle transazioni viene eseguita mediante la connessione all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando l'oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Il <xref:Microsoft.SqlServer.Management.Common.ServerConnection> oggetto fa riferimento il <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> proprietà del <xref:Microsoft.SqlServer.Management.Smo.Server> dell'oggetto quando viene stabilita la connessione. Metodi come <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> e <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> appartengono alla proprietà dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di programmi SMO](creating-smo-programs.md)  
  
  