---
title: Introduzione a SSMA per MySQL Console (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
caps.latest.revision: 23
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0b41087aeaa65c87269a34f3208a4b63d91971e7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Introduzione a SSMA per MySQL Console (MySQLToSQL)
In questa sezione viene descritta la procedura per avviare e iniziare a usare l'applicazione console MySQL. Elencati, anche nel presente documento, vengono usate le convenzioni in una finestra di output della Console di SSMA tipico.  
  
## <a name="launching-ssma-console"></a>Avviare la Console di SSMA  
Utilizzare la procedura seguente per avviare l'applicazione console SSMA:  
  
1.  Passare a **avviare** e scegliere **tutti i programmi**.  
  
2.  Fare clic su di **SQL Server Migration Assistant per MySQL Prompt dei comandi** scelta rapida.  
  
    Viene visualizzato il menu di utilizzo della Console di SSMA e `(/? Help)`, che consentono di iniziare a utilizzare l'applicazione console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procedura per utilizzare la Console SSMA  
Dopo la console viene avviata correttamente nel sistema Windows, è possibile utilizzare la procedura seguente per lavorare su di esso:  
  
1.  Configurare la Console di SSMA tramite i file di script. Per ulteriori informazioni su questa sezione, vedere [creazione di file di Script &#40; MySQLToSQL &#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md) .  
  
2.  [Creazione di valore della variabile file &#40; MySQLToSQL &#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [Creare i file di connessione del Server &#40; MySQLToSQL &#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [L'esecuzione la Console SSMA &#40; MySQLToSQL &#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) in base alle esigenze del progetto  
  
Altre funzionalità:  
  
1.  [Protezione delle Password](http://msdn.microsoft.com/en-us/4ffbc587-ea3f-49ad-bc42-a654f672325e) e l'esportazione / importazione in altri computer della finestra  
  
2.  [Generare report](http://msdn.microsoft.com/en-us/1c0202e8-546d-4cb3-a37f-1d2e35d53839) per visualizzare il codice xml dettagliate l'output di report per la migrazione di dati e /conversion di valutazione. I report di errore dettagliato possono essere generati anche per i comandi di aggiornamento e la sincronizzazione.  
  
## <a name="ssma-console-output-conventions"></a>Convenzioni di Output di Console SSMA  
Durante l'esecuzione di comandi script SSMA e le opzioni, il programma di console consente di visualizzare i risultati e messaggi (le informazioni, errore e così via) per l'utente nella console o se necessario, reindirizza a un file di output xml. Ogni tipo di messaggio nell'output è identificato da un colore univoco. Ad esempio, il messaggio di testo di colore bianco indica i comandi di file di script. quello di colore verde rappresenta un prompt dei comandi per l'input dell'utente e così via.  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
Colore interpretazione dell'output di console nella tabella seguente:  
  
|Colore|Description|  
|---------|---------------|  
|Red|Errore irreversibile durante l'esecuzione|  
|Grigio|Indicatore di data e ora, messaggio per l'utente|  
|bianco|Comandi nel file di script, il tipo di messaggio|  
|Giallo|Avviso|  
|Green|Richiedi input utente|  
|azzurro|Inizio, fine e il risultato di un'operazione|  
  
## <a name="see-also"></a>Vedere anche  
[L'installazione di SSMA per MySQL](http://msdn.microsoft.com/en-us/e89b45bd-59c1-4d23-8bd7-3dafc1947448)  
  

