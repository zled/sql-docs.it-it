---
title: Istruzione UPDATE MEMBER (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE_MEMBER
- UPDATE MEMBER
- MEMBER
- UPDATE
helpviewer_keywords:
- calculated members [MDX]
- UPDATE MEMBER statement
ms.assetid: 07ab708d-d165-4fb1-a9f9-fb8197ff0dab
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a08e79f52452f69cd755f0cd1345a894bd6017a3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---update-member"></a>Definizione dei dati MDX - UPDATE MEMBER
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiorna un membro calcolato esistente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
UPDATE MEMBER Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Stringa valida che specifica il nome del cubo che contiene il membro.  
  
 *Member_Name*  
 Stringa valida che specifica il nome del membro esistente.  
  
 *MDX_Expression*  
 Espressione MDX (Multidimensional Expression) valida nella quale il membro deve essere aggiornato.  
  
 *Property_name*  
 Stringa valida che specifica il nome per la proprietà di un membro calcolato.  
  
 *Property_Value*  
 Espressione scalare valida che specifica il valore della proprietà per il membro calcolato.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione UPDATE MEMBER aggiorna un membro calcolato esistente conservando la relativa precedenza di questo membro in relazione agli altri calcoli. Pertanto, non è possibile utilizzare l'istruzione UPDATE MEMBER per modificare SOLVEORDER.  
  
 Non è possibile specificare un'istruzione UPDATE MEMBER nello script MDX per un cubo.  
  
 Specificando un cubo diverso dal cubo connesso viene generato un errore. Pertanto, per identificare il cubo corrente è consigliabile usare CURRENTCUBE anziché il nome di un cubo.  
  
 Per altre informazioni sulle proprietà dei membri definite da OLE DB, vedere la documentazione di OLE DB.  
  
## <a name="standard-properties"></a>Proprietà standard  
 Ogni membro dispone di un set di proprietà predefinite. Nella seguente tabella vengono descritte queste proprietà predefinite.  
  
|Identificatore proprietà|Significato|  
|-------------------------|-------------|  
|FORMAT_STRING|Oggetto [!INCLUDE[msCoName](../includes/msconame-md.md)] stringa di formato di stile Office che l'applicazione client consente di visualizzare i valori delle celle.|  
|VISIBLE|Un valore che indica se il membro calcolato è visibile in un set di righe dello schema. Visible calcolati i membri possono essere aggiunti a un set con il [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) (funzione). Un valore diverso da zero indica che il membro calcolato è visibile. Il valore predefinito per questa proprietà è *Visible*.<br /><br /> I membri calcolati non visibili, vengono in genere utilizzati come passaggi intermedi in membri calcolati più complessi. A tali membri calcolati è possibile fare riferimento anche da altri tipi di membri, ad esempio le misure.|  
|NON_EMPTY_BEHAVIOR|La misura o il set che MDX utilizza per determinare il comportamento dei membri calcolati durante la risoluzione delle celle vuote.|  
|CAPTION|Un valore di stringa che specifica la didascalia che può essere utilizzata dall'applicazione client per la visualizzazione del membro.|  
|DISPLAY_FOLDER|Un valore di stringa che specifica il percorso della cartella di visualizzazione in cui il membro deve essere mostrato dall'applicazione client. Il separatore di livello delle cartelle è definito dall'applicazione client. Per gli strumenti e i client forniti da [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], la barra rovesciata (\\) come separatore del livello. Per fornire più cartelle di visualizzazione per un membro definito, utilizzare un punto e virgola (;) per separare le cartelle.|  
|ASSOCIATED_MEASURE_GROUP|Il nome del gruppo di misure al quale questo membro è associato.|  
  
## <a name="see-also"></a>Vedere anche  
 [DROP MEMBER-istruzione &#40; MDX &#41;](../mdx/mdx-data-definition-drop-member.md)   
 [CREARE l'istruzione MEMBER &#40; MDX &#41;](../mdx/mdx-data-definition-create-member.md)   
 [Le istruzioni di definizione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
