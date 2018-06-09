---
title: Introduzione a SSMA per Sybase Console (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0ae06be98a30b6c293ef3625f31ff2ac272c1d8e
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34778547"
---
# <a name="getting-started-with-the-ssma-for-sybase-console-sybasetosql"></a>Introduzione a SSMA per Sybase Console (SybaseToSQL)
In questa sezione viene descritta la procedura per l'avvio e introduzione di SSMA per l'applicazione console di Sybase. Inoltre elencati nel presente documento vengono usate le convenzioni in una finestra di output della Console di SSMA tipico.  
  
## <a name="launching-the-ssma-console"></a>Avviare la Console di SSMA  
Utilizzare la procedura seguente per avviare l'applicazione console SSMA:  
  
1.  Andare a Start e quindi scegliere tutti i programmi.  
  
2.  Fare clic su di **SQL Server Migration Assistant per Sybase Prompt dei comandi** scelta rapida.  
  
    Viene visualizzato il menu di utilizzo della Console di SSMA e `(/? Help)`, che consentono di iniziare a utilizzare l'applicazione console.  
  
## <a name="using-the-ssma-console"></a>Utilizzando la Console di SSMA  
Dopo la console viene avviata correttamente nel sistema Windows, è possibile utilizzare la procedura seguente per lavorare su di esso:  
  
1.  Configurare la Console di SSMA tramite i file di script. Per ulteriori informazioni su questa sezione, vedere [creazione di file di Script &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
2.  [Creazione di file di valore della variabile &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [La creazione dei file di connessione del Server &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [L'esecuzione la Console di SSMA &#40;SybaseToSQL&#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) in base alle esigenze del progetto. 
  
Altre funzionalità:  
  
1.  [Specificare una password](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c) e l'esportazione/importazione, altri computer della finestra.  
  
2.  [Generare report](http://msdn.microsoft.com/en-us/19278f6a-6d58-4867-9d71-c6228040466e) per visualizzare il codice xml dettagliato i report per la migrazione di conversione o di valutazione e i dati di output. È anche possibile generare report di errore dettagliati per i comandi di aggiornamento e la sincronizzazione.  
  
## <a name="ssma-console-output-conventions"></a>Convenzioni di output di Console di SSMA  
Durante l'esecuzione di comandi script SSMA e le opzioni, il programma di console consente di visualizzare i risultati e messaggi (le informazioni, errore e così via) per l'utente nella console o, se necessario, reindirizza a un file di output xml. Ogni tipo di messaggio nell'output è identificato da un colore univoco. Ad esempio, il messaggio di testo di colore bianco indica i comandi di file di script. quello di colore verde rappresenta un prompt dei comandi per l'input dell'utente e così via.  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
Interpretazione di colore dell'output di console viene visualizzato nella tabella seguente:  
  
|Colore|Description|  
|---------|---------------|  
|Red|Errore irreversibile durante l'esecuzione|  
|Grigio|Indicatore di data e ora, messaggio per l'utente|  
|bianco|Comandi nel file di script, il tipo di messaggio|  
|Giallo|Avviso|  
|Green|Richiedi input utente|  
|azzurro|Inizio, fine e risultato di un'operazione|  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
