---
title: Esecuzione di comandi in un'origine dati analitici | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- AdomdCommand object
- commands [ADOMD.NET]
- ADOMD.NET, commands
ms.assetid: 1a958e5f-fc18-480b-9706-fc44e3b1d534
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 36d94ba3ae75f2b3d59e0fb159ee639a5f2edb43
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202021"
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
|Restituzione di un oggetto `XMLReader` che contiene i dati in un formato conforme a XML for Analysis (XMLA)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Esempio di esecuzione di un comando  
 In questo esempio viene utilizzato <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> per eseguire un comando XMLA che elaborerà il cubo `Adventure Works DW` nel server locale senza restituire dati.  
  
 [!code-csharp[Adomd.NetClient#ExecuteXMLAProcessCommand](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#executexmlaprocesscommand)]  
  
  
