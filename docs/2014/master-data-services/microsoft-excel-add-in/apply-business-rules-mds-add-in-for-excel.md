---
title: Applicare le regole di business (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: eb340f0786c61ef1536b893b309bdc959108087a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174031"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Applicare le regole business (componente aggiuntivo MDS per Excel)
  Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] applicare le regole di business quando si vuole convalidare i dati e confermare che sono validi. È possibile correggere le convalide e pubblicare nuovamente i dati.  
  
> [!NOTE]  
>  La convalida dei dati si verifica automaticamente quando si pubblicano dati. Per altre informazioni, vedere [Stored procedure di convalida &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'accesso all'area funzionale **Visualizzatore** .  
  
-   È necessario avere un foglio di lavoro attivo che contenga i dati gestiti da MDS.  
  
### <a name="to-apply-business-rules"></a>Per applicare le regole business  
  
1.  Nel gruppo **Pubblica e convalida** fare clic su **Applica regole**.  
  
    > [!NOTE]  
    >  Il numero di membri (righe) convalidati contemporaneamente dipende da un'impostazione in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Per altre informazioni, vedere [Impostazioni delle regole business](../system-settings-master-data-services.md#BusinessRules).  
  
2.  I dati vengono convalidati automaticamente rispetto alle regole business e vengono visualizzate due colonne. Se queste colonne non sono visualizzate automaticamente, nel gruppo **Pubblica e convalida** fare clic su **Mostra stato** per visualizzarle.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione di dati &#40;componente aggiuntivo MDS per Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
