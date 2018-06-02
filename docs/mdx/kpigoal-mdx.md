---
title: KPIGoal (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4d7bfd5c6458e725692a0c0fcd8c7b3d03a1ca29
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580293"
---
# <a name="kpigoal-mdx"></a>KPIGoal (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il membro da cui viene calcolato il valore della parte relativa all'obiettivo dell'indicatore di prestazioni chiave (KPI) specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
KPIGoal(KPI_Name)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Nome_kpi*  
 Espressione stringa valida che specifica il nome di un indicatore di prestazioni chiave (KPI).  
  
## <a name="remarks"></a>Remarks  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituiti valore, obiettivo, stato e tendenza dell'indicatore di prestazioni chiave (KPI) relativo alla misura del ricavo del canale per i discendenti di tre membri della gerarchia dell'attributo Fiscal Year:  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
