---
title: Aggiunta di un'origine dati di Visual FoxPro | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data source [ODBC], adding
- adding data sources [ODBC], Visual FoxPro ODBC driver
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bb3c905283e52d353f53c3daeb3ce1cebe65562
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899048"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Aggiunta di un'origine dati di Visual FoxPro
Per accedere a dati di Visual FoxPro dall'applicazione, è necessario disporre di un'origine dati. È possibile creare un'origine dati, come indicato di seguito:  
  
-   In un'applicazione, ad esempio Microsoft® Word, Microsoft Excel o Microsoft Access, che utilizza il driver ODBC.  
  
-   Di fuori dell'applicazione, utilizzando il pannello di controllo di Microsoft Windows e Windows 2000, Microsoft Windows® 95 o Microsoft Windows 98.  
  
 Dopo un'origine dati esistente nel sistema, è possibile riutilizzare la stessa origine dati ogni volta che si desidera accedere ai dati di Visual FoxPro. Se si dispone di più database diversi o tabelle che si desidera accedere, è possibile creare un'origine dati separata per ogni database o una directory.  
  
 La procedura seguente crea un'origine dati tramite Pannello di controllo. Per ulteriori informazioni su come creare un'origine dati da un'applicazione, vedere [l'accesso a Visual FoxPro dati da Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Per aggiungere un'origine dati di Visual FoxPro  
  
1.  Nei computer che eseguono Windows 2000, aprire il pannello di controllo di Windows e fare doppio clic su strumenti di amministrazione.  
  
2.  Fare doppio clic su origini dati (ODBC) per aprire la finestra di dialogo Amministratore origine dati ODBC. Questa icona è disponibile dopo aver installato il Driver ODBC di Visual FoxPro o qualsiasi software dei driver ODBC.  
  
    > [!NOTE]  
    >  Se si esegue una versione precedente di Windows, aprire il pannello di controllo di Windows e fare doppio clic su 32 bit ODBC o ODBC per aprire la finestra di dialogo Amministratore origine dati ODBC.  
  
3.  Fare clic su Aggiungi.  
  
4.  Nella finestra di dialogo Crea nuova origine dati, selezionare Microsoft Visual FoxPro Driver e quindi fare clic su Fine.  
  
5.  Nel [la finestra di dialogo di installazione di ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md), digitare il nome dell'origine dati e la descrizione, selezionare il tipo di database, selezionare il database o la directory e quindi fare clic su OK.  
  
     Il nome della nuova origine dati viene visualizzato nell'elenco di origini dati utente nella scheda DSN utente della finestra di dialogo Amministratore origine dati ODBC.  
  
6.  Fare clic su OK per salvare la nuova origine dati e chiudere la finestra di dialogo Amministratore origine dati ODBC.
