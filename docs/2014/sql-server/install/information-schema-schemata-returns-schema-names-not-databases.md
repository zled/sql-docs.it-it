---
title: INFORMATION_SCHEMA. I nomi di schemi restituisce lo schema in un database, non i database in un'istanza | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c32683c6dc6aaa26079443d2ff4bc5d1f0994d76
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198441"
---
# <a name="informationschemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA restituisce i nomi degli schemi di un database, non i database di un'istanza
  Sono state rilevate istruzioni che fanno riferimento alla vista INFORMATION_SCHEMA.SCHEMATA. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la vista restituisce tutti i database inclusi in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mentre in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive restituisce tutti gli schemi di un database.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la vista INFORMATION_SCHEMA.SCHEMATA restituisce tutti i database inclusi in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mentre ora restituisce tutti gli schemi di un database, in modo conforme allo standard SQL.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare l'applicazione per fare riferimento il **Sys. Databases** per restituire tutti i database in un'istanza della vista del catalogo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
