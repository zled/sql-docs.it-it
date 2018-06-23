---
title: La migrazione degli script a VSTA | Documenti Microsoft
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
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
caps.latest.revision: 44
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 99acbad66d2a614431bc1f08ad88bd12f2a3e6b4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170050"
---
# <a name="migrate-scripts-to-vsta"></a>Migrare script a VSTA
  Quando esegue l'aggiornamento [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] pacchetti [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene eseguita la migrazione degli script in qualsiasi attività Script o componente di Script a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). VSTA è l'ambiente di scripting utilizzato da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], l'ambiente di scripting per [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA).  
  
 Se gli script nelle attività Script o nei componenti di script fanno riferimento a interfacce, potrebbe essere necessario modificare tali riferimenti prima di aggiornare il pacchetto. In caso contrario, il pacchetto non verrà aggiornato o gli script non verranno convalidati, a seconda del metodo di aggiornamento utilizzato. Per modificare tali riferimenti, sostituire i riferimenti alle interfacce IDTS*xxx*90 interfacce con riferimenti a IDTS corrispondente*xxx*100 interfacce.  
  
 Per ulteriori informazioni su come eseguire la migrazione degli script e aggiornare i pacchetti, vedere [aggiornare pacchetti di Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
## <a name="understanding-migration-failures"></a>Informazioni sugli errori di migrazione  
 Quando si esegue la migrazione degli script, la migrazione può non riuscire a causa di uno dei motivi seguenti:  
  
-   Il punto di ingresso per lo script VSA è stato rinominato.  
  
     Il punto di ingresso specifica il metodo nella classe `ScriptMain` nel progetto VSTA chiamato dal runtime di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] come punto di ingresso nel codice dell'attività Script. La classe `ScriptMain` è la classe predefinita generata dai modelli di script.  
  
-   Nello script VSA non è presente alcun punto di ingresso o sono presenti più punti di ingresso.  
  
-   Non è stato possibile aggiungere riferimenti ad assembly.  
  
-   La classe `ScriptMain` è stata modificata per ereditare dalle altre classi oltre alla classe `ScriptObjectModelSSIS`. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] non supporta l'ereditarietà multipla.  
  
 Non è possibile convertire uno script VSA che utilizza [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] di uno script VSTA che utilizza [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Tuttavia, è possibile creare un nuovo script VSTA che utilizza [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]. Per altre informazioni, vedere [Scrittura di codice e debug dell'attività Script](../../integration-services/control-flow/script-task.md) e [Codifica e debug del componente Script](../../integration-services/data-flow/transformations/script-component.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di pacchetti tramite scripting](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  