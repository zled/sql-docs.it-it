---
title: Creazione di etichette in Microsoft Word utilizzando i dati di Visual FoxPro | Documenti Microsoft
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
- Visual FoxPro data [ODBC], mailing labels
- Visual FoxPro data [ODBC], Word
- mailing labels [ODBC]
- Visual FoxPro ODBC driver [ODBC], Word
- FoxPro ODBC driver [ODBC], word
ms.assetid: c901b60c-9f84-407a-b3d1-b4d301a71370
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 54c7d1445f6592a496f7e0d3c7b47e017595d6e1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="creating-mailing-labels-in-microsoft-word-using-visual-foxpro-data"></a>Creazione di etichette in Microsoft Word utilizzando i dati di Visual FoxPro
È possibile utilizzare i dati di Visual FoxPro in un Microsoft Word per Windows 95 o Windows 98 documento. Potrebbe ad esempio, si desidera creare etichette dalle informazioni del cliente archiviate in una tabella di Visual FoxPro.  
  
### <a name="to-create-mailing-labels"></a>Per creare etichette  
  
1.  In Microsoft Word, creare un nuovo documento vuoto.  
  
2.  Dal menu Strumenti, scegliere l'unione.  
  
3.  Nell'Helper della stampa unione, scegliere Crea e quindi selezionare etichette.  
  
4.  Nella sezione principale del documento, scegliere finestra attiva.  
  
5.  In origine dati, scegliere Recupera dati, quindi selezionare Apri origine dati.  
  
6.  Nella finestra di dialogo Apri origine dati, scegliere MS Query.  
  
7.  Nella finestra di dialogo Seleziona origine dati, selezionare un'origine dati di Visual FoxPro e quindi fare clic su utilizza.  
  
8.  Se il database a cui accede l'origine dati include tabelle, selezionare una tabella nella finestra di dialogo Aggiungi tabelle. Microsoft Query Visualizza la tabella aggiunta nella parte superiore della finestra di Progettazione query.  
  
9. Selezionare i campi per la query tramite trascinamento dalla tabella nel minore della metà della finestra di progettazione.  
  
10. Dal menu File, scegliere i dati restituiti in Microsoft Word. Chiude Microsoft Query e i dati selezionati sono disponibili per l'uso del documento di unione.  
  
11. Nella sezione principale del documento, scegliere il programma di installazione.  
  
12. Nella finestra di dialogo Opzioni di etichetta, selezionare le informazioni della stampante e l'etichetta è desiderato e quindi fare clic su OK.  
  
13. Nella finestra di dialogo Crea etichette, selezionare i campi che si desidera stampare nelle etichette indirizzi e quindi fare clic su OK.  
  
14. Nell'Helper della stampa unione, l'unione dei dati con il documento, fare clic su Merge.  
  
15. Nella finestra di dialogo unione, selezionare le opzioni desiderato e quindi fare clic su Merge.
