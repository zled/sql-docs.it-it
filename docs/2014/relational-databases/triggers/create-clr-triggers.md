---
title: Creare trigger CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-dml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CRL triggers
- DML triggers, CLR triggers
- DDL triggers, CLR triggers
ms.assetid: 31f41703-134d-49fc-9850-76c297351c2c
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 398470880fb412048c96a3114f6d3c648ef4bc1a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065545"
---
# <a name="create-clr-triggers"></a>Creazione di trigger CLR
  È possibile creare un oggetto di database all'interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programmato in un assembly creato in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR). Tra gli oggetti di database che consentono l'utilizzo del ricco modello di programmazione offerto da CLR vi sono trigger DML, trigger DDL, stored procedure, funzioni, funzioni di aggregazione e tipi.  
  
 Per creare un trigger CLR (DML o DDL) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , eseguire le operazioni seguenti:  
  
-   Definire il trigger come una classe in un linguaggio supportato da .NET Framework. Per altre informazioni sulla programmazione di trigger in CLR, vedere [Trigger CLR](../../database-engine/dev-guide/clr-triggers.md). Compilare quindi la classe per ottenere un assembly in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] utilizzando il compilatore appropriato.  
  
-   Per registrare l'assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzare l'istruzione CREATE ASSEMBLY. Per altre informazioni sugli assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Assemblies &#40;Database Engine&#41;](../clr-integration/assemblies-database-engine.md).  
  
-   Creare il trigger che fa riferimento all'assembly registrato.  
  
> [!NOTE]  
>  Con la distribuzione di un progetto SQL Server in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene registrato un assembly nel database specificato per il progetto. La distribuzione del progetto crea inoltre trigger CLR nel database per tutti i metodi annotati con l'attributo `SqlTrigger`. Per altre informazioni, vedere [Distribuzione di oggetti di database CLR](../clr-integration/deploying-clr-database-objects.md).  
  
> [!NOTE]  
>  Per impostazione predefinita, l'esecuzione di codice CLR in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è disattivata. È possibile creare, modificare ed eliminare oggetti di database che fanno riferimento a moduli di codice gestito. Tali riferimenti non verranno tuttavia eseguiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a meno che non si attivi [l'opzione clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) usando [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).  
  
 **Per creare, modificare o eliminare un assembly**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-assembly-transact-sql)  
  
 **Per creare un trigger CLR**  
  
-   [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)  
  
## <a name="see-also"></a>Vedere anche  
 [Trigger DML](dml-triggers.md)   
 [Concetti relativi alla programmazione dell'integrazione con CLR &#40;Common Language Runtime&#41;](../clr-integration/common-language-runtime-clr-integration-programming-concepts.md)   
 [Accesso ai dati da oggetti di database CLR](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
