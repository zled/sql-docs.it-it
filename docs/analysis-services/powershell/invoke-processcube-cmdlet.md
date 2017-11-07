---
title: Cmdlet Invoke-ProcessCube | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b10ba7c1-8f10-4e72-9626-f9285e4341fd
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e54ec7316c74bd1551194c318e9a981dff341b72
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="invoke-processcube-cmdlet"></a>Cmdlet Invoke-ProcessCube

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Elaborare un cubo utilizzando una variabile di tipo di elaborazione specifica.  
  
>[!NOTE] 
>In questo articolo può contenere esempi e informazioni non aggiornate. Usare il cmdlet Get-Help per la versione più recente.
  
## <a name="syntax"></a>Sintassi  
 `Invoke-ProcessCube [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
 `Invoke-ProcessCube –DatabaseCube <Microsoft.AnalysisServices.Cube> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Il cmdlet Invoke-ProcessCube elabora un cubo al livello specificato. Ad esempio, ProcessFull sovrascrive dati esistenti con tutti dati nuovi. Quando si elabora un cubo, è necessario specificare il tipo di elaborazione. Per altre informazioni, vedere [Opzioni e impostazioni di elaborazione &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-name-string"></a>-Nome \<stringa >  
 Specifica il cubo da elaborare.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|0|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-database-string"></a>-Database \<stringa >  
 Specifica il database a cui appartiene il cubo.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|1|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>-ProcessType \<Microsoft.AnalysisServices.ProcessType >  
 Specifica il tipo di processo: ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache, ProcessRecalc.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|2|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-databasecube-microsoftanalysissevicescube"></a>-DatabaseCube \<Microsoft.AnalysisSevices.Cube >  
 Specifica un oggetto Microsoft.AnalysisServices.Cube da elaborare. Utilizzare questo parametro se si desidera passare il nome del cubo tramite pipeline.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByPropertyName)|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|Nessuno|  
|Output|Nessuno|  
  
## <a name="example-1"></a>Esempio 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works > Get-Item .| Invoke-ProcessCube–ProcessType:ProcessDefault`  
  
 Questo comando reindirizza l'identità del cubo da elaborare.  
  
## <a name="example-2"></a>Esempio 2  
 `PS SQL SERVER:\sqlas\locahost\default > Invoke-ProcessCube “Adventure Works” –database AWTEST –ProcessType:ProcessDefault`  
  
 Questo comando elabora il cubo Adventure Works nel database AWTEST.   
  
  

