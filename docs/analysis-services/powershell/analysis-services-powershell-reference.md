---
title: Analysis Services PowerShell Reference | Documenti Microsoft
ms.custom: 
ms.date: 06/21/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 4064f8eb4d2dfd37d0ae201977739fff9df67f1a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="analysis-services-powershell-reference"></a>Guida di riferimento a PowerShell per Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]I cmdlet di PowerShell sono inclusi nel [modulo SqlServer](https://www.powershellgallery.com/packages/SqlServer/21.0.17099). 
  
>[!NOTE] 
> Operazioni di database di Analysis Services Azure utilizzano il modulo SqlServer stesso come SQL Server Analysis Services. Tuttavia, non tutti i cmdlet sono supportati in Azure Analysis Services. Per ulteriori informazioni, vedere [gestire Azure Analysis Services con PowerShell](https://docs.microsoft.com/azure/analysis-services/analysis-services-powershell).
  
##  <a name="bkmk_cmdlets"></a> Cmdlet di Analysis Services  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fornisce cmdlet che corrispondono ai metodi nello spazio dei nomi **Microsoft.AnalysisServices** . Nella tabella seguente viene descritto ogni cmdlet e viene fornito un collegamento al metodo AMO (Analysis Management Objects) corrispondente.  
  
 Se si vuole usare PowerShell per eseguire un'attività non inclusa nell'elenco seguente (ad esempio creare o sincronizzare un database), è possibile scrivere uno script TMSL o XMLA per tale azione, quindi eseguire lo script usando il cmdlet **Invoke-ASCmd** .  
  
|Cmdlet|Description|Metodi AMO equivalenti|  
|------------|-----------------|----------------------------|  
|[Cmdlet Add-RoleMember](../../analysis-services/powershell/add-rolemember-cmdlet.md)|Aggiungere un membro a un ruolo del database.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Cmdlet Backup-ASDatabase](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)|Eseguire il backup di un database di Analysis Services.|[Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)|  
|[Cmdlet Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)|Eseguire una query o uno script in formato XMLA o TSML (JSON).|<xref:Microsoft.AnalysisServices.Core.Server.Execute%2A>|  
|[Cmdlet Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)|Elaborare un database.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Invoke-ProcessCube](../../analysis-services/powershell/invoke-processcube-cmdlet.md)|Elaborare un cubo.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Invoke-ProcessDimension](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)|Elaborare una dimensione.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Invoke-ProcessPartition](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)|Elaborare una partizione.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Invoke-ProcessTable](../../analysis-services/powershell/invoke-processtable-cmdlet.md)|Elaborare una tabella in un modello tabulare, il modello di compatibilità 1200 o superiore.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Merge-Partition](../../analysis-services/powershell/merge-partition-cmdlet.md)|Unire una partizione.|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[Cmdlet New-RestoreFolder](../../analysis-services/powershell/new-restorefolder-cmdlet.md)|Creare una cartella per contenere il backup di un database.|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[Cmdlet New-RestoreLocation](../../analysis-services/powershell/new-restorelocation-cmdlet.md)|Specificare uno o più server remoti in cui ripristinare il database.|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Cmdlet Remove-RoleMember](../../analysis-services/powershell/remove-rolemember-cmdlet.md)|Rimuovere un membro da un ruolo del database.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Cmdlet Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)|Ripristinare un database in un'istanza del server.|<xref:Microsoft.AnalysisServices.Core.Server.Restore%2A>|  
  

  
  
