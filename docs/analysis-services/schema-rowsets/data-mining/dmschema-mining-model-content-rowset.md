---
title: Set di righe DMSCHEMA_MINING_MODEL_CONTENT | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1b1fec6efb8ec638c54226ffa9d2ef335beb19f0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="dmschemaminingmodelcontent-rowset"></a>Set di righe DMSCHEMA_MINING_MODEL_CONTENT
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Consente alle applicazioni client di esplorare il contenuto di un modello di data mining. Per passare al contenuto del modello di data mining, le applicazioni client possono utilizzare le restrizioni speciali relative alle operazioni sull'albero descritte alla fine di questo argomento.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_MODEL_CONTENT** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||Nome del catalogo. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Popola questa colonna con il nome del database di cui il modello è un membro.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **VT_NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**||Nome del modello al quale è associato il contenuto descritto da questa riga.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||Nomi degli attributi che corrispondono a questo nodo.|  
|**NODE_NAME**|**DBTYPE_WSTR**||Nome del nodo. Attualmente, questa colonna contiene lo stesso valore di **NODE_UNIQUE_NAME**, anche se ciò potrebbe cambiare nelle versioni future.|  
|**NODE_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco del nodo.|  
|**NODE_TYPE**|**DBTYPE_I4**||Tipo del nodo. Verrà generato uno dei valori seguenti (algoritmi di data mining di terze parti potrebbero determinare l'estensione di questo elenco):<br /><br /> **DM_NODE_TYPE_CLASSIFICATION_TREE_ROOT** (**2**)<br /><br /> **DM_NODE_TYPE_TREE_INTERIOR** (**3**)<br /><br /> **DM_NODE_TYPE_TREE_DISTRIBUTION** (**4**)<br /><br /> **DM_NODE_TYPE_CLUSTER** (**5**)<br /><br /> **DM_NODE_TYPE_UNKNOWN** (**6**)<br /><br /> **DM_NODE_TYPE_ITEMSET** (**7**)<br /><br /> **DM_NODE_TYPE_ASSOCIATION_RULE** (**8**)<br /><br /> **DM_NODE_TYPE_NB_PREDICTABLE_ATTRIBUTE** (**9**)<br /><br /> **DM_NODE_TYPE_NB_INPUT_ATTRIBUTE** (**10**)<br /><br /> **DM_NODE_TYPE_NB_INPUT_ATTRIBUTE_STATE** (**11**)<br /><br /> **DM_NODE_TYPE_SEQUENCE** (**13**)<br /><br /> **DM_NODE_TYPE_TRANSITION** (**14**)<br /><br /> **DM_NODE_TYPE_TIME_SERIES** (**15**)<br /><br /> **DM_NODE_TYPE_TS_TREE** (**16**)<br /><br /> **DM_NODE_TYPE_NN_SUBNETWORK** (**17**) rete neurale, subnet<br /><br /> **DM_NODE_TYPE_NN_INPUT_LAYER** (**18**) rete neurale, livello di input (nodo padre dei nodi di input)<br /><br /> **DM_NODE_TYPE_NN_HIDDEN_LAYER** (**19**) rete neurale, livello nascosto (nodo padre dei nodi nascosti)<br /><br /> **DM_NODE_TYPE_NN_OUTPUT_LAYER** (**20**) rete neurale, livello di output (nodo padre dei nodi di output)<br /><br /> **DM_NODE_TYPE_NN_INPUT_NODE** (**21**) rete neurale, nodo di input<br /><br /> **DM_NODE_TYPE_NN_HIDDEN_NODE** (**22**) rete neurale, nodo nascosto<br /><br /> **DM_NODE_TYPE_NN_OUTPUT_NODE** (**23**) rete neurale, nodo di output<br /><br /> **DM_NODE_TYPE_NN_MARGINAL_STAT_NODE** (**24**) rete neurale, nodo statistiche marginali<br /><br /> **DM_NODE_TYPE_REGRESSION_TREE_ROOT** (**25**)<br /><br /> **DM_NODE_TYPE_NB_MARGINAL_STAT_NODE** (**26**) rete neurale, nodo statistiche marginali|  
|**NODE_GUID**|**DBTYPE_GUID**||GUID del nodo. Questa colonna non è supportata da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**NODE_CAPTION**|**DBTYPE_WSTR**||Etichetta o didascalia associata al nodo. Questa proprietà viene utilizzata principalmente per scopi di visualizzazione.|  
|**CHILDREN_CARDINALITY**|**DBTYPE_UI4**||Stima del numero di nodi figlio del nodo.|  
|**PARENT_UNIQUE_NAME**|**DBTYPE_WSTR**||Nome univoco dell'elemento padre del nodo. **NULL** viene restituito per tutti i nodi a livello di radice.|  
|**NODE_DESCRIPTION**|**DBTYPE_WSTR**||Descrizione intuitiva del nodo.|  
|**NODE_RULE**|**DBTYPE_WSTR**||Descrizione XML della regola incorporata nel nodo.|  
|**MARGINAL_RULE**|**DBTYPE_WSTR**||Descrizione XML della regola passata al nodo dal nodo padre.|  
|**NODE_PROBABILITY**|**DBTYPE_R8**||Probabilità associata a questo nodo.|  
|**MARGINAL_PROBABILITY**|**DBTYPE_R8**||Probabilità di raggiungere il nodo dal nodo padre.|  
|**NODE_DISTRIBUTION**|**DBTYPE_HCHAPTER**||Tabella contenente l'istogramma delle probabilità del nodo.|  
|**NODE_SUPPORT**|**DBTYPE_R8**||Numero di case che supportano il nodo.|  
|**MSOLAP_MODEL_COLUMN**|**DBTYPE_WSTR**||Nome della colonna della definizione del modello relativa al nodo.|  
|**MSOLAP_NODE_SCORE**|**DBTYPE_R8**||Punteggio calcolato per il nodo.|  
|**MSOLAP_NODE_SHORT_CAPTION**|**DBTYPE_WSTR**||Didascalia breve per il nodo che può essere utilizzata per scopi di visualizzazione al fine di migliorare la leggibilità.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_MODEL_CONTENT** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**NODE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**NODE_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**NODE_TYPE**|**DBTYPE_I4**|Facoltativa.|  
|**NODE_GUID**|**DBTYPE_WSTR**|Facoltativa.|  
|**NODE_CAPTION**|**DBTYPE_WSTR**|Facoltativa.|  
|**TREE_OPERATION**|**DBTYPE_UI4**|Facoltativa. Vedere di seguito per osservazioni aggiuntive.|  
  
 La restrizione **TREE_OPERATION**, non si trova in qualsiasi colonna specifica del **DMSCHEMA_MINING_MODEL_CONTENT** set di righe; indica, invece, un operatore di albero. Il consumer può specificare un **NODE_UNIQUE_NAME** restrizione e l'operatore di albero (**PREDECESSORI**, **figli**, **elementi di pari livello**,  **PADRE**, **DISCENDENTI**, **SELF**) per ottenere il set di membri richiesto. Il **SELF** operatore include la riga per il nodo stesso nell'elenco di righe restituite. Nella tabella seguente vengono descritte le costanti che costituiscono la definizione di bitmap per il **TREE_OPERATION** restrizione. Possono essere combinati utilizzando l'operatore logico **o** operatore.  
  
|Costante|Value|  
|--------------|-----------|  
|**DMTREEOP_ANCESTORS**|**0x00000020**|  
|**DMTREEOP_CHILDREN**|**0x00000001**|  
|**DMTREEOP_SIBLINGS**|**0x00000002**|  
|**DMTREEOP_PARENT**|**0x00000004**|  
|**DMTREEOP_SELF**|**0x00000008**|  
|**DMTREEOP_DESCENDANTS**|**0x00000010**|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Data Mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
