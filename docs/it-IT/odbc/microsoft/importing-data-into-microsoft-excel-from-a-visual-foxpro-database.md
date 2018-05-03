---
title: Importazione di dati in Microsoft Excel da un Database di Visual FoxPro | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa6da8abaca5b3b14c48bc4324a50301d5a36d87
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Importazione di dati in Microsoft Excel da un Database di Visual FoxPro
Se è stata definita un'origine dati per tale, è possibile importare dati di Visual FoxPro nel foglio di lavoro Microsoft Excel. Per informazioni sulla creazione di un'origine dati di Visual FoxPro, vedere [l'accesso a un'origine di dati Visual FoxPro da Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Per importare i dati di Visual FoxPro in un foglio di lavoro di Microsoft Excel  
  
1.  Aprire un foglio di calcolo di Microsoft Excel.  
  
2.  Nel menu di dati, scegliere Carica dati esterni. Verrà visualizzata la finestra di Query Microsoft.  
  
3.  Nella finestra di dialogo Seleziona origine dati, selezionare un'origine dati di Visual FoxPro e quindi fare clic su utilizza.  
  
4.  Se il database a cui accede l'origine dati include tabelle, selezionare una tabella nella finestra di dialogo Aggiungi tabelle. Microsoft Query Visualizza la tabella aggiunta nella parte superiore della finestra di Progettazione query.  
  
    > [!NOTE]  
    >  L'elenco dei proprietari non è disponibile in questa finestra di dialogo perché il driver non supporta i proprietari. L'elenco dei Database non è disponibile perché il driver non supporta più database in un'origine dati.  
  
5.  Selezionare i campi per la query tramite trascinamento dalla tabella nel minore della metà della finestra di progettazione.  
  
6.  Chiudere Microsoft Query. I dati selezionati vengono importati nel foglio di calcolo Microsoft Excel.
