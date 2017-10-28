---
title: Guida introduttiva di SSMA per la Console di DB2 (DB2ToSQL) | Documenti Microsoft
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
ms.assetid: f245c017-023e-4880-8721-8908d339525e
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 24c96c6e76d89d271d80e3be51c8c27d62dbd6b3
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma--for-db2-console-db2tosql"></a>Guida introduttiva di SSMA per la Console di DB2 (DB2ToSQL)
In questa sezione viene descritta la procedura per avviare e iniziare a usare l'applicazione console di DB2. Elencati, anche nel presente documento, vengono usate le convenzioni in una finestra di output della Console di SSMA tipico.  
  
## <a name="launching-ssma-console"></a>Avviare la Console di SSMA  
Utilizzare la procedura seguente per avviare l'applicazione console SSMA:  
  
1.  Passare a **avviare** e scegliere **tutti i programmi**.  
  
2.  Fare clic su di  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per DB2 Prompt dei comandi** scelta rapida.  
  
    Viene visualizzato il menu di utilizzo della Console di SSMA e `(/? Help)`, che consentono di iniziare a utilizzare l'applicazione console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procedura per utilizzare la Console SSMA  
Dopo la console viene avviata correttamente nel sistema Windows, è possibile utilizzare la procedura seguente per lavorare su di esso:  
  
1.  Configurare la Console di SSMA tramite i file di script. Per ulteriori informazioni su questa sezione, vedere [DB2ToSQL creazione di file di Script &#40; &#41;](../../ssma/db2/creating-script-files-db2tosql.md) .  
  
2.  [Creazione di file di valore della variabile &#40; DB2ToSQL &#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
3.  [Creazione di DB2ToSQL i file di connessione del Server &#40; &#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
4.  [L'esecuzione la Console SSMA &#40; DB2ToSQL &#41; ](../../ssma/db2/executing-the-ssma-console-db2tosql.md) in base alle esigenze del progetto  
  
Altre funzionalità:  
  
1.  [La gestione delle password](http://msdn.microsoft.com/en-us/56d546e3-8747-4169-aace-693302667e94) e l'esportazione / importazione in altri computer della finestra  
  
2.  [Generazione di report](http://msdn.microsoft.com/en-us/69ef5fd9-190d-4c58-8199-b3f77d5e1883) per visualizzare il codice xml dettagliate l'output di report per la migrazione di dati e /conversion di valutazione. I report di errore dettagliato possono essere generati anche per i comandi di aggiornamento e la sincronizzazione.  
  
## <a name="ssma-console-output-conventions"></a>Convenzioni di Output di Console SSMA  
Durante l'esecuzione di comandi script SSMA e le opzioni, il programma di console consente di visualizzare i risultati e messaggi (le informazioni, errore e così via) per l'utente nella console o se necessario, reindirizza a un file di output xml. Ogni tipo di messaggio nell'output è identificato da un colore univoco. Ad esempio, il messaggio di testo di colore bianco indica i comandi di file di script. quello di colore verde rappresenta un prompt dei comandi per l'input dell'utente e così via.  
  
![Ssmaconsoleoutput_oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "ssmaconsoleoutput_oracle")  
  
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
[L'installazione di SSMA per DB2](http://msdn.microsoft.com/en-us/79fbe8ea-471b-407a-be2a-4100d9b57c61)  
  

