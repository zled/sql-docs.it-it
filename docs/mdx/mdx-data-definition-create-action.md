---
title: Istruzione CREATE ACTION (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE ACTION
- Action
- CREATE
- CREATE_ACTION
dev_langs: kbMDX
helpviewer_keywords:
- invocation types [MDX]
- dimensions [Analysis Services], actions
- CREATE ACTION statement
- cubes [Analysis Services], actions
- actions [MDX]
- hierarchies [Analysis Services], actions
ms.assetid: 0419f349-ece2-42ba-8552-a1023f268a41
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 22c4cb48c762f2686f4cad86499b64cad0cc7e8b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---create-action"></a>Definizione dei dati MDX - creare azioni
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Crea un'azione che può essere associata a un cubo, a una dimensione, a una gerarchia o a un oggetto subordinato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE ACTION CURRENTCUBE | Cube_Name  
   .Action_Name <action body>  
<action body> ::=   
FOR   
        CUBE   
    | Hierarchy_Name [MEMBERS]   
    | Level_Name [MEMBERS]   
    | CELLS   
    | SET }   
      AS 'MDX_Expression'   
        [, TYPE = '  
              { URL   
            | HTML   
            | STATEMENT   
               | DATASET   
            | ROWSET   
            | COMMANDLINE   
               | PROPRIETARY }   
         ']  
   [ , INVOCATION = 'INTERACTIVE | ON_OPEN | BATCH ' ]  
   [ , APPLICATION = String_Expression ]  
   [ , DESCRIPTION = String_Expression ]  
   [ , CAPTION = 'MDX_Expression' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Stringa valida che specifica il nome di un cubo.  
  
 *Nome Action_*  
 Stringa valida che specifica il nome dell'azione da creare.  
  
 *Nome Hierarchy_*  
 Stringa valida che specifica il nome di una gerarchia.  
  
 *Nome Level_*  
 Stringa valida che specifica il nome di un livello.  
  
 *Nome Member_*  
 Stringa valida che specifica il nome o la chiave di un membro.  
  
 *MDX_Expression*  
 Espressione MDX valida.  
  
 *String_Expression*  
 Espressione stringa valida.  
  
## <a name="remarks"></a>Osservazioni  
 Le applicazioni client possono creare ed eseguire azioni non sicure, così come possono utilizzare funzioni non sicure. Per evitare queste situazioni, utilizzare il **Safety Options** proprietà. Per ulteriori informazioni, vedere l'argomento dedicato alle opzioni di sicurezza.  
  
> [!NOTE]  
>  Questa istruzione è stata inclusa per compatibilità con le versioni precedenti. Familiarità con le azioni [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], ad esempio le azioni di drill-through o di un Report, non sono supportati.  
  
## <a name="action-types"></a>Tipi di azioni  
 Nella tabella seguente vengono descritti i diversi tipi di azioni disponibili in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
|Tipo di azione|Description|  
|-----------------|-----------------|  
|**URL**|Viene restituita una stringa costituita da un URL a cui accedere tramite browser Internet.<br /><br /> Nota: Se questa azione non inizia con `http://` o `https://`, l'azione sarà disponibile per il browser a meno che non **SafetyOptions** è impostato su **DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL**.|  
|**HTML**|Viene restituita una stringa costituita da uno script HTML. Tale stringa deve essere salvata in un file che sarà possibile visualizzare utilizzando un browser Internet. In questo caso è possibile che nell'ambito del codice HTML generato venga eseguito un intero script.|  
|**ISTRUZIONE**|Viene restituita una stringa è un'istruzione che deve essere eseguito mediante l'impostazione di **SetText** metodo di un oggetto comando per la stringa e la chiamata di **ICommand:: Execute**(metodo). Se il comando non riesce, verrà restituito un errore.|  
|**SET DI DATI**|Viene restituita una stringa è un'istruzione MDX che deve essere eseguita impostando il **SetText** metodo di un oggetto comando per la stringa e la chiamata di **ICommand:: Execute** metodo. L'interfaccia richiesta deve essere l'ID (IID) **IDataset**. Il comando riesce se viene creato un set di dati. L'applicazione client deve consentire all'utente di visualizzare il set di dati restituito.|  
|**SET DI RIGHE**|Simile a **DATASET**, anziché richiedere un IID di **IDataset**, l'applicazione client deve richiedere un IID di **IRowset**. Il comando riesce se viene creato un set di righe. L'applicazione client deve consentire all'utente di visualizzare il set di righe restituito.|  
|**RIGA DI COMANDO**|L'applicazione client deve eseguire la stringa dell'azione, che è costituita da una riga di comando.|  
|**PROPRIETARIO**|L'applicazione client può visualizzare o eseguire l'azione esclusivamente se dispone di informazioni personalizzate, non generiche, sull'azione specifica. Le azioni proprietarie non vengono restituite all'applicazione client, a meno che l'applicazione client richiede in modo esplicito, impostando la restrizione appropriata sul **APPLICATION_NAME**.|  
  
## <a name="invocation-types"></a>Tipi di chiamate  
 Nella tabella seguente vengono descritti i diversi tipi di chiamate disponibili in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Il tipo di chiamata viene utilizzato dall'applicazione client solo per determinare quando richiamare l'azione, ma non determina effettivamente il comportamento di chiamata dell'azione.  
  
|Tipo di chiamata|Description|  
|---------------------|-----------------|  
|**INTERATTIVO**|L'azione deve essere richiamata dall'applicazione client tramite l'interazione dell'utente.|  
|**ON_OPEN**|L'azione deve essere richiamata dall'applicazione client quando viene aperto l'oggetto di destinazione. Questo tipo di chiamata non è attualmente implementato.|  
|**BATCH**|L'azione deve essere richiamata dall'applicazione client quando l'oggetto di destinazione è coinvolto in un'operazione batch, secondo quanto determinato dall'applicazione client. Questo tipo di chiamata non è attualmente implementato.|  
  
### <a name="scope"></a>Ambito  
 Ogni azione è definita per un cubo specifico e ha un nome univoco in tale cubo. Un'azione può avere uno degli ambiti elencati nella tabella seguente.  
  
 Ambito cubo  
 Per azioni indipendenti da una dimensione, una cella o un membro specifico, ad esempio l'avvio di un'emulazione di terminale per un sistema di produzione AS/400.  
  
 Ambito dimensione  
 L'azione viene applicata a una dimensione specifica. Le azioni di questo tipo non dipendono dagli specifici livelli o membri selezionati.  
  
 Ambito livello  
 L'azione viene applicata a un livello di dimensione specifico. Le azioni di questo tipo non dipendono dallo specifico membro selezionato nella dimensione.  
  
 Ambito membro  
 L'azione viene applicata a membri specifici di un livello.  
  
 Ambito cella  
 L'azione viene applicata solo a celle specifiche.  
  
 Ambito set  
 L'azione viene applicata solo a un set. Il nome, **ActionParameterSet**, è riservato per usi dall'applicazione all'interno dell'espressione dell'azione.  
  
## <a name="see-also"></a>Vedere anche  
 [Le istruzioni di definizione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
