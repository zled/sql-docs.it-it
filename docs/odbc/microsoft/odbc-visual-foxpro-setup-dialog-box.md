---
title: La finestra di dialogo programma di installazione di Visual FoxPro ODBC | Documenti Microsoft
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
- installing Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], installing
- FoxPro ODBC driver [ODBC], installing
ms.assetid: de020197-7f53-4643-9cbf-b7887ba88de9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e891cbbdfdf77c49262ca21263a7f5b248a70c27
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904616"
---
# <a name="odbc-visual-foxpro-setup-dialog-box"></a>La finestra di dialogo programma di installazione di Visual FoxPro ODBC
Il **installazione ODBC Visual FoxPro** la finestra di dialogo consente di aggiungere o modificare un'origine dati di Visual FoxPro.  
  
 Per scaricare il driver, vedere [il sito di download del Driver ODBC Visual FoxPro](http://go.microsoft.com/fwlink/?LinkId=121318).  
  
## <a name="dialog-box-options"></a>Finestre di dialogo  
 **Nome dell'origine dati**  
 Digitare il nome che si desidera utilizzare per l'origine dati.  
  
 **Description**  
 Digitare una descrizione per l'origine dati.  
  
 **Tipo di database**  
 Consente di scegliere il tipo di database che si desidera l'origine dati a cui connettersi.  
  
 **Database di Visual FoxPro (. DBC)**  
 Specifica che l'origine dati si connette a un Visual FoxPro [database](../../odbc/microsoft/visual-foxpro-terminology.md) (file DBC) e per tutte le tabelle e viste del database locale.  
  
 **Directory di tabella disponibili**  
 Specifica che l'origine dati si connette a una directory di [libero tabelle](../../odbc/microsoft/visual-foxpro-terminology.md). Qualsiasi [database](../../odbc/microsoft/visual-foxpro-terminology.md) tabelle nella stessa directory vengono ignorate da funzioni di catalogo ODBC, ad esempio [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) o [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md). Tabelle di database è possibile accedere tramite istruzioni SQL SELECT inviate tramite [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) e [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
 **Percorso**  
 Visualizza il percorso e il nome per il database o la directory di tabelle disponibile a cui si connette l'origine dati.  
  
 **Sfoglia**  
 Consente di cercare il sistema e la rete per il database o una directory a cui si desidera connettersi all'origine dati.  
  
 **Opzioni**  
 Espande la finestra di dialogo in modo che è possibile impostare le opzioni di Visual FoxPro ODBC Driver.  
  
## <a name="driver"></a>Driver  
 **Sequenza di confronto**  
 La sequenza nella quale vengono ordinati i campi. Le sequenze predefinite riflettono le sequenze supportate dalla versione del linguaggio del sistema operativo. Per un elenco di sequenze di confronto supportate, vedere [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
 **Exclusive**  
 Quando questa casella di controllo è selezionata, il driver apre il database di Visual FoxPro esclusivamente quando si accede ai dati utilizzando l'origine dati. Altri utenti non possono accedere al database o le tabelle nel database, mentre il database è aperto in modalità esclusiva. Tabelle di database aperto esclusivamente vengono aperti come condiviso. Per aprire una tabella in modo esclusivo, utilizzare il [SET esclusivo](../../odbc/microsoft/set-exclusive-command.md) comando. Questa casella di controllo è disabilitata quando **tipo di Database** è impostato su **directory tabella libera**.  
  
 **Null**  
 Determina se le colonne create con l'istruzione ALTER TABLE e CREATE TABLE consentono valori null. Se è impostata su ON Null, Inserisci – SQL inserisce un valore null in qualsiasi colonna non inclusa in un'istruzione INSERT-SQL... Clausola VALUE. Se Null è impostata su OFF, viene inserito un valore vuoto. È inoltre possibile controllare questa opzione in una stringa di connessione passata come illustrato nel codice seguente:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;NULL=NO"  
```  
  
 **eliminato**  
 Determina se vengono restituite righe contrassegnate come eliminate. È inoltre possibile controllare questa opzione in una stringa di connessione passata come illustrato nel codice seguente:  
  
```  
strCon = "DRIVER=MICROSOFT VISUAL FOXPRO DRIVER;  
SOURCETYPE=DBC;SOURCEDB=D:\Testdata.dbc;BACKGROUNDFETCH=NO;  
DELETED=YES"  
```  
  
 **Recuperare i dati in background**  
 Determina se verranno recuperati i record in background (recupero progressivo) o l'applicazione rimarrà in attesa finché vengono recuperati tutti i record nel set di risultati.
