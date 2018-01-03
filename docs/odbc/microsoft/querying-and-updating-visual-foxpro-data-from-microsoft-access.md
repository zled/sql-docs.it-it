---
title: Esecuzione di query e aggiornamento dei dati di Visual FoxPro da Microsoft Access | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34383ecfbfae7c037137296942ba392ddb50db63
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Esecuzione di query e aggiornamento dei dati di Visual FoxPro da Microsoft Access
È possibile eseguire una query e aggiornare i dati archiviati in un database di Visual FoxPro da un database Microsoft Access utilizzando l'opzione di tabella di collegamento.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Per collegare un database di Visual FoxPro a un database Microsoft Access  
  
1.  Aprire un database Microsoft Access.  
  
2.  Nella scheda tabelle, fare clic su nuovo.  
  
3.  Nella finestra di dialogo nuova tabella, selezionare la tabella di collegamento e fare clic su OK.  
  
4.  Nella finestra di dialogo di collegamento, selezionare il Database di ODBC nei file dell'elenco dei tipi.  
  
5.  Nella finestra di dialogo origini dati SQL, selezionare l'origine dati che si connette ai dati di Visual FoxPro che si desidera eseguire una query e fare clic su OK.  
  
6.  Nella finestra di dialogo Collega tabelle, selezionare le tabelle che si desidera eseguire una query e aggiornare e fare clic su OK. Le tabelle di Visual FoxPro collegate vengono visualizzate nella scheda tabelle del database di Microsoft Access.  
  
 È ora possibile utilizzare Microsoft Access per eseguire query e aggiornare i dati nelle tabelle di Visual FoxPro collegate. Le modifiche apportate ai dati collegati vengono inviate all'origine dati di Visual FoxPro.  
  
 Se si desidera che le modifiche apportate in Microsoft Access influisce sui dati nell'origine dei dati di Visual FoxPro, vedere [l'importazione di dati Visual FoxPro in Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
