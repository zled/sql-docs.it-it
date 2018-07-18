---
title: Introduzione a SSMA per la Console di accesso (AccessToSQL) | Microsoft Docs
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
ms.assetid: 8585ec16-7e0a-483a-b250-adab9b9232a3
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0e2a7465cc46e5ca2bb69ba4c7ef61dd85bf9882
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985403"
---
# <a name="getting-started-with-ssma-for-access-console-accesstosql"></a>Introduzione a SSMA per la Console di accesso (AccessToSQL)
In questa sezione viene descritta la procedura per avviare e iniziare a usare l'applicazione console di accesso. Anche nell'elenco, nel presente documento, vengono utilizzate le convenzioni di in una finestra di output della Console SSMA tipica.  
  
## <a name="launching-ssma-console"></a>Avviare Console SSMA  
Per avviare l'applicazione console SSMA, procedere come segue:  
  
1.  Passare a **avviare** e scegliere **tutti i programmi**.  
  
2.  Scegliere il **SQL Server Migration Assistant per Access Prompt dei comandi** scelta rapida.  
  
    Viene visualizzato il menu di utilizzo della Console SSMA e `(/? Help)`, che consentono di iniziare a usare l'applicazione console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procedure per l'utilizzo della Console SSMA  
Dopo che la console viene avviata correttamente nel sistema Windows, è possibile utilizzare i passaggi seguenti per risolverlo:  
  
1.  Configurare Console SSMA tramite i file di script. Per altre informazioni su questa sezione, vedere [creazione di file di Script &#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
2.  [Creazione di file di valore della variabile &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
  
3.  [Creazione di file di connessione del Server &#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
4.  [Esecuzione della Console SSMA &#40;AccessToSQL&#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md) secondo le esigenze di progetto  
  
Altre funzionalità:  
  
1.  [Specificare una password](http://msdn.microsoft.com/b099d0f9-dd37-4c87-8b6f-ed0177881ea4) ed esportare / importare in un altro computer della finestra  
  
2.  [Generare report](http://msdn.microsoft.com/abb4264a-622e-4215-af5b-14e309b8a399) per visualizzare il codice xml dettagliate dell'output di report per la migrazione di dati e /conversion assessment. I report di errore dettagliati possono anche essere generati per i comandi di aggiornamento e la sincronizzazione.  
  
## <a name="ssma-console-output-conventions"></a>Convenzioni di Output di Console SSMA  
Dopo l'esecuzione di comandi di script SSMA e le opzioni, il programma di console vengono visualizzati i risultati e messaggi (le informazioni, errore, e così via) per l'utente nella console o se necessario, reindirizza a un file di output xml. Ogni tipo di messaggio nell'output è identificato da un colore univoco. Ad esempio, il messaggio di testo di colore bianco indica i comandi di file di script; quello di colore verde rappresenta un prompt dei comandi per l'input utente e così via.  
  
![Output della Console SSMA](../../ssma/access/media/ssmaconsoleoutput.jpg "Output della Console SSMA")  
  
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
[Installazione di SQL Server Migration Assistant per Access](http://msdn.microsoft.com/dd50eebd-75df-4e0d-8c4d-88b511aae4c7)  
  
