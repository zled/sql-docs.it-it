---
title: Un Provider Microsoft OLE DB semplice | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- simple provider [ADO]
- providers [ADO], OLE DB simple provider
- OLE DB simple provider [ADO]
ms.assetid: 1e7dc6f0-482c-4103-8187-f890865e40fc
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7e4a5742b9d5b084d10540737ac87c55d441d0a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-ole-db-simple-provider-overview"></a>Panoramica di Simple Provider Microsoft OLE DB
Il Microsoft OLE DB semplici Provider (OSP) consente di ADO per accedere ai dati per il quale un provider è stato scritto utilizzando il [OLE DB semplici Provider (OSP) Toolkit](http://msdn.microsoft.com/en-us/6e7b7931-9e4a-4151-ae51-672abd3f84a6). Un provider semplice servono per accedere alle origini dati che richiedono il supporto di OLE DB solo fondamentale, ad esempio matrici in memoria o documenti XML.

## <a name="connection-string-parameters"></a>Parametri di stringa di connessione
 Per connettersi a OLE DB semplici Provider DLL, impostare il *Provider* argomento per il [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà:

```
MSDAOSP
```

 Questo valore può essere impostato o utilizzando il [Provider](../../../ado/reference/ado-api/provider-property-ado.md) proprietà.

 È possibile connettersi a un provider semplice che è stato registrato come provider OLE DB completo utilizzando il nome del provider registrato, determinato dal writer di provider.

## <a name="typical-connection-string"></a>Stringa di connessione tipica
 Una stringa di connessione tipica per questo provider è:

```
"Provider=MSDAOSP;Data Source=serverName"
```

 La stringa è costituita da queste parole chiave:

|Parola chiave|Description|
|-------------|-----------------|
|**Provider**|Specifica il provider OLE DB per SQL Server.|
|**Data Source**|Specifica il nome di un server.|

## <a name="xml-document-example"></a>Esempio di documento XML
 Di OLE DB semplici Provider (OSP) in MDAC 2.7 o versioni successive e Windows Data Access Components (Windows DAC) è stata migliorata per supportare l'apertura di ADO gerarchica **recordset** rispetto ai file XML arbitrari. Questi file XML possono contenere lo schema di persistenza XML ADO, ma non è necessaria. Questo è stato implementato tramite la connessione di OSP per il **MSXML2.DLL**; pertanto **MSXML2** o versione successiva è richiesto.

 Il **portfolio.xml** file utilizzato nell'esempio seguente contiene la struttura seguente:

```
Portfolio
   Stock
      Shares
      Symbol
      Price
      Info
         Company Name
         WebSite
```

 Gli oggetti DSO XML Usa regole euristiche predefinite per convertire i nodi in un albero XML capitoli gerarchico **Recordset**.

 Utilizzando tale euristica predefinita, la struttura ad albero XML viene convertito in un due livelli gerarchici **Recordset** nel formato seguente:

```
Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text
```

 Si noti che i tag Portfolio e le informazioni non sono rappresentati di gerarchica **Recordset**. Per una spiegazione delle modalità di DSO XML di conversione strutture ad albero XML gerarchici **recordset**, vedere le seguenti regole. La colonna $Text viene illustrata nella sezione seguente.

## <a name="rules-for-assigning-xml-elements-and-attributes-to-columns-and-rows"></a>Regole per l'assegnazione di elementi e attributi XML le colonne e righe
 Gli oggetti DSO XML segue una procedura per l'assegnazione di elementi e gli attributi di colonne e righe nelle applicazioni di associazione a dati. XML viene modellato come una struttura ad albero con un tag che contiene l'intera gerarchia. Ad esempio, una descrizione XML di un libro potrebbe contenere tag capitolo, figura e tag di sezione. Livello più alto sarà il tag di libro, contenente il capitolo sottoelementi, la figura e sezione. Quando gli oggetti DSO XML esegue il mapping di elementi XML in righe e colonne, i sottoelementi, non l'elemento di primo livello, vengono convertiti.

 Gli oggetti DSO XML utilizza questa procedura per la conversione dei sottoelementi:

-   Ogni sottoelemento e attributo corrisponde a una colonna in alcune **Recordset** nella gerarchia.

-   Il nome della colonna è lo stesso nome del sottoelemento o attributo, a meno che l'elemento padre ha un attributo e un sottoelemento con lo stesso nome, nel qual caso un "!" viene anteposto al nome di colonna del sottoelemento.

-   Ogni colonna è un *semplice* colonna contenente valori scalari (in genere stringhe) o un **Recordset** colonna che contiene figlio **recordset**.

-   Nelle colonne corrispondenti per gli attributi sono sempre semplici.

-   Nelle colonne corrispondenti per i sottoelementi sono **Recordset** colonne se il sottoelemento ha un proprio sottoelementi o attributi (o entrambi), o padre del sottoelemento include più di un'istanza di un sottoelemento come elemento figlio. In caso contrario, la colonna è semplice.

-   Quando sono presenti più istanze di un sottoelemento (padri differenti), la relativa colonna è un **Recordset** colonna se *qualsiasi* delle istanze implica un **Recordset** colonna, è semplice colonna solo se *tutti* istanze implicano una colonna semplice.

-   Tutti **recordset** dispone di una colonna aggiuntiva denominata $Text.

 Il codice necessari per costruire un **Recordset** è indicato di seguito:

```
Dim adoConn as ADODB.Connection
Dim adoRS as ADODB.Recordset

Set adoRS = New ADODB.Connection
Set adoRS = New ADODB.Recordset

adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
adoRS.Open "http://WebServer/VRoot/portfolio.xml, adoConn
```

> [!NOTE]
>  Con diverse convenzioni di denominazione, è possibile specificare il percorso del file di dati.

```
'HTTP://
adoRS.Open "http://WebServer/VRoot/portfolio.xml", adoConn
'FILE://
adoRS.Open "file:/// C:\\Directory\\portfolio.xml", adoConn
'UNC Path
adoRS.Open "\\ComputerName\ShareName\portfolio.xml", adoConn
'Full DOS Path
adoRS.Open "C:\Directory\portfolio.xml", adoConn
```

 Non appena il **Recordset** è stato aperto, il consueto ADO **Recordset** è possibile utilizzare i comandi di navigazione.

 **Recordset** generati dal OSP presentano alcune limitazioni:

-   I cursori client (**adUseClient**) non sono supportati.

-   Gerarchica **recordset** creato sopra arbitrario XML non può essere persistente utilizzando **Recordset. Save**.

-   **Recordset** creato con il OSP sono di sola lettura.

-   Il XMLDSO aggiunge una colonna aggiuntiva dei dati ($Text) a ogni **Recordset** nella gerarchia.

 Per ulteriori informazioni sui Provider OLE DB semplici, vedere [la creazione di un Provider semplice](http://msdn.microsoft.com/en-us/b31a6cba-58ae-4ee8-9039-700973d354d6).

## <a name="code-example"></a>Esempio di codice
 Il codice di Visual Basic seguente illustra l'apertura di un file XML arbitrario, la costruzione di un modello gerarchico **Recordset**e in modo ricorsivo la scrittura di ogni record di ogni **Recordset** alla finestra di debug.

 Di seguito è riportato un semplice file XML contenente le quotazioni di borsa. Il codice seguente usa questo file per costruire un due livelli gerarchici **Recordset**.

```
<portfolio>
   <stock>
      <shares>100</shares>
      <symbol>MSFT</symbol>
      <price>$70.00</price>
      <info>
         <companyname>Microsoft Corporation</companyname>
         <website>http://www.microsoft.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>AAPL</symbol>
      <price>$107.00</price>
      <info>
         <companyname>Apple Computer, Inc.</companyname>
         <website>http://www.apple.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>DELL</symbol>
      <price>$50.00</price>
      <info>
         <companyname>Dell Corporation</companyname>
         <website>http://www.dell.com</website>
      </info>
    </stock>
    <stock>
       <shares>100</shares>
       <symbol>INTC</symbol>
       <price>$115.00</price>
       <info>
          <companyname>Intel Corporation</companyname>
          <website>http://www.intel.com</website>
       </info>
   </stock>
</portfolio>
```

 Di seguito sono due subroutine di Visual Basic. Il primo crea il **Recordset** e lo passa al *WalkHier* sub procedura viene illustrato che in modo ricorsivo verso il basso della gerarchia, ogni scrittura **campo** in ogni record in ogni **Recordset** alla finestra di debug.

```
Private Sub BrowseHierRecordset()
' Add ADO 2.7 or later to Project/References
' No need to add MSXML2, ADO just passes the ProgID through to the OSP.

    Dim adoConn As ADODB.Connection
    Dim adoRS As ADODB.Recordset
    Dim adoChildRS As ADODB.Recordset

    Set adoConn = New ADODB.Connection
    Set adoRS = New ADODB.Recordset
    Set adoChildRS = ADODB.Recordset

    adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
    adoRS.Open "http://bwillett3/Kowalski/portfolio.xml", adoConn

    Dim iLevel As Integer
    iLevel = 0
    WalkHier iLevel, adoRS

End Sub

Sub WalkHier(ByVal iLevel As Integer, ByVal adoRS As ADODB.Recordset)
    iLevel = iLevel + 1
    PriorLevel = iLevel
    While Not adoRS.EOF
        For ndx = 0 To adoRS.Fields.Count - 1
            If adoRS.Fields(ndx).Name <> "$Text" Then
                If adoRS.Fields(ndx).Type = adChapter Then
                    Set adoChildRS = adoRS.Fields(ndx).Value
                    WalkHier iLevel, adoChildRS
                Else
                    Debug.Print iLevel & ": adoRS.Fields(" & ndx & _
                       ") = " & adoRS.Fields(ndx).Name & " = " & _
                       adoRS.Fields(ndx).Value
                End If
            End If
        Next ndx
        adoRS.MoveNext
    Wend
    iLevel = PriorLevel
End Sub
```
