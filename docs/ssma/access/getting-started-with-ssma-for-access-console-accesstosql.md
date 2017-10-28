---
title: Introduzione a SSMA per la Console di accesso (AccessToSQL) | Documenti Microsoft
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
ms.assetid: 8585ec16-7e0a-483a-b250-adab9b9232a3
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2b555cebf6fbfda157b72e8bc71b10600da54d39
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-access-console-accesstosql"></a>Introduzione a SSMA per la Console di accesso (AccessToSQL)
In questa sezione viene descritta la procedura per avviare e iniziare a usare l'applicazione console di accesso. Elencati, anche nel presente documento, vengono usate le convenzioni in una finestra di output della Console di SSMA tipico.  
  
## <a name="launching-ssma-console"></a>Avviare la Console di SSMA  
Utilizzare la procedura seguente per avviare l'applicazione console SSMA:  
  
1.  Passare a **avviare** e scegliere **tutti i programmi**.  
  
2.  Fare clic su di **SQL Server Migration Assistant per Access Prompt dei comandi** scelta rapida.  
  
    Viene visualizzato il menu di utilizzo della Console di SSMA e `(/? Help)`, che consentono di iniziare a utilizzare l'applicazione console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procedura per utilizzare la Console SSMA  
Dopo la console viene avviata correttamente nel sistema Windows, è possibile utilizzare la procedura seguente per lavorare su di esso:  
  
1.  Configurare la Console di SSMA tramite i file di script. Per ulteriori informazioni su questa sezione, vedere [creazione di file di Script &#40; AccessToSQL &#41; ](../../ssma/access/creating-script-files-accesstosql.md).  
  
2.  [Creazione di valore della variabile file &#40; AccessToSQL &#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
  
3.  [Creare i file di connessione del Server &#40; AccessToSQL &#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
4.  [L'esecuzione la Console SSMA &#40; AccessToSQL &#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md) in base alle esigenze del progetto  
  
Altre funzionalità:  
  
1.  [Specificare una password](http://msdn.microsoft.com/en-us/b099d0f9-dd37-4c87-8b6f-ed0177881ea4) e l'esportazione / importazione in altri computer della finestra  
  
2.  [Generare report](http://msdn.microsoft.com/en-us/abb4264a-622e-4215-af5b-14e309b8a399) per visualizzare il codice xml dettagliate l'output di report per la migrazione di dati e /conversion di valutazione. I report di errore dettagliato possono essere generati anche per i comandi di aggiornamento e la sincronizzazione.  
  
## <a name="ssma-console-output-conventions"></a>Convenzioni di Output di Console SSMA  
Durante l'esecuzione di comandi script SSMA e le opzioni, il programma di console consente di visualizzare i risultati e messaggi (le informazioni, errore e così via) per l'utente nella console o se necessario, reindirizza a un file di output xml. Ogni tipo di messaggio nell'output è identificato da un colore univoco. Ad esempio, il messaggio di testo di colore bianco indica i comandi di file di script. quello di colore verde rappresenta un prompt dei comandi per l'input dell'utente e così via.  
  
![Output della Console SSMA](../../ssma/access/media/ssmaconsoleoutput.jpg "Output della Console SSMA")  
  
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
[L'installazione di SQL Server Migration Assistant per Access](http://msdn.microsoft.com/en-us/dd50eebd-75df-4e0d-8c4d-88b511aae4c7)  
  

