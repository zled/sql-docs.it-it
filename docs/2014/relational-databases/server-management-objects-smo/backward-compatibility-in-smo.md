---
title: Compatibilità con le versioni precedenti in SMO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a1406eaa3d8d9a82f28b1c813f08a3a570c8eefe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37313477"
---
# <a name="backward-compatibility-in-smo"></a>Compatibilità con le versioni precedenti in SMO
  Le applicazioni SMO create utilizzando le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono essere comunque ricompilate in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite SMO.  
  
## <a name="migrating-smo-applications"></a>Migrazione di applicazioni SMO  
 È necessario che i riferimenti alle DLL SMO nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengano rimossi e che vengano inclusi invece i riferimenti alle nuove DLL SMO disponibili in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Vengono utilizzati in genere i riferimenti agli elementi seguenti:  
  
-   Microsoft.SqlServer.ConnectionInfo  
  
-   Microsoft.SqlServer.Smo  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc  
  
 Tali file sono necessari per le classi di connessione, le classi di utilità SMO e le classi della libreria Microsoft Foundation Class.  
  
> [!NOTE]  
>  Poiché SmoEnum.dll è stato rimosso, è necessario che i riferimenti a tale file vengono rimossi dal progetto [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SMO.  
  
 Lo spazio dei nomi è stato modificato ed è pertanto necessario utilizzare gli elementi seguenti:  
  
##### <a name="for-visual-c"></a>Per Visual C#  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a>Per Visual Basic  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 Se nel codice viene utilizzata la funzionalità URN, ad esempio `Server.GetSqlSmoObject(Urn)`, è necessario collegarsi allo spazio dei nomi Microsoft.SqlServer.Management.Sdk.Sfc.  
  
 Se nel codice viene utilizzato direttamente l'oggetto Transfer, è necessario collegarsi allo spazio dei nomi Microsoft.SqlServer.Management.SmoExtended.  
  
 Potrebbe necessario modificare il codice quando si esegue la relativa migrazione, poiché numerose caratteristiche di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sono deprecate in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per altre informazioni sulle funzionalità deprecate, vedere [funzionalità del motore di Database deprecate in SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentazione Online.  
  
  
