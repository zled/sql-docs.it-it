---
title: Importazione di dati di Visual FoxPro in Microsoft Access | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6835c7ba9b4e1d2034b20e2e9945888f74bba60c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Importazione di dati di Visual FoxPro in Microsoft Access
È possibile importare i dati archiviati in un database di Visual FoxPro in un database di Microsoft Access utilizzando l'opzione di importazione.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Per importare i dati di Visual FoxPro in un database Microsoft Access  
  
1.  Aprire un database Microsoft Access.  
  
2.  Dal menu File, scegliere che quindi importare dati esterni.  
  
3.  Nella finestra di dialogo Importa, selezionare i file dell'elenco dei tipi di database ODBC.  
  
4.  Nella finestra di dialogo origini dati SQL, selezionare l'origine dati di Visual FoxPro che si connette ai dati FoxPro che si desidera eseguire una query e fare clic su OK.  
  
5.  Nella finestra di dialogo Importa oggetti, selezionare uno o più tabelle che si desidera importare e fare clic su OK. I nomi delle tabelle di Visual FoxPro importati vengono visualizzati nella scheda tabelle del database di Microsoft Access.  
  
 È ora possibile utilizzare Microsoft Access per modificare i dati nelle tabelle di Visual FoxPro importati. I dati che si importano sono uno snapshot dei dati archiviati in Visual FoxPro; le modifiche apportate ai dati importati non vengono inviate fino all'origine dati di Visual FoxPro.  
  
 Se si desidera che le modifiche apportate in Microsoft Access per modificare i dati nell'origine dei dati di Visual FoxPro, vedere [esecuzione di query e l'aggiornamento di Visual FoxPro dati da Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
