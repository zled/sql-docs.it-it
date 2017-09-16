---
title: 'HelloData: Una semplice applicazione ADO | Documenti Microsoft'
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HelloData sample application [ADO]
- ADO, samples
ms.assetid: de4bcd56-dac2-45e6-95ab-9fd7f25878fc
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a1c7d61c6349945274febc92e4e6b5acfcc379b9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="hellodata-a-simple-ado-application"></a>HelloData: Una semplice applicazione ADO
Questa semplice applicazione passaggi per ognuna delle quattro operazioni ADO principali: recupero, esame, la modifica e aggiornamento dei dati. Queste operazioni vengono eseguite sul database di esempio Northwind incluso in Microsoft® SQL Server. Per concentrarsi sui fondamenti di ADO e per evitare confusione codice, gestione degli errori nell'esempio è minimo.  
  
### <a name="to-run-hellodata"></a>Per eseguire HelloData  
  
1.  Creare un nuovo progetto Standard EXE Visual Basic che fa riferimento alla libreria ADO. Per ulteriori informazioni, vedere [riferimenti alle librerie ADO](../../../ado/guide/referencing-the-ado-libraries.md).  
  
2.  Creare quattro pulsanti di comando nella parte superiore del form, l'impostazione di **nome** e **didascalia** proprietà sui valori indicati nella tabella alla fine di questo argomento.  
  
3.  Sotto i pulsanti, aggiungere un **controllo DataGrid Microsoft** (Msdatgrd). Il file Msdatgrd è incluso con Visual Basic e si trova nella cartella \windows\system32 o \Winnt\System32. Per aggiungere il controllo DataGrid al riquadro casella degli strumenti di Visual Basic, selezionare **componenti...** dal **progetto** menu. Quindi selezionare la casella accanto a "Microsoft controllo DataGrid 6.0 (SP3) (OLEDB)" e quindi fare clic su **OK**. Per aggiungere il controllo al progetto, trascinare il controllo DataGrid dalla casella degli strumenti al form Visual Basic.  
  
4.  Creare un **TextBox** nel form sotto la griglia e impostarne le proprietà, come illustrato nella tabella. Il modulo dovrebbe essere simile nella figura seguente, dopo aver terminato.  
  
5.  Infine, copiare il codice riportato nella [codice HelloData](../../../ado/guide/data/hellodata-code.md)e incollarlo nella finestra dell'editor di codice del form. Premere **F5** per eseguire il codice.  
  
> [!NOTE]
>  Nell'esempio seguente e nella Guida, l'id utente "MyId" con una password "123aBc" viene utilizzato per autenticare il server. È necessario sostituire questi valori con le credenziali di accesso valido per il server. Inoltre, sostituire il valore "MySQLServer" con il nome del server.  
  
 Per una descrizione dettagliata del codice, vedere [commenti sul HelloData](../../../ado/guide/data/comments-on-hellodata.md).  
  
 ![Mostra Form1 per l'applicazione VB HelloData](../../../ado/guide/data/media/hellodata.gif "HelloData")  
  
|Tipo di controllo|Proprietà|Valore|  
|------------------|--------------|-----------|  
|Form|Nome|Form1|  
||Altezza|6500|  
||Larghezza|6500|  
|DataGrid MS|Nome|grdDisplay1|  
|TextBox|Nome|txtDisplay1|  
||Su più righe|true|  
|Pulsante di comando|Nome|cmdGetData|  
||Caption|Get Data|  
|Pulsante di comando|Nome|cmdExamineData|  
||Caption|Esaminare i dati|  
|Pulsante di comando|Nome|cmdEditData|  
||Caption|Modificare i dati|  
|Pulsante di comando|Nome|cmdUpdateData|  
||Caption|Dati di aggiornamento|
