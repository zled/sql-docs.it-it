---
title: Corrispondenza Data Quality nel componente aggiuntivo MDS per Excel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be78d051-0d56-46d3-bb89-327e218dadd6
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 08040fafaa66570d3c0f2023bc1a66d0f82c1d4d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063149"
---
# <a name="data-quality-matching-in-the-mds-add-in-for-excel"></a>Corrispondenza Data Quality nel componente aggiuntivo MDS per Excel
  Con il tempo, sarà necessario aggiungere ulteriori dati al repository MDS. Prima di aggiungere i dati, può essere utile confrontare i nuovi dati con quelli già gestiti in MDS, per verificare che non si stiano aggiungendo dati duplicati o non accurati.  
  
 In [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] MDS viene utilizzata la funzionalità Data Quality Services (DQS) di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per mettere in corrispondenza i dati simili. Quando si utilizza la funzionalità di ricerca di corrispondenza nel componente aggiuntivo, i record simili vengono raggruppati e viene visualizzato un punteggio che rappresenta l'accuratezza del risultato. Per altre informazioni sulla funzionalità di ricerca di corrispondenza fornita da DQS, vedere [Corrispondenza di dati](../../data-quality-services/data-matching.md).  
  
## <a name="workflow-for-data-quality-matching"></a>Flusso di lavoro per la corrispondenza Data Quality  
 Quando si usa DQS con [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]MDS, usare il flusso di lavoro seguente:  
  
1.  Recuperare un elenco di dati gestiti da MDS e combinarlo con un elenco non gestito in MDS. Per altre informazioni, vedere [Combine Data &#40;MDS Add-in for Excel&#41;](combine-data-mds-add-in-for-excel.md).  
  
2.  Utilizzare la Knowledge Base DQS per confrontare i dati nell'elenco combinato. Per altre informazioni, vedere [Match Similar Data &#40;MDS Add-in for Excel&#41;](match-similar-data-mds-add-in-for-excel.md).  
  
3.  Per visualizzare ulteriori dettagli sulle analogie trovate da DQS, mostrare le colonne dei dettagli.  
  
4.  Analizzare i risultati e determinare quali dati devono essere aggiunti al repository MDS e quali dati sono duplicati.  
  
5.  Pubblicare i dati nuovi e/o aggiornati nel repository MDS.  
  
## <a name="knowledge-bases"></a>Knowledge Base  
 I risultati della corrispondenza forniti nel componente aggiuntivo sono basati su una Knowledge Base DQS.  
  
-   La Knowledge Base predefinita (DQS Data) viene creata al momento dell'installazione di DQS. Se si sceglie din utilizzare la Knowledge Base predefinita, senza aggiungere i criteri di corrispondenza alla Knowledge Base predefinita nel client Data Quality, è necessario eseguire il mapping delle colonne nel foglio di lavoro ai domini nella Knowledge Base, quindi assegnare un valore di peso ai domini scelti.  
  
-   È possibile utilizzare il client Data Quality per creare una nuova Knowledge Base con criteri di corrispondenza o per aggiungere i criteri di corrispondenza alla Knowledge Base predefinita. In questo caso, i valori di peso sono determinati dai criteri di corrispondenza già creati ed è necessario solo eseguire il mapping delle colonne ai domini. Per altre informazioni, vedere [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
 Per altre informazioni sulle Knowledge Base, vedere [Knowledge Base e domini DQS](../../data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Combinare dati esterni con i dati gestiti da MDS in preparazione a un confronto.|[Combinare i dati &#40;componente aggiuntivo MDS per Excel&#41;](combine-data-mds-add-in-for-excel.md)|  
|Utilizzare la Knowledge Base DQS per trovare analogie nei dati.|[Cercare la corrispondenza tra dati simili &#40;componente aggiuntivo MDS per Excel&#41;](match-similar-data-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Pubblicazione di dati &#40;componente aggiuntivo MDS per Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [Corrispondenza di dati](../../data-quality-services/data-matching.md)  
  
  