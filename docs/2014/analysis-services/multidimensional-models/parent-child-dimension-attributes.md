---
title: Gli attributi in gerarchie padre-figlio | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 26e8af7c0709faa813b1b4c85345858abe5fc520
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069925"
---
# <a name="attributes-in-parent-child-hierarchies"></a>Attributi nelle gerarchie padre-figlio
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene in genere adottato un presupposto generale riguardo al contenuto dei membri di una dimensione. I membri foglia contengono dati derivati direttamente da origini dei dati sottostanti, mentre i membri non foglia contengono dati derivati da aggregazioni eseguite su membri figlio.  
  
 In una gerarchia padre-figlio, tuttavia, alcuni membri non foglia potrebbero includere dati derivati da origini dei dati sottostanti oltre ai dati aggregati da membri figlio. Per questi membri non foglia di una gerarchia padre-figlio vengono creati membri figlio speciali generati dal sistema contenenti i dati della tabella dei fatti sottostante. Questi membri, denominati *membri dei dati*, contengono un valore direttamente associato a un membro non foglia indipendente dal valore di riepilogo calcolato dai discendenti del membro non foglia.  
  
 I membri dei dati sono disponibili solo per le dimensioni con gerarchie padre-figlio e sono visibili solo se l'attributo padre lo consente. È possibile utilizzare Progettazione dimensioni per controllare la visibilità dei membri dei dati. Per esporre i membri di dati, impostare il `MembersWithData` proprietà dell'attributo padre a `NonLeafDataVisible.` per nascondere i membri di dati contenuti nell'attributo padre, impostare il `MembersWithData` proprietà dell'attributo padre in `NonLeafDataHidden`.  
  
 Questa impostazione non altera la normale modalità di aggregazione dei membri non foglia in quanto il membro dei dati viene sempre incluso come membro figlio ai fini dell'aggregazione. È tuttavia possibile utilizzare una formula personalizzata di rollup per ignorare la normale modalità di aggregazione. Il MDX (Multidimensional Expressions) [DataMember](/sql/mdx/datamember-mdx) funzione offre la possibilità di accedere al valore del membro dati associato indipendentemente dal valore della `MembersWithData` proprietà.  
  
 Il `MembersWithDataCaption` proprietà dell'attributo padre fornisce [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] con il modello di denominazione utilizzato per generare i nomi dei membri per i membri di dati.  
  
## <a name="using-data-members"></a>Utilizzo dei membri dei dati  
 I membri dei dati sono utili durante l'aggregazione di misure in base a dimensioni organizzative con gerarchie padre-figlio. Ad esempio, nella figura seguente viene illustrata una dimensione con tre livelli, rappresentante il volume delle vendite lorde dei prodotti. Il primo livello indica il volume delle vendite lorde per tutti i rappresentanti. Il secondo livello include il volume delle vendite lorde per tutto il personale addetto alle vendite raggruppato in base al responsabile delle vendite e il terzo livello include il volume delle vendite lorde per tutto il personale addetto alle vendite raggruppato in base al rappresentante.  
  
 ![Dimensioni volume delle vendite lorde con tre livelli](../media/agdatamember1.gif "dimensione volume delle vendite lorde con tre livelli")  
  
 In genere, il valore del membro Sales Manager 1 verrebbe derivato dall'aggregazione dei valori dei membri Salesperson 1 e Salesperson 2. Tuttavia, poiché anche Sales Manager 1 può vendere prodotti, tale membro può inoltre includere dati derivati dalla tabella dei fatti, in quanto a Sales Manager 1 potrebbero essere associate vendite lorde.  
  
 Le commissioni individuali per ogni membro del personale addetto alle vendite, inoltre, possono essere diverse. In questo caso, vengono utilizzate due scale diverse per calcolare le commissioni per le vendite lorde individuali dei responsabili delle vendite rispetto alle vendite lorde totali generate dai rappresentanti. Pertanto, è importante poter accedere ai dati della tabella dei fatti sottostante per i membri non foglia. MDX `DataMember` funzione può essere utilizzata per recuperare il volume delle vendite lorde individuale del membro Sales Manager 1, e un'espressione di rollup personalizzato consente di escludere il membro dei dati dal valore aggregato del membro Sales Manager 1, che fornisce il lordo volume delle vendite dei venditori associati a tale membro.  
  
## <a name="see-also"></a>Vedere anche  
 [Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md)   
 [Gerarchia padre-figlio](parent-child-dimension.md)  
  
  
