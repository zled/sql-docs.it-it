---
title: Utilizzo di Stored procedure (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- user-defined functions [MDX]
- stored procedures [MDX]
ms.assetid: 818fb2ad-f88b-4d0c-9f70-f378aed42e8e
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2c24641d2be7e4e2130d21881b94a9bcd1698fd7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="using-stored-procedures-mdx"></a>Utilizzo di stored procedure (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  È possibile estendere la funzionalità di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e delle espressioni MDX scrivendo stored procedure .NET o funzioni .NET definite dall'utente. Per ulteriori informazioni, vedere [programmazione Server ADOMD.NET](../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
 Quando si fa riferimento o si chiama una stored procedure, è necessario specificare il nome della funzione seguito da una coppia di parentesi. Nelle parentesi è possibile includere particolari espressioni, dette argomenti, che consentono di passare dati ai parametri. Quando si chiama una funzione è necessario specificare i valori degli argomenti per tutti i parametri, nella stessa sequenza in cui sono definiti i parametri nella funzione definita dall'utente.  
  
 La query di esempio seguente presuppone che si disponga di un assembly denominato SampleAssembly registrato nel server [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *Stored procedure di* è la terminologia utilizzata nel [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per questi tipi di funzioni. Le versioni precedenti di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] chiamato questi tipi di funzioni come *funzioni definite dall'utente*.  
  
## <a name="types-of-stored-procedures"></a>Tipi di stored procedure  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] supporta sia assembly COM che assembly CLR. È preferibile utilizzare gli assembly CLR, perché per tali assembly sono disponibili funzionalità di sicurezza più avanzate. Se nel server è installato Microsoft Office Excel, saranno disponibili anche le funzioni di Excel.  
  
> [!NOTE]  
>  Gli assembly COM creati con Microsoft Visual Basic, Applications Edition (VBA) vengono registrati automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; La sintassi MDX &#41;](../mdx/functions-mdx-syntax.md)  
  
  

