---
title: Riferimento alle librerie ADO In un'applicazione Visual Basic 6 | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology: drivers
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual Basic application[ADO]
- ADO, libraries
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 745e305dc6b513a22bce48b40f511a850386e1b4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Riferimento alle librerie ADO In un'applicazione Visual Basic 6
Per importare le librerie di ADO in un'applicazione di Microsoft Visual Basic 6, è necessario impostare un riferimento nel progetto di Visual Basic.  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>Per impostare un riferimento alla libreria ADO in un progetto di Visual Basic  
  
1.  Creare un nuovo o aprire un progetto di Visual Basic esistente.  
  
2.  Fare clic su di **progetto** voce di menu e quindi selezionare **riferimenti...**  dal Pannello di menu a discesa.  
  
3.  Da **riferimenti disponibili**, selezionare la casella per **Microsoft ActiveX Data Objects *n* libreria**, dove ***n*** rappresenta la versione più recente numero di versione. Il **percorso** campo sottostante è necessario identificare la scelta come *$installDir\msado15.dll*, dove *$installDir* rappresenta il percorso della directory in cui la libreria ADO è stato installato.  
  
4.  Se si prevede di utilizzare ADO MD, ripetere il passaggio 3 per selezionare **Microsoft ActiveX Data Objects (multidimensionali) *n* libreria**. Il **percorso** campo dovrebbe identificare questa scelta come *$installDir\msadomd.dll*.  
  
5.  Se si prevede di utilizzare ADOX, ripetere il passaggio 3 per selezionare **Microsoft ADO ext *n* per la sicurezza e DDL**. Il **percorso** campo dovrebbe identificare questa scelta come *$installDir\msadox.dll*.  
  
6.  Fare clic su **OK** per completare l'impostazione dei riferimenti.  
  
## <a name="backward-compatibility"></a>Compatibilità con le versioni precedenti  
 Installazione di ADO copia anche le librerie dei tipi seguenti di versioni precedenti:  
  
-   *msado27.tlb*, libreria dei tipi 2.7 ADO  
  
-   *msado26.tlb*, ADO 2.6 libreria  
  
-   *msado25.tlb*, libreria dei tipi 2,5 ADO  
  
-   *Msado21*, libreria dei tipi 2.1 ADO  
  
-   *msado20.tlb*, ADO libreria dei tipi 2.0  
  
 Se l'applicazione deve usare uno qualsiasi di queste librerie di ADO per motivi di compatibilità con le versioni precedenti, è necessario importare la versione appropriata della libreria dei tipi. A tale scopo, seguire le procedure nella sezione precedente, sostituendo *msado15.dll* da *msadoXX.tlb*, dove *XX* rappresenta il numero di versione è necessario importare.
