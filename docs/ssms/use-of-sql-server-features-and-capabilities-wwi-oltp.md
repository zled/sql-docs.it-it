---
title: Argomenti per gli strumenti esterni | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arguments [SQL Server Management Studio]
- external tools [SQL Server Management Studio]
ms.assetid: 3991c13a-f23f-450b-a2ba-19391c399735
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 514b5f4e9e5df63f745e7f2e6a9465cddd6c4628
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="arguments-for-external-tools"></a>Strumenti esterni - Argomenti
Gli argomenti sono variabili per le quali l'ambiente Visual Studio specifica dei valori quando viene avviato uno strumento esterno dal menu **Strumenti**. Al menu **Strumenti** è possibile aggiungere strumenti esterni, come il Blocco note, usando la finestra di dialogo **Strumenti esterni**.  
  
Nella tabella seguente vengono elencati gli argomenti per gli strumenti esterni.  
  
|Nome|Argomento|Description|  
|--------|------------|---------------|  
|**Percorso elemento**|$(ItemPath)|Il nome file completo dell'origine corrente (definito come unità + percorso + nome file); vuoto se è attiva una finestra non di origine.|  
|**Directory elemento**|$(ItemDir)|La directory dell'origine corrente (definita come unità + percorso); vuoto se è attiva una finestra non di origine.|  
|**Nome file elemento**|$(ItemFilename)|Il nome file dell'origine corrente (definito come nome file); vuoto se è attiva una finestra non di origine.|  
|**Estensione elemento**|$(ItemExt)|L'estensione del nome file dell'origine corrente.|  
|**Riga corrente***|$(CurLine)|La posizione di riga corrente del cursore nell'editor.|  
|**Colonna corrente***|$(CurCol)|La posizione di colonna corrente del cursore nell'editor.|  
|**Testo corrente***|$(CurText)|Il testo corrente (la parola sotto la posizione corrente del cursore o selezione di una riga singola, se presente).|  
|**Percorso di destinazione**|$(TargetPath)|Il nome file completo della destinazione (definito come unità + percorso + nome file).|  
|**Directory di destinazione**|$(TargetDir)|La directory della destinazione.|  
|**Nome destinazione**|$(TargetName)|Il nome file della destinazione.|  
|**Estensione di destinazione**|$(TargetExt)|L'estensione del nome file della destinazione.|  
|**Directory progetto**|$(ProjDir)|La directory del progetto corrente (definita come unità + percorso).|  
|**Nome file progetto**|$(ProjFileName)|Il nome file del progetto corrente (definito come unità + percorso + nome file).|  
|**Directory soluzione**|$(SolutionDir)|La directory della soluzione corrente (definita come unità + percorso).|  
|**Nome file soluzione**|$(SolutionFileName)|Il nome file della soluzione corrente (definito come unità + percorso + nome file).|  
  
*La riga, la colonna o il testo corrente dipendono dalla posizione del cursore nell'editor di testo, come indicato nella barra di stato.  
  
## <a name="see-also"></a>Vedere anche  
[Finestra di dialogo Strumenti esterni](../ssms/external-tools-dialog-box.md)  
[Elementi generali dell'interfaccia utente](../ssms/general-user-interface-elements.md)  
  

