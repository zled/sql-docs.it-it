---
title: Finestra di dialogo Parametri query (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3e99a38d3b9c06257f4f5202a3142292409d29e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069525"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Finestra di dialogo Parametri query (Visual Database Tools)
  Questa finestra di dialogo consente di immettere valori per i parametri definiti nella query. Viene visualizzata quando si esegue una query contenente parametri che richiedono la presenza dell'utente finale in fase di esecuzione.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Elenca i parametri definiti per la query eseguita. Se la query contiene parametri denominati, i nomi vengono visualizzati nell'elenco. Se nella query sono contenuti parametri senza nome, per ogni parametro della query verranno elencati i nomi di parametro definiti dal sistema.  
  
 **Value**  
 Immettere il valore per ogni parametro elencato in **Nome**. Il valore utilizzato per ultimo viene visualizzato come valore del parametro predefinito.  
  
## <a name="example"></a>Esempio  
 La query del riquadro SQL riportata di seguito consente di aprire la finestra di dialogo Parametri query quando viene eseguita nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di query con parametri &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  