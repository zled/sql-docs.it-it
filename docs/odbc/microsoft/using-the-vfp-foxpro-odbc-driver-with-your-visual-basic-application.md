---
title: Utilizzare il Driver ODBC di FoxPro VFP con l'applicazione Visual Basic | Documenti Microsoft
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
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 96107d42ae4923cd1b9f7ad1c16bd492d0203c99
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Utilizza il Driver ODBC di FoxPro VFP con l'applicazione Visual Basic
Applicazione di Microsoft® Visual Basic® può comunicare con i dati di Visual FoxPro mediante la creazione di un controllo dati che si connette a un'origine dati di Visual FoxPro.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Per connettersi ai dati di Visual FoxPro utilizzando il controllo dei dati in Visual Basic  
  
1.  Creare un'origine dati denominata "test" che si connette al database di esempio TasTrade incluso in Visual FoxPro. L'installazione di Visual FoxPro predefinita, il database di esempio TasTrade nel percorso:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  In Visual Basic, creare un nuovo modulo e inserire una casella di testo e un controllo dati su di esso.  
  
3.  Modifica proprietà di connessione del controllo dati come segue:  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Modificare la proprietà RecordsetType nel modo seguente:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Modificare la proprietà di origine record come segue:  
  
    ```  
    customer  
    ```  
  
6.  Modificare la proprietà DataSource per la casella di testo per il nome predefinito per il controllo di dati per le operazioni seguenti:  
  
    ```  
    data1  
    ```  
  
7.  Modificare proprietà DataField della casella di testo nel modo seguente:  
  
    ```  
    customer_id  
    ```  
  
8.  Eseguire il modulo e usare il controllo dei dati per scorrere i campi id cliente dal database di esempio di Visual FoxPro TasTrade.
