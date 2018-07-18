---
title: Attributi nelle gerarchie padre-figlio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data members [Analysis Services]
- nonleaf members
- MembersWithDataCaption property
- members [Analysis Services]
- members [Analysis Services], data
- leaf members
- parent-child dimensions [Analysis Services]
- MembersWithData property
ms.assetid: 249971cc-4bcd-44f1-8241-bdacc04d3d38
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bbf5919d44a4e36e1bdddaf5c34c5e3ab6aa4315
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220281"
---
# <a name="attributes-in-parent-child-hierarchies"></a>Attributi nelle gerarchie padre-figlio
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene in genere adottato un presupposto generale riguardo al contenuto dei membri di una dimensione. I membri foglia contengono dati derivati direttamente da origini dei dati sottostanti, mentre i membri non foglia contengono dati derivati da aggregazioni eseguite su membri figlio.  
  
 In una gerarchia padre-figlio, tuttavia, alcuni membri non foglia potrebbero includere dati derivati da origini dei dati sottostanti oltre ai dati aggregati da membri figlio. Per questi membri non foglia di una gerarchia padre-figlio vengono creati membri figlio speciali generati dal sistema contenenti i dati della tabella dei fatti sottostante. Questi membri, denominati *membri dei dati*, contengono un valore direttamente associato a un membro non foglia indipendente dal valore di riepilogo calcolato dai discendenti del membro non foglia.  
  
 I membri dei dati sono disponibili solo per le dimensioni con gerarchie padre-figlio e sono visibili solo se l'attributo padre lo consente. È possibile utilizzare Progettazione dimensioni per controllare la visibilità dei membri dei dati. Per esporre i membri dati, impostare il `MembersWithData` proprietà dell'attributo padre su `NonLeafDataVisible.` per nascondere i membri di dati contenuti nell'attributo padre, impostare il `MembersWithData` proprietà nell'attributo padre su `NonLeafDataHidden`.  
  
 Questa impostazione non altera la normale modalità di aggregazione dei membri non foglia in quanto il membro dei dati viene sempre incluso come membro figlio ai fini dell'aggregazione. È tuttavia possibile utilizzare una formula personalizzata di rollup per ignorare la normale modalità di aggregazione. Espressioni MDX (MDX) [DataMember](/sql/mdx/datamember-mdx) la funzione offre la possibilità di accedere al valore del membro dati associato indipendentemente dal valore della `MembersWithData` proprietà.  
  
 Il `MembersWithDataCaption` proprietà dell'attributo padre fornisce [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] con il modello di denominazione utilizzato per generare i nomi dei membri per i membri dati.  
  
## <a name="using-data-members"></a>Utilizzo dei membri dei dati  
 I membri dei dati sono utili durante l'aggregazione di misure in base a dimensioni organizzative con gerarchie padre-figlio. Ad esempio, nella figura seguente viene illustrata una dimensione con tre livelli, rappresentante il volume delle vendite lorde dei prodotti. Il primo livello indica il volume delle vendite lorde per tutti i rappresentanti. Il secondo livello include il volume delle vendite lorde per tutto il personale addetto alle vendite raggruppato in base al responsabile delle vendite e il terzo livello include il volume delle vendite lorde per tutto il personale addetto alle vendite raggruppato in base al rappresentante.  
  
 ![Dimensioni volume delle vendite lorde con tre livelli](../media/agdatamember1.gif "dimensione volume delle vendite lorde con tre livelli")  
  
 In genere, il valore del membro Sales Manager 1 verrebbe derivato dall'aggregazione dei valori dei membri Salesperson 1 e Salesperson 2. Tuttavia, poiché anche Sales Manager 1 può vendere prodotti, tale membro può inoltre includere dati derivati dalla tabella dei fatti, in quanto a Sales Manager 1 potrebbero essere associate vendite lorde.  
  
 Le commissioni individuali per ogni membro del personale addetto alle vendite, inoltre, possono essere diverse. In questo caso, vengono utilizzate due scale diverse per calcolare le commissioni per le vendite lorde individuali dei responsabili delle vendite rispetto alle vendite lorde totali generate dai rappresentanti. Pertanto, è importante poter accedere ai dati della tabella dei fatti sottostante per i membri non foglia. L'espressione MDX `DataMember` funzione può essere utilizzata per recuperare il volume di vendite lorde individuali del membro Sales Manager 1, e un'espressione di rollup personalizzato utilizzabile per escludere il membro dei dati dal valore aggregato del membro Sales Manager 1, che fornisce il gross volume delle vendite i rappresentanti associati al membro.  
  
## <a name="see-also"></a>Vedere anche  
 [Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md)   
 [Gerarchia padre-figlio](parent-child-dimension.md)  
  
  
