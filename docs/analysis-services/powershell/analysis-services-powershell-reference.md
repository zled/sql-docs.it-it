---
title: "Guida di riferimento a PowerShell per Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Guida di riferimento a PowerShell per Analysis Services
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include cmdlet e un provider PowerShell per Analysis Services (SQLASCMDLETS) in modo che sia possibile usare Windows PowerShell per la navigazione, l'amministrazione e l'esecuzione di query sugli oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per altre informazioni sul caricamento e sull'uso del provider e dei cmdlet, vedere [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md) (Script di PowerShell in Analysis Services). Per un esempio di come usare i tipi AMO in PowerShell per creare un database tabulare, vedere [AMO PowerShell Example](../../analysis-services/powershell/amo-powershell-example.md).  
  
##  <a name="bkmk_cmdlets"></a> Cmdlet di Analysis Services  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fornisce cmdlet che corrispondono ai metodi nello spazio dei nomi **Microsoft.AnalysisServices**. Nella tabella seguente viene descritto ogni cmdlet e viene fornito un collegamento al metodo AMO (Analysis Management Objects) corrispondente.  
  
 Se si vuole usare PowerShell per eseguire un'attività non inclusa nell'elenco seguente (ad esempio creare o sincronizzare un database), è possibile scrivere uno script TMSL o XMLA per tale azione, quindi eseguire lo script usando il cmdlet **Invoke-ASCmd**.  
  
|Cmdlet|Description|Metodi AMO equivalenti|  
|------------|-----------------|----------------------------|  
|[Cmdlet Add-RoleMember](../../analysis-services/powershell/add-rolemember-cmdlet.md)|Aggiungere un membro a un ruolo del database.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Cmdlet Backup-ASDatabase](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)|Eseguire il backup di un database di Analysis Services.|<xref:Microsoft.AnalysisServices.Database.Backup%2A>|  
|[Cmdlet Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)|Eseguire una query o uno script in formato XMLA o TSML (JSON).|<xref:Microsoft.AnalysisServices.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)|Elaborare un database.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Invoke-ProcessCube](../../analysis-services/powershell/invoke-processcube-cmdlet.md)|Elaborare un cubo.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Invoke-ProcessDimension](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)|Elaborare una dimensione.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Invoke-ProcessPartition](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)|Elaborare una partizione.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Invoke-ProcessTable](../../analysis-services/powershell/invoke-processtable-cmdlet.md)|Elaborare una tabella in un modello tabulare, in un modello di compatibilità 1200 o in una versione successiva.|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Cmdlet Merge-Partition](../../analysis-services/powershell/merge-partition-cmdlet.md)|Unire una partizione.|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[Cmdlet New-RestoreFolder](../../analysis-services/powershell/new-restorefolder-cmdlet.md)|Creare una cartella per contenere il backup di un database.|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[Cmdlet New-RestoreLocation](../../analysis-services/powershell/new-restorelocation-cmdlet.md)|Specificare uno o più server remoti in cui ripristinare il database.|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Cmdlet Remove-RoleMember](../../analysis-services/powershell/remove-rolemember-cmdlet.md)|Rimuovere un membro da un ruolo del database.|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Cmdlet Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)|Ripristinare un database in un'istanza del server.|<xref:Microsoft.AnalysisServices.Server.Restore%2A>|  
  
## Vedere anche  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Riferimento a Tabular Model Scripting Language &#40;TMSL&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Livello di compatibilità per i modelli tabulari in Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services Scripting Language &#40;ASSL per XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)  
  
  