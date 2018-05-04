---
title: Risoluzione dei problemi, Driver ODBC di Visual FoxPro | Documenti Microsoft
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
- set ANSI [ODBC]
- troubleshooting Visual FoxPro ODBC driver [ODBC]
- remote views [ODBC]
- multitiered views [ODBC]
- parameterized views [ODBC], Visual FoxPro ODBC driver
- fetches [ODBC], Visual FoxPro ODBC driver
- positioned updates [ODBC]
- background fetching [ODBC]
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd8f7c5a071d13b71a1c61ce6f7b328174cb2a8a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>Risoluzione dei problemi (Driver ODBC di Visual FoxPro)
Le sezioni seguenti illustrano come migliorare le prestazioni e risolvere i problemi che possono verificarsi quando si utilizza il Driver ODBC di Visual FoxPro.  
  
## <a name="accessing-parameterized-views"></a>L'accesso a viste con parametri  
 È possibile accedere alle viste con parametri in un database di Visual FoxPro usando il driver. Una vista con parametri consente di creare una clausola WHERE della vista SQL **selezionare** scaricato istruzione che limita i record a quei record che soddisfano le condizioni della clausola WHERE creata usando il valore fornito per il parametro. Poiché il driver non supporta i parametri di passaggio alla visualizzazione, i tentativi di accedere a una vista con parametri utilizzando il driver avrà esito negativo.  
  
 Il valore del parametro può essere fornito in fase di esecuzione o a livello di codice passato alla visualizzazione.  
  
## <a name="accessing-remote-views"></a>L'accesso Remote viste  
 È possibile accedere alle viste remote in un database di Visual FoxPro usando il driver. Visualizzazioni remote sono che accedono a dati non FoxPro o una combinazione di FoxPro e dati non FoxPro. Per accedere alle viste remote, utilizzare Visual FoxPro.  
  
## <a name="deleting-records"></a>Eliminazione di record  
 È possibile contrassegnare i record per l'eliminazione tramite il driver, ma non è possibile rimuovere definitivamente i record dal database. Per rimuovere definitivamente i record da una tabella, utilizzare Visual FoxPro.  
  
## <a name="increasing-performance-using-background-fetching"></a>Miglioramento delle prestazioni tramite il recupero in Background  
 È possibile migliorare le prestazioni in recuperi di grandi dimensioni tramite lo sfondo del recupero di funzionalità del driver. Recupero in background utilizza un thread separato per recuperare i dati richiesti da un'origine dati specifica.  
  
 È possibile applicare background recupero per un'origine dati in uno dei modi seguenti:  
  
-   Controllare il **recuperare i dati in background** casella di controllo di [la finestra di dialogo di installazione di ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md).  
  
-   Utilizzare la parola chiave attributo BackgroundFetch nella stringa di connessione.  
  
 Per informazioni sulle parole chiave di attributo stringa di connessione, vedere [utilizzando le stringhe di connessione](../../odbc/microsoft/using-connection-strings.md).  
  
## <a name="updating-multitiered-views"></a>Aggiornamento delle visualizzazioni a più livelli  
 Una vista più livelli è una vista basata su una o più visualizzazioni anziché su una tabella di base. Quando si aggiornano i dati in una visualizzazione di più livelli, gli aggiornamenti anche un solo livello, la vista su cui è basata la vista di primo livello; tabelle di base non vengono aggiornate.  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>Utilizzo di Data Definition Language (DDL) in Stored procedure  
 DDL, ad esempio CREATE TABLE o ALTER TABLE, è possibile utilizzare nelle routine di Visual FoxPro archiviati.  
  
 Per informazioni sul linguaggio, è possibile utilizzare nelle stored procedure, vedere [il supporto per le regole, valori predefiniti, trigger e Stored procedure](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md).  
  
## <a name="using-positioned-updates"></a>Usando gli aggiornamenti posizionati  
 Il driver non supporta gli aggiornamenti posizionati. Utilizzare la clausola SQL WHERE per identificare le righe che si desidera aggiornare.  
  
## <a name="using-the-set-ansi-command"></a>Il comando SET ANSI  
 Se si è uno sviluppatore di Visual FoxPro, è necessario tenere presente che l'impostazione predefinita per SET ANSI è impostata su ON per il driver, a differenza di un'impostazione OFF per Visual FoxPro. Il valore predefinito di impostazione per SET ANSI consente origini dati di Visual FoxPro da un comportamento coerente con altre origini dati ODBC che in genere eseguono confronti esatto. È possibile modificare l'impostazione predefinita. Per ulteriori informazioni, vedere [SET ANSI](../../odbc/microsoft/set-ansi-command.md).
