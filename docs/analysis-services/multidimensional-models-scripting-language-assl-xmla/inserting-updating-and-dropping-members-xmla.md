---
title: Inserimento, aggiornamento ed eliminazione di membri (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- inserting dimension members
- XML for Analysis, members
- removing dimension members
- dropping dimension members
- write-enabled dimensions [Analysis Services]
- XMLA, members
- deleting dimension members
- dimensions [Analysis Services], XML for Analysis
ms.assetid: bba922b5-8b88-4051-9506-ff055248182a
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d98ad262e92a1da61c6ac3dda67aaac871dabd1e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="inserting-updating-and-dropping-members-xmla"></a>Inserimento, aggiornamento ed eliminazione di membri (XMLA)
  È possibile utilizzare il [inserire](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [aggiornare](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), e [Drop](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md) comandi XML for Analysis (XMLA) consentono rispettivamente di inserire, aggiornare o eliminare membri da una dimensione abilitata per la scrittura. Per ulteriori informazioni sulle dimensioni abilitate per la scrittura, vedere [dimensioni abilitate per la scrittura](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
## <a name="inserting-new-members"></a>Inserimento di nuovi membri  
 Il **inserire** comando inserisce nuovi membri in attributi specificati in una dimensione abilitata per la scrittura.  
  
 Prima di costruire il **inserire** comando, è necessario disponibili per i nuovi membri da inserire le informazioni seguenti:  
  
-   Dimensione in cui inserire i nuovi membri.  
  
-   Attributo della dimensione in cui inserire i nuovi membri.  
  
-   Nomi dei nuovi membri, inclusa qualsiasi conversione applicabile per il nome.  
  
-   Chiavi dei nuovi membri. Se un attributo utilizza una chiave composta, per la chiave può essere necessario utilizzare più valori.  
  
-   Valori per tutte le proprietà dell'attributo applicabili non implementate come altri attributi nella dimensione. Tali proprietà includono operazioni unarie, conversioni, rollup personalizzati e relative proprietà e livelli ignorati.  
  
 Il **inserire** comando accetta solo due proprietà:  
  
-   Il [oggetto](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) proprietà che contiene un riferimento all'oggetto per la dimensione in cui devono essere inseriti i membri. Il riferimento all'oggetto contiene l'identificatore di database, l'identificatore di cubo e l'identificatore di dimensione per la dimensione.  
  
-   Il [attributi](../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md) proprietà, che contiene uno o più [attributo](../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) elementi per identificare gli attributi in cui devono essere inseriti i membri. Ogni **attributo** elemento identifica un attributo e fornisce nome, valore, traduzioni, operatore unario, rollup personalizzati, le proprietà personalizzate di rollup e livelli ignorati per un singolo membro da aggiungere all'attributo identificato.  
  
    > [!NOTE]  
    >  Tutte le proprietà per il **attributo** elemento deve essere incluso. In caso contrario, è possibile che si verifichi un errore.  
  
## <a name="updating-existing-members"></a>Aggiornamento di membri esistenti  
 Il **aggiornamento** comando Aggiorna i membri esistenti in attributi specificati, in base alle relazioni con altri membri in altri attributi, in una dimensione abilitata per la scrittura. Il **aggiornamento** comando è possibile spostare membri in altri livelli delle gerarchie contenute nella dimensione e possono essere utilizzati per ristrutturare gerarchie padre-figlio definite dagli attributi padre.  
  
 Prima di costruire il **aggiornamento** comando, è necessario disponibili per i membri da aggiornare le informazioni seguenti:  
  
-   Dimensione in cui aggiornare i membri esistenti.  
  
-   Attributi della dimensione in cui aggiornare i membri esistenti.  
  
-   Chiavi dei membri esistenti. Se un attributo utilizza una chiave composta, per la chiave può essere necessario utilizzare più valori.  
  
-   Valori per tutte le proprietà dell'attributo applicabili non implementate come altri attributi nella dimensione. Tali proprietà includono operazioni unarie, conversioni, rollup personalizzati e relative proprietà e livelli ignorati.  
  
 Il **aggiornamento** comando accetta solo tre proprietà obbligatorie:  
  
-   Il **oggetto** proprietà che contiene un riferimento all'oggetto per la dimensione in cui i membri devono essere aggiornati. Il riferimento all'oggetto contiene l'identificatore di database, l'identificatore di cubo e l'identificatore di dimensione per la dimensione.  
  
-   Il **attributi** proprietà, che contiene uno o più **attributo** elementi per identificare gli attributi in cui devono essere aggiornati i membri. Il **attributo** elemento identifica un attributo e fornisce nome, valore, traduzioni, operatore unario, rollup personalizzati, le proprietà personalizzate di rollup e livelli ignorati per un singolo membro da aggiornare per l'attributo identificato.  
  
    > [!NOTE]  
    >  Tutte le proprietà per il **attributo** elemento deve essere incluso. In caso contrario, è possibile che si verifichi un errore.  
  
-   Il [in](../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md) proprietà, che contiene uno o più **attributo** gli elementi che vincolano gli attributi in cui devono essere aggiornati i membri. Il **in** proprietà è fondamentale per limitare un **aggiornamento** per istanze specifiche di un membro. Se il **dove** proprietà non è specificata, vengono aggiornate tutte le istanze di un membro specifico. Si supponga ad esempio che siano presenti tre clienti per cui si desidera modificare il nome di città da Redmond in Bellevue. Per modificare il nome della città, è necessario fornire un **dove** proprietà che identifica il cliente i tre membri dell'attributo per cui i membri dell'attributo City devono essere modificati. Se non si specifica questo **in** proprietà, ogni cliente il cui nome di città è attualmente Redmond avrebbe il nome di città Bellevue dopo il **aggiornamento** esecuzione del comando.  
  
    > [!NOTE]  
    >  Ad eccezione dei nuovi membri, il **aggiornare** comando possibile aggiornare solo i valori di chiave di attributo per gli attributi non presenti il **in cui** clausola. Quando ad esempio viene aggiornato un cliente, il relativo nome di città non può essere aggiornato. In caso contrario, il nome di città viene modificato per tutti i clienti.  
  
### <a name="updating-members-in-parent-attributes"></a>Aggiornamento di membri in attributi padre  
 Per supportare gli attributi padre, il **aggiornamento** comando facoltativo [MoveWithDescendants](../../analysis-services/xmla/xml-elements-properties/movewithdescendants-element-xmla.md)utilizza proprietà. L'impostazione di **MoveWithDescendants** proprietà su true indica che i discendenti del membro padre comporta lo spostamento con il membro padre quando cambia l'identificatore del membro padre. Se questo valore è impostato su false, lo spostamento di un membro padre comporta la promozione dei relativi discendenti immediati al livello in cui il membro padre si trovava in precedenza.  
  
 Quando l'aggiornamento dei membri di un attributo padre, il **aggiornare** comando non è possibile aggiornare i membri di altri attributi.  
  
## <a name="dropping-existing-members"></a>Eliminazione di membri esistenti  
 Prima di costruire il **Drop** comando, è necessario disponibili per i membri da eliminare le informazioni seguenti:  
  
-   Dimensione in cui eliminare i membri esistenti.  
  
-   Attributi della dimensione in cui eliminare i membri esistenti.  
  
-   Chiavi dei membri esistenti da eliminare. Se un attributo utilizza una chiave composta, per la chiave può essere necessario utilizzare più valori.  
  
 Il **Drop** comando accetta solo due proprietà obbligatorie:  
  
-   Il **oggetto** proprietà che contiene un riferimento all'oggetto per la dimensione in cui i membri devono essere eliminati. Il riferimento all'oggetto contiene l'identificatore di database, l'identificatore di cubo e l'identificatore di dimensione per la dimensione.  
  
-   Il **in** proprietà, che contiene uno o più **attributo** elementi per limitare gli attributi in cui i membri devono essere eliminati. Il **in** proprietà è fondamentale per limitare un **Drop** per istanze specifiche di un membro. Se il **dove** comando non è specificato, vengono eliminate tutte le istanze di un membro specifico. Si supponga ad esempio che siano presenti tre clienti che si desidera eliminare da Redmond. Per eliminare tali clienti, è necessario fornire un **dove** proprietà che identifica i tre membri dell'attributo Customer da rimuovere e il membro Redmond dell'attributo City da cui i tre clienti devono essere rimossi. Se il **in** proprietà specifica solo il membro Redmond dell'attributo City, ogni cliente associato a Redmond verrebbe eliminato dal **Drop** comando. Se il **in** proprietà specifica solo i tre membri dell'attributo Customer, i tre clienti verrebbero completamente eliminati dal **Drop** comando.  
  
    > [!NOTE]  
    >  Il **attributo** elementi inclusi un **Drop** comando deve contenere solo il **AttributeName** e **chiavi** proprietà. In caso contrario, è possibile che si verifichi un errore.  
  
### <a name="dropping-members-in-parent-attributes"></a>Eliminazione di membri in attributi padre  
 L'impostazione di [DeleteWithDescendants](../../analysis-services/xmla/xml-elements-properties/deletewithdescendants-element-xmla.md) proprietà indica che i discendenti di un membro padre devono essere eliminati anche con il membro padre. Se questo valore è impostato su false, i discendenti immediati del membro padre vengono invece promossi al livello in cui il membro padre si trovava in precedenza.  
  
> [!IMPORTANT]  
>  Per eliminare sia il membro padre che i relativi discendenti, è sufficiente che un utente disponga delle autorizzazioni per l'eliminazione del solo membro padre e non è necessario che disponga delle autorizzazioni per l'eliminazione dei discendenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Eliminare l'elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Inserisci elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Elemento Update &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Definizione e identificazione di oggetti &#40; XMLA &#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
