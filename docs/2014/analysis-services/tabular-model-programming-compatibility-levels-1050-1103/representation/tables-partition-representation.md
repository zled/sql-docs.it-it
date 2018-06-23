---
title: Partizionare rappresentazione (tabulare) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b606cd63-755c-4ac0-b19b-95b5363afbdf
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6b05a9e169ec2227242be254d7eeb728693ea513
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167935"
---
# <a name="partition-representation-tabular"></a>Rappresentazione di una partizione (tabulare)
  Per scopi operativi una tabella può essere divisa in diversi subset di righe che, quando vengono combinate formano la tabella. Ognuno di tali subset è una partizione della tabella.  
  
## <a name="partition-representation"></a>Rappresentazione di una partizione  
 In termini di oggetti AMO, una rappresentazione di partizione dispone di una relazione di mapping uno-a-uno con <xref:Microsoft.AnalysisServices.Partition> e non sono richiesti altri oggetti AMO principali.  
  
### <a name="partition-in-amo"></a>Partizione in AMO  
 In caso di utilizzo di AMO per gestire una partizione, è necessario trovare il gruppo di misure che rappresenta la tabella di modelli tabulari e operare iniziando da tale ambito.  
  
 Nel frammento di codice seguente viene illustrato come aggiungere una partizione a una tabella di modelli tabulari esistente.  
  
```  
  
private void AddPartition(  
                     AMO.Cube modelCube  
                  ,  AMO.DataSource newDatasource  
                  ,  string mgName  
                  ,  string newPartitionName  
                  , string partitionSelectStatement  
                  , Boolean processPartition  
             )  
{  
    mgName = mgName.Trim();  
    newPartitionName = newPartitionName.Trim();  
    partitionSelectStatement = partitionSelectStatement.Trim();  
    //Validate Input  
    if (string.IsNullOrEmpty(newPartitionName) || string.IsNullOrWhiteSpace(newPartitionName))  
    {  
        MessageBox.Show(String.Format("Partition Name cannot be empty or blank"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (modelCube.MeasureGroups[mgName].Partitions.ContainsName(newPartitionName))  
    {  
        MessageBox.Show(String.Format("Partition Name already defined. Duplicated names are not allowed"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (string.IsNullOrEmpty(partitionSelectStatement) || string.IsNullOrWhiteSpace(partitionSelectStatement))  
    {  
        MessageBox.Show(String.Format("Select statement cannot be empty or blank"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    //Input validated  
    string partitionID = newPartitionName; //Using partition name as the ID  
    AMO.Partition currentPartition = new AMO.Partition(partitionID, partitionID);  
    currentPartition.StorageMode = AMO.StorageMode.InMemory;  
    currentPartition.ProcessingMode = AMO.ProcessingMode.Regular;  
    currentPartition.Source = new AMO.QueryBinding(newDatasource.ID, partitionSelectStatement);  
    modelCube.MeasureGroups[mgName].Partitions.Add(currentPartition);  
    try  
    {  
        modelCube.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        if (processPartition)  
        {  
            modelCube.MeasureGroups[mgName].Partitions[partitionID].Process(AMO.ProcessType.ProcessFull);  
            MessageBox.Show(String.Format("Partition successfully processed."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        }  
  
    }  
    catch (AMO.AmoException amoXp)  
    {  
        MessageBox.Show(String.Format("AMO exception accessing the server.\nError message: {0}", amoXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (Exception)  
    {  
        throw;  
    }  
}  
  
```  
  
## <a name="amo2tabular-sample"></a>Esempio AMO2Tabular  
 Per comprendere tuttavia la modalità di utilizzo di AMO (Analysis Management Objects) per creare e modificare le rappresentazioni della partizione, vedere il codice sorgente dell'esempio AMO to Tabular. L'esempio è disponibile in Codeplex. Nota importante sul codice: il codice viene fornito solo come supporto ai concetti logici illustrati in questo argomento e non deve essere utilizzato in un ambiente di produzione né deve essere utilizzato per altro scopo se non quello formativo.  
  
  