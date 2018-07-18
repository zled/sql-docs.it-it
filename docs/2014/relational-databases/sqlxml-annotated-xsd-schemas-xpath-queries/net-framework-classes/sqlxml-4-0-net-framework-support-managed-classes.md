---
title: Classi gestite SQLXML | Microsoft Docs
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
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f718c0f23beba22afa5f9246951a8cac3a957145
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264287"
---
# <a name="sqlxml-managed-classes"></a>classi gestite SQLXML
  Le classi gestite [!INCLUDE[msCoName](../../../includes/msconame-md.md)] espongono la funzionalità di SQLXML 4.0 in [!INCLUDE[msCoName](../../../includes/msconame-md.md)].NET Framework. Le classi gestite SQLXML consentono di scrivere un'applicazione C# per accedere ai dati XML da un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], portare i dati nell'ambiente .NET Framework, elaborare i dati e inviare nuovamente gli aggiornamenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come DiffGram per applicarli. Quando si applicano aggiornamenti a un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando le classi gestite SQLXML, è necessario utilizzare uno schema di mapping. Per un esempio funzionante, vedere [l'accesso a funzionalità SQLXML nell'ambiente .NET](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Per utilizzare le classi gestite SQLXML con SQLXML 4.0, è necessario installare Microsoft Visual Studio.  
  
> [!NOTE]  
>  .NET Framework include il provider di dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET. Tale provider può essere utilizzato per accedere a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dall'ambiente .NET. È tuttavia in grado di gestire solo query SQL tradizionali (ovvero query del database relazionale ad eccezione delle query FOR XML). Non è possibile eseguire modelli XML o query XPath sul lato server in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Modello a oggetti di classi gestite SQLXML](../../../database-engine/dev-guide/sqlxml-managed-classes-object-model.md)  
 Vengono documentate le classi gestite SQLXML e le proprietà e i metodi rispettivi.  
  
 [Uso di classi gestite SQLXML](sqlxml-4-0-net-framework-support-managed-classes.md)  
 Vengono forniti esempi di utilizzo delle classi gestite SQLXML.  
  
  
