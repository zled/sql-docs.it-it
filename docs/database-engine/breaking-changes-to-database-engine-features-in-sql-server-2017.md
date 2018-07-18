---
title: Modifiche di rilievo apportate alle funzionalità del Motore di database in SQL Server 2017 | Microsoft Docs
description: Modifiche di rilievo apportate alle funzionalità del motore di database in SQL Server 2017
ms.date: 04/19/2017
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-engine
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- breaking changes 2017 [SQL Server]
ms.assetid: ''
caps.latest.revision: 1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d709fa78a3c46d7e707b155b71ed5f49a83153c9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32863786"
---
# <a name="breaking-changes-to-database-engine-features-in-includesssqlv14-mdincludessssqlv14-mdmd"></a>Modifiche di rilievo apportate alle funzionalità del motore di database in [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)]
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


  In questo argomento vengono descritte le modifiche di rilievo introdotte nel [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)]. Tali modifiche potrebbero interrompere il funzionamento di applicazioni, funzionalità o script basati su versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È possibile che questi problemi si verifichino quando viene effettuato un aggiornamento.  
  
## <a name="breaking-changes-in-includesssqlv14-mdincludessssqlv14-mdmdincludessdeincludesssde-mdmd"></a>Modifiche di rilievo in [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)]  
  
-  CLR usa la Sicurezza dall'accesso di codice (CAS, Code Access Security) in .NET Framework, non più supportata come limite di sicurezza. A partire da [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)], viene introdotta un'opzione `sp_configure` denominata `clr strict security` per migliorare la sicurezza degli assembly CLR. CLR strict security è abilitata per impostazione predefinita e considera gli assembly CLR `SAFE` e `EXTERNAL_ACCESS` come se fossero contrassegnati `UNSAFE`. È possibile disabilitare l'opzione `clr strict security` per la compatibilità con le versioni precedenti, ma questa operazione è sconsigliata. Quando `clr strict security` è disabilitata, un assembly CLR creato con `PERMISSION_SET = SAFE` potrebbe essere in grado di accedere alle risorse di sistema esterne, chiamare codice non gestito e acquisire privilegi **sysadmin**. Dopo l'abilitazione di strict security, tutti gli assembly non firmati non verranno caricati. Inoltre, se il database dispone di assembly `SAFE` o `EXTERNAL_ACCESS`, le istruzioni `RESTORE` o `ATTACH DATABASE` possono essere completate ma gli assembly potrebbero non essere caricati.   
  Per caricare gli assembly, è necessario modificare oppure eliminare e ricreare ogni assembly in modo che sia firmato con un certificato o una chiave asimmetrica con un account di accesso corrispondente con l'autorizzazione `UNSAFE ASSEMBLY` nel server. Per altre informazioni, vedere [CLR strict security](../database-engine/configure-windows/clr-strict-security.md). 


  
## <a name="previous-versions"></a>Versioni precedenti  

-   [Modifiche di rilievo apportate alle funzionalità del Motore di database in SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
-   [Modifiche di rilievo apportate alle funzionalità del motore di database in SQL Server 2014](https://msdn.microsoft.com/library/ms143179\(v=sql.120\))  
  
-   [Modifiche di rilievo apportate alle funzionalità del motore di database in SQL Server 2012](https://msdn.microsoft.com/library/ms143179\(v=sql.110\))  
  
-   [Modifiche di rilievo apportate alle funzionalità del motore di database in SQL Server 2008](https://msdn.microsoft.com/library/ms143179\(v=sql.100\))  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del motore di database deprecate in SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Funzionalità del motore di database non più usate in SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Compatibilità con le versioni precedenti del motore di database di SQL Server](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
