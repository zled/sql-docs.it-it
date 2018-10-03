---
title: Rimuovere operazioni DDL nelle tabelle inserite ed eliminate all'interno di trigger DML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe6aa8c12e6132fa44380158585bd13a7c313548
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48188231"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a>Rimuovere le istruzioni DDL eseguite su tabelle inserite ed eliminate all'interno di trigger DML
  Istruzioni data definition language (DDL), ad esempio CREATE INDEX non possono essere eseguite sulle tabelle inserite ed eliminate all'interno di trigger DML. Alcune istruzioni DDL sulle tabelle inserite ed eliminate sono consentite nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere "Utilizzo delle tabelle inserted e deleted" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Rimuovere le istruzioni DLL eseguite nelle tabelle inserite ed eliminate all'interno di trigger DML.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
