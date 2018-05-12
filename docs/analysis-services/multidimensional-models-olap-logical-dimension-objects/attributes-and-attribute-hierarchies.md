---
title: Gli attributi e gerarchie di attributi | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e30f3be6270cdc62b4b17048f9032a7c5587557
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="attributes-and-attribute-hierarchies"></a>Attributi e gerarchie di attributi
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Le dimensioni sono raccolte di attributi, associate a una o più colonne in una tabella o una vista della vista origine dati.  
  
## <a name="key-attribute"></a>Attributo chiave  
 Ogni dimensione contiene un attributo chiave. Ogni attributo è associato a una o più colonne di una tabella della dimensione. L'attributo chiave è l'attributo di una dimensione che identifica le colonne della tabella principale della dimensione utilizzate nelle relazioni di chiave esterna con la tabella dei fatti. In genere, l'attributo chiave rappresenta la colonna o le colonne chiave primaria nella tabella della dimensione. È possibile definire una chiave primaria logica in una tabella di una vista origine dati che non disponga di una chiave primaria fisica nell'origine dei dati sottostante. **Per ulteriori informazioni**, vedere [definire chiavi primarie logiche in una vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-logical-primary-keys-in-a-data-source-view-analysis-services.md). Quando si definiscono gli attributi chiave, tramite la Creazione guidata cubo e la Creazione guidata dimensione viene eseguito un tentativo di utilizzo delle colonne chiave primaria della tabella della dimensione nella vista origine dati. Se nella tabella della dimensione non è definita una chiave primaria logica o una chiave primaria fisica, tramite le procedure guidate potrebbe non essere possibile definire correttamente gli attributi chiave per la dimensione.  
  
## <a name="binding-an-attribute-to-columns-in-data-source-view-tables-or-views"></a>Associazione di un attributo a colonne di tabelle o viste della vista origine dati  
 Un attributo è associato a colonne di una o più tabelle o viste della vista origine dati. Un attributo è sempre associato a una o più colonne chiave, che determinano i membri inclusi nell'attributo. Per impostazione predefinita, la colonna chiave è l'unica colonna a cui un attributo è associato. Un attributo può inoltre essere associato a una o più colonne aggiuntive per scopi specifici. Ad esempio, un attributo **NameColumn** proprietà determina il nome visualizzato all'utente per ogni membro dell'attributo, questa proprietà dell'attributo può essere associato a una colonna particolare dimensione tramite una vista origine dati o può essere associata a una colonna calcolata nella vista origine dati. Per ulteriori informazioni, vedere [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md).  
  
## <a name="attribute-hierarchies"></a>Gerarchie di attributi  
 Per impostazione predefinita, i membri degli attributi sono organizzati in gerarchie a due livelli, costituite da un livello foglia e da un livello Totale. Il livello Totale contiene il valore aggregato dei membri dell'attributo nelle misure di ogni gruppo di misure di cui la dimensione a cui è correlato l'attributo è membro. Tuttavia, se il **IsAggregatable** è impostata su False, il livello totale non è stato creato. Per ulteriori informazioni, vedere [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md).  
  
 Gli attributi vengono in genere organizzati in gerarchie definite dall'utente che indicano i percorsi drill-down che è possibile utilizzare per esplorare i dati nei gruppi di misure a cui un attributo è correlato. Nelle applicazioni client gli attributi possono essere utilizzati per ottenere informazioni sui raggruppamenti e sui vincoli. Quando gli attributi vengono organizzati in gerarchie definite dall'utente, si definiscono relazioni tra i livelli di gerarchia quando i livelli sono correlati in un molti-a-uno o di una relazione uno a uno (chiamato un *naturale* relazione). In una gerarchia Calendar Time, ad esempio, un livello Day dovrà essere correlato al livello Month, il livello Month al livello Quarter e così via. Grazie alla definizione delle relazioni tra i livelli in una gerarchia definita dall'utente, Analysis Services consente di definire aggregazioni più utili al fine di migliorare le prestazioni di esecuzione delle query e l'utilizzo della memoria da parte dei processi di elaborazione, ottimizzando l'utilizzo di cubi complessi o di grandi dimensioni. Per ulteriori informazioni, vedere [gerarchie utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md), [Create User-Defined gerarchie](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md), e [definire relazioni tra attributi](../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
## <a name="attribute-relationships-star-schemas-and-snowflake-schemas"></a>Relazioni tra attributi, schemi star e schemi snowflake  
 Per impostazione predefinita, in uno schema star tutti gli attributi sono direttamente correlati all'attributo chiave, che consente agli utenti di esplorare i fatti nel cubo in base a qualsiasi gerarchia di attributo nella dimensione. In uno schema snowflake, un attributo è direttamente collegato all'attributo chiave se la relativa tabella sottostante è direttamente collegata alla tabella dei fatti oppure è indirettamente collegato tramite l'attributo associato alla chiave nella tabella sottostante che collega la tabella con schema snowflake alla tabella collegata direttamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare gerarchie definite dall'utente](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)   
 [Definire relazioni tra attributi](../../analysis-services/multidimensional-models/attribute-relationships-define.md)   
 [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
