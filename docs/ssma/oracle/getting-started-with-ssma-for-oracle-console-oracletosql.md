---
title: Introduzione a SSMA per Oracle Console (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Oracle Console, Console Output Conventions
- Oracle Console, Launching Console
ms.assetid: 667a5e4a-6848-4973-a72d-1287f64718ac
caps.latest.revision: 31
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: f80a1d1dde407c2269a29c4c18c0ad583dc39b93
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34777317"
---
# <a name="getting-started-with-ssma--for-oracle-console-oracletosql"></a>Introduzione a SSMA per Oracle Console (OracleToSQL)
In questa sezione viene descritta la procedura per avviare e iniziare a usare l'applicazione console Oracle. Elencati, anche nel presente documento, vengono usate le convenzioni in una finestra di output della Console di SSMA tipico.  
  
## <a name="launching-ssma-console"></a>Avviare la Console di SSMA  
Utilizzare la procedura seguente per avviare l'applicazione console SSMA:  
  
1.  Passare a **avviare** e scegliere **tutti i programmi**.  
  
2.  Fare clic su di  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per Oracle Prompt dei comandi** scelta rapida.  
  
    Viene visualizzato il menu di utilizzo della Console di SSMA e `(/? Help)`, che consentono di iniziare a utilizzare l'applicazione console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procedura per utilizzare la Console SSMA  
Dopo la console viene avviata correttamente nel sistema Windows, è possibile utilizzare la procedura seguente per lavorare su di esso:  
  
1.  Configurare la Console di SSMA tramite i file di script. Per ulteriori informazioni su questa sezione, vedere [creazione di file di Script &#40;OracleToSQL&#41; ](../../ssma/oracle/creating-script-files-oracletosql.md) .  
  
2.  [Creazione di file di valore della variabile &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
  
3.  [La creazione dei file di connessione del Server &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
4.  [L'esecuzione la Console di SSMA &#40;OracleToSQL&#41; ](../../ssma/oracle/executing-the-ssma-console-oracletosql.md) in base alle esigenze del progetto  
  
Altre funzionalità:  
  
1.  [Specificare una password](http://msdn.microsoft.com/en-us/8c7d9f8e-06bb-476c-bbd2-15b61d5bba3c) ed esportazione / importazione in altri computer di finestra  
  
2.  [Generare report](http://msdn.microsoft.com/en-us/ccad6262-01e1-447a-bd2b-c105154c80ce) per visualizzare il codice xml dettagliate output report per la migrazione /conversion e i dati di valutazione. I report di errore dettagliato possono essere generati anche per i comandi di aggiornamento e la sincronizzazione.  
  
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
[Installazione di SSMA per Oracle](http://msdn.microsoft.com/en-us/9211013a-ab24-4c52-9b26-87994b35e502)  
  
