---
title: Introduzione a SSMA per la Console MySQL (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 8f33769bee5c8d6d9e134eb9dd5dcf8549d651cb
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983083"
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Introduzione a SSMA per la Console MySQL (MySQLToSQL)
In questa sezione viene descritta la procedura per avviare e iniziare a usare l'applicazione console MySQL. Anche nell'elenco, nel presente documento, vengono utilizzate le convenzioni di in una finestra di output della Console SSMA tipica.  
  
## <a name="launching-ssma-console"></a>Avviare Console SSMA  
Per avviare l'applicazione console SSMA, procedere come segue:  
  
1.  Passare a **avviare** e scegliere **tutti i programmi**.  
  
2.  Scegliere il **SQL Server Migration Assistant per MySQL Prompt dei comandi** scelta rapida.  
  
    Viene visualizzato il menu di utilizzo della Console SSMA e `(/? Help)`, che consentono di iniziare a usare l'applicazione console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procedure per l'utilizzo della Console SSMA  
Dopo che la console viene avviata correttamente nel sistema Windows, è possibile utilizzare i passaggi seguenti per risolverlo:  
  
1.  Configurare Console SSMA tramite i file di script. Per altre informazioni su questa sezione, vedere [creazione di file di Script &#40;MySQLToSQL&#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md) .  
  
2.  [Creazione di file di valore della variabile &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [Creazione di file di connessione del Server &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [Esecuzione della Console SSMA &#40;MySQLToSQL&#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) secondo le esigenze di progetto  
  
Altre funzionalità:  
  
1.  [Protezione di Password](http://msdn.microsoft.com/4ffbc587-ea3f-49ad-bc42-a654f672325e) ed esportare / importare in un altro computer della finestra  
  
2.  [Generare report](http://msdn.microsoft.com/1c0202e8-546d-4cb3-a37f-1d2e35d53839) per visualizzare il codice xml dettagliate dell'output di report per la migrazione di dati e /conversion assessment. I report di errore dettagliati possono anche essere generati per i comandi di aggiornamento e la sincronizzazione.  
  
## <a name="ssma-console-output-conventions"></a>Convenzioni di Output di Console SSMA  
Dopo l'esecuzione di comandi di script SSMA e le opzioni, il programma di console vengono visualizzati i risultati e messaggi (le informazioni, errore, e così via) per l'utente nella console o se necessario, reindirizza a un file di output xml. Ogni tipo di messaggio nell'output è identificato da un colore univoco. Ad esempio, il messaggio di testo di colore bianco indica i comandi di file di script; quello di colore verde rappresenta un prompt dei comandi per l'input utente e così via.  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
Colore dall'interpretazione dell'output della console nella tabella seguente:  
  
|Colore|Description|  
|---------|---------------|  
|Red|Errore irreversibile durante l'esecuzione|  
|Grigio|Data e un timestamp, messaggio all'utente|  
|bianco|Comandi di file di script, il tipo di messaggio|  
|Giallo|Avviso|  
|Green|Richiedi input utente|  
|azzurro|Inizio, fine e il risultato di un'operazione|  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per MySQL](http://msdn.microsoft.com/e89b45bd-59c1-4d23-8bd7-3dafc1947448)  
  
