---
title: Proprietà SqlServiceType (classe SqlServiceAdvancedProperty) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
caps.latest.revision: 42
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d752b3879880fccf8eccf86a453afacf466ea7af
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>Proprietà SqlServiceType (classe SqlServiceAdvancedProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene il tipo del servizio gestito associato alla proprietà avanzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.SetBoolValue(NumValue)  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlServiceAdvancedProperty](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) che rappresenta una proprietà avanzata.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore uint32 che specifica il tipo di servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Osservazioni  
 I possibili valori restituiti sono i seguenti:  
  
|Tipo|Definizione|  
|----------|----------------|  
|*1*|MSSQLSERVER è il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|*2*|SQLSERVERAGENT è il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.|  
|*3*|MSFTESQL è il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] del motore di ricerca full-text.|  
|*4*|MsDtsServer è il servizio [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .|  
|*5*|MSSQLServerOLAPService è il servizio [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|  
|*6*|ReportServer è il servizio [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .|  
|*7*|SQLBrowser è il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser.|  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
