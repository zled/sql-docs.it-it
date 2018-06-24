---
title: Impostare l'analisi veloce | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 94f4fe123cb37e60e175ad39b932e61376e217b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063637"
---
# <a name="set-fast-parse"></a>Impostazione dell'analisi veloce
  È necessario impostare la proprietà relativa all'analisi veloce per ogni colonna dell'origine o della trasformazione in cui questa viene utilizzata. Per impostare la proprietà, utilizzare l'editor avanzato dell'origine file flat e della trasformazione Conversione dati.  
  
### <a name="to-set-fast-parse"></a>Per impostare l'analisi veloce  
  
1.  Fare clic con il pulsante destro del mouse sull'origine file flat o sulla trasformazione Conversione dati e quindi scegliere **Visualizza editor avanzato**.  
  
2.  Nella finestra di dialogo **Editor avanzato** fare clic sulla scheda **Proprietà input e output** .  
  
3.  Nel riquadro **Input e output** fare clic sulla colonna per la quale si desidera abilitare l'analisi veloce.  
  
4.  Nella finestra Proprietà espandere la **Custom Properties** nodo e quindi impostare il `FastParse` proprietà `True`.  
  
5.  Fare clic su **OK**.  
  
  