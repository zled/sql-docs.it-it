---
title: Esecuzione di comandi su un'origine dati analitici | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2255f699edf57b1416191383b216875a7f13bb5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="executing-commands-against-an-analytical-data-source"></a>Esecuzione di comandi in un'origine dati analitici
  Dopo avere stabilito una connessione a un'origine dati analitica, è possibile utilizzare un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> per eseguire comandi e restituire risultati da tale origine dati. Tali comandi possono recuperare dati tramite istruzioni MDX (Multidimensional Expressions) o DMX (Data Mining Extensions) o tramite una sintassi limitata di SQL. È inoltre possibile utilizzare comandi ASSL (Analysis Services Scripting Language) per modificare il database sottostante.  
  
## <a name="creating-a-command"></a>Creazione di un comando  
 Prima di eseguire un comando, è necessario crearlo. Per creare un comando, utilizzare uno dei due elementi seguenti:  
  
-   Costruttore <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> che può accettare un comando da eseguire nell'origine dati e un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> su cui eseguire il comando.  
  
-   Metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Sul testo del comando da effettuare può essere eseguita una query e il testo stesso può essere modificato tramite la proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A>. I comandi creati non devono restituire dati dopo l'esecuzione.  
  
## <a name="running-a-command"></a>Esecuzione di un comando  
 Dopo avere creato un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, sono disponibili numerosi metodi <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> che il comando può utilizzare per eseguire le diverse azioni. Nella tabella seguente vengono elencate alcune di tali azioni.  
  
|Per|Metodo da utilizzare|  
|--------|---------------------|  
|Restituzione di risultati come un flusso di dati|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> per restituire un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|  
|Restituzione di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|Esecuzione di comandi che non restituiscono righe|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|Restituire un **XMLReader** oggetto che contiene i dati in un file XML per formato conforme a Analysis (XMLA)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Esempio di esecuzione di un comando  
 Questo esempio viene utilizzato il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> per eseguire un comando XMLA che elaborerà il **Adventure Works DW** cubo nel server locale, senza restituire dati.  
  
 [!code-cs[Adomd.NetClient#ExecuteXMLAProcessCommand](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/executing-commands-again_1.cs)]  
  
  
