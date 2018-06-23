---
title: INFORMATION_SCHEMA. I nomi degli schemi restituisce degli schemi in un database, i database non inclusi in un'istanza | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e624597090ab6a7efdb21ebbff6785b1471d7367
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169563"
---
# <a name="informationschemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA restituisce i nomi degli schemi di un database, non i database di un'istanza
  Sono state rilevate istruzioni che fanno riferimento alla vista INFORMATION_SCHEMA.SCHEMATA. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la vista restituisce tutti i database inclusi in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mentre in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive restituisce tutti gli schemi di un database.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la vista INFORMATION_SCHEMA.SCHEMATA restituisce tutti i database inclusi in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mentre ora restituisce tutti gli schemi di un database, in modo conforme allo standard SQL.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare l'applicazione per fare riferimento il **Sys. Databases** per restituire tutti i database in un'istanza di vista del catalogo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;nuovo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
