---
title: 'Attività 7: Creazione di un dominio composito | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e88fa44fb4457a979dfa1236531ed8bfa61f88fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167546"
---
# <a name="task-7-creating-a-composite-domain"></a>Attività 7: Creazione di una regola per un dominio composito
  In questa attività, si crea un dominio composito **Address Validation**, che comprende **Address Line**, **Città**, **stato**e  **Codice postale** domini. Un dominio composito consente di definire una regola tra domini che interessa più domini di una regola. Vi sono altri vantaggi correlati a un dominio composito, quale la possibilità di analizzare un valore di campo in più domini.  Ad esempio, un valore per un campo Nome completo può essere analizzato in domini diversi First Name, Middle Name e Last Name. In questa esercitazione viene definita solo una regola tra domini. Vedere [Managing a Composite Domain](http://msdn.microsoft.com/library/hh510399.aspx) per altri dettagli.  
  
1.  Nel riquadro sinistro, fare clic su **creare un dominio composito** pulsante sulla barra degli strumenti.  
  
     ![Creare un pulsante della barra degli strumenti dominio composito](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "creare un pulsante della barra degli strumenti dominio composito")  
  
2.  Immettere **indirizzo convalida** per il **nome dominio composito**.  
  
     ![Risolvere la convalida dominio composito](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "indirizzo dominio composito di convalida")  
  
3.  Dall'elenco di domini selezionare **Address Line**, **Città**, **stato**, e **codice postale** e fare clic su **freccia destra** per l'aggiunta di **domini nel dominio composito** elenco.  
  
4.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 8: Creazione di una regola dominio composito](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  