---
title: Il recupero dei dati tramite AdomdDataReader | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- retrieving data
- AdomdDataReader object
- data retrieval [ADOMD.NET], AdomdDataReader object
ms.assetid: 8ed7ea26-b5f8-4852-80fc-75dd62df5b3a
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 17ed47d13aab29ea47c5f1d041705029844e359e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062327"
---
# <a name="retrieving-data-using-the-adomddatareader"></a>Recupero di dati tramite AdomdDataReader
  Nel recupero di dati analitici, l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> consente di ottenere un buon bilanciamento tra overhead e interattività. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> consente di recuperare un flusso di dati bidimensionale, forward-only e di sola lettura da un'origine dati analitici. Tale flusso privo di buffer consente alla logica procedurale di elaborare sequenzialmente risultati da un'origine dati analitici con notevole efficienza. Per questo motivo l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> rappresenta una soluzione efficace durante il recupero di grandi quantità di dati da visualizzare poiché i dati stessi non vengono memorizzati nella memoria cache.  
  
 L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> consente inoltre di aumentare le prestazioni dell'applicazione recuperando i dati non appena sono disponibili anziché attendere i risultati completi della query da restituire. Tramite <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> è inoltre possibile ridurre l'overhead di sistema poiché, per impostazione predefinita, tale lettore archivia in memoria solo una riga alla volta.  
  
 Le prestazioni risultano ottimizzate poiché l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> fornisce meno informazioni sui dati recuperati rispetto agli altri metodi per il recupero di dati. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> non supporta un modello a oggetti di grandi dimensioni per la rappresentazione di dati o metadati né consente a tale modello di utilizzare caratteristiche analitiche più complesse, ad esempio il writeback delle celle. L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> fornisce tuttavia un set di metodi fortemente tipizzati per il recupero di dati di set di celle e un metodo per il recupero di metadati di set di celle in formato tabulare. Inoltre, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> implementa la **IDbDataReader** interfaccia supportano il data binding e per il recupero dei dati tramite il `SelectCommand` (metodo), dal **System. Data** dello spazio dei nomi del Libreria di classi Microsoft .NET Framework.  
  
## <a name="retrieving-data-from-the-adomddatareader"></a>Recupero di dati tramite AdomdDataReader  
 Per utilizzare l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> per recuperare dati, effettuare le seguenti operazioni:  
  
1.  **Creare una nuova istanza dell'oggetto.**  
  
     Per creare una nuova istanza della classe <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> o <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
2.  **Recuperare i dati.**  
  
     Quando il comando esegue la query, ADOMD.NET restituisce i risultati nel formato tabulare `Resultset` descritto nella specifica XML for Analysis in modo da rendere bidimensionali i dati per l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>. Considerando le dimensioni variabili dei dati analitici, l'utilizzo di un formato tabulare è anomalo in caso di esecuzione di query su questo tipo di dati.  
  
     ADOMD.NET archivia tali risultati tabulari nel buffer di rete presente nel client fino a quando non vengono richiesti dall'utente tramite la chiamata a uno dei metodi seguenti:  
  
    -   Chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
         Il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Read%2A> ottiene una riga dai risultati della query. Successivamente è possibile passare il nome o il riferimento ordinale della colonna alla proprietà <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Item%2A> per accedere a ogni colonna della riga restituita. Se ad esempio alla prima colonna della riga corrente è assegnato il nome ColumnName, `reader[0].ToString()` o `reader["ColumnName"].ToString()` restituiranno il contenuto della prima colonna della riga corrente.  
  
    -   Uno dei metodi tipizzati della funzione di accesso.  
  
         L'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> fornisce una serie di metodi tipizzati della funzione di accesso che consentono di accedere ai valori di colonna nei tipi di dati nativi. Quando si conosce il tipo di dati sottostanti di un valore di colonna, un metodo tipizzato della funzione di accesso riduce la conversione dei tipi necessaria per il recupero del valore di colonna ottimizzando in questo modo le prestazioni.  
  
         Alcuni tra i metodi tipizzati della funzione di accesso disponibili includono <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDateTime%2A>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDouble%2A> e <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetInt32%2A>. Per un elenco completo di metodi tipizzati della funzione di accesso, vedere <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
3.  **Chiudere il lettore.**  
  
     È sempre necessario chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.Close%2A> al termine dell'utilizzo dell'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>. Mentre un'istanza di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> è aperta, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> viene utilizzato esclusivamente dall'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> specifico. Non sarà possibile eseguire qualsiasi comando sull'istanza di <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, ad esempio la creazione di un altro oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> o `System.Xml.XmlReader`, fino a quando l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> non verrà chiuso.  
  
### <a name="example-of-retrieving-data-from-the-adomddatareader"></a>Esempio di recupero di dati tramite AdomdDataReader  
 Nell'esempio di codice seguente viene scorso l'oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> e vengono restituiti i primi due valori di ogni riga in formato stringa.  
  
```vb  
If Reader.HasRows Then  
    Do While objReader.Read()  
        Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
            objReader.GetString(0), objReader.GetString(1))  
    Loop  
Else  
  Console.WriteLine("No rows returned.")  
End If  
  
objReader.Close()  
```  
  
```csharp  
if (objReader.HasRows)  
  while (objReader.Read())  
    Console.WriteLine("\t{0}\t{1}", _  
        objReader.GetString(0), objReader.GetString(1));  
else  
  Console.WriteLine("No rows returned.");  
  
objReader.Close();  
```  
  
## <a name="retrieving-metadata-from-the-adomddatareader"></a>Recupero di metadati tramite AdomdDataReader  
 Mentre un'istanza di un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> è aperta, è possibile recuperare informazioni sullo schema, ovvero metadati, per il recordset corrente utilizzando il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>. <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetSchemaTable%2A>Restituisce un `DataTable` oggetto popolato con le informazioni sullo schema per il recordset corrente. Gli oggetti `DataTable` conterranno una riga per ogni colonna del recordset. Ogni colonna di una riga di tabella dello schema è mappata a una proprietà della colonna restituita nel set di celle, in cui `ColumnName` è il nome della proprietà e il valore della colonna è il valore della proprietà.  
  
### <a name="example-of-retrieving-metadata-from-the-adomddatareader"></a>Esempio di recupero di metadati tramite AdomdDataReader  
 Nell'esempio di codice seguente vengono restituite le informazioni sullo schema per un oggetto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>.  
  
```vb  
Dim schemaTable As DataTable = objReader.GetSchemaTable()  
  
Dim objRow As DataRow  
Dim objColumn As DataColumn  
  
For Each objRow In schemaTable.Rows  
  For Each objColumn In schemaTable.Columns  
    Console.WriteLine(objColumn.ColumnName & " = " & objRow(objColumn).ToString())  
  Next  
  Console.WriteLine()  
Next  
DataTable schemaTable = objReader.GetSchemaTable();  
```  
  
```csharp  
foreach (DataRow objRow in schemaTable.Rows)  
{  
  foreach (DataColumn objColumn in schemaTable.Columns)  
    Console.WriteLine(objColumn.ColumnName + " = " + objRow[objColumn]);  
  Console.WriteLine();  
}  
```  
  
## <a name="retrieving-multiple-result-sets"></a>Recupero di più set di risultati  
 Nelle operazioni di data mining è supportato il concetto di tabelle nidificate, che ADOMD.NET espone come set di righe nidificati. Per recuperare il set di righe nidificato associato a ogni riga, chiamare il metodo <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader.GetDataReader%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Recupero di dati da un'origine dati analitici](retrieving-data-from-an-analytical-data-source.md)   
 [Il recupero dei dati tramite l'oggetto CellSet](retrieving-data-using-the-cellset.md)   
 [Recupero di dati tramite XmlReader](retrieving-data-using-the-xmlreader.md)  
  
  