---
title: Creazione di un set di righe con IOpenRowset | Documenti Microsoft
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
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7cdce7632aa726d2992a0383d19691569ed57c0a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170558"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Creazione di un set di righe con IOpenRowset
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta il **IOpenRowset:: OPENROWSET** (metodo) con le restrizioni seguenti:  
  
-   Una tabella di base o una vista deve essere specificato in un database ID (DBID) struttura che la *pTableID* cui punta il parametro.  
  
-   Il DBID *eKind* membro deve indicare DBKIND_NAME.  
  
-   Il DBID *uName* membro deve specificare il nome di una tabella di basa esistente o una vista come una stringa di caratteri Unicode.  
  
-   Il *pIndexID* parametro della **OpenRowset** deve essere NULL.  
  
 Il set di risultati di **IOpenRowset:: OPENROWSET** contiene un singolo set di righe. Set di risultati che contengono un singolo set di righe possono essere supportati da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cursori. Il supporto del cursore consente allo sviluppatore di utilizzare i meccanismi di concorrenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](rowsets.md)  
  
  