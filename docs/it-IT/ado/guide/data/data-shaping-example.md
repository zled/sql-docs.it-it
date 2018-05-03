---
title: Data Shaping esempio | Documenti Microsoft
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
- data shaping [ADO], about data shaping
ms.assetid: 1bfdcad4-52e1-45bc-ad21-783657ef0a44
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 991ea5c55a99aa8dbe043dd99b9703acd73172e9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="data-shaping-example"></a>Data Shaping di esempio
I seguenti dati di data shaping di comando di seguito viene illustrato come compilare un modello gerarchico **Recordset** dal **clienti** e **ordini** tabelle nel database Northwind.  
  
```  
SHAPE {SELECT CustomerID, ContactName FROM Customers}   
APPEND ({SELECT OrderID, OrderDate, CustomerID FROM Orders} AS chapOrders   
RELATE customerID TO customerID)   
```  
  
 Quando questo comando viene utilizzato per aprire un **Recordset** oggetto (come illustrato nella [Visual Basic esempio di Data Shaping](../../../ado/guide/data/visual-basic-example-of-data-shaping.md)), viene creato un capitolo (**chapOrders**) per ogni record restituito dal **clienti** tabella. In questo capitolo è costituito da un subset del **Recordset** restituito dal **ordini** tabella. Il **chapOrders** capitolo contiene tutte le informazioni richieste relative agli ordini effettuati dal cliente specificato. In questo esempio, il capitolo è costituito da tre colonne: **OrderID**, **OrderDate**, e **CustomerID**.  
  
 Le prime due voci di risultante a forma di **Recordset** sono i seguenti:  
  
|CustomerID|ContactName|OrderID|OrderDate|CustomerID|  
|----------------|-----------------|-------------|---------------|----------------|  
|ALFKI|Maria inferiore|10643<br /><br /> 10692<br /><br /> 10702<br /><br /> 10835<br /><br /> 10952<br /><br /> 11011|1997-08-25<br /><br /> 1997-10-03<br /><br /> 1997-10-13<br /><br /> 1998-01-15<br /><br /> 1998-03-16<br /><br /> 1998-04-09|ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI|  
|ANATR|Ana Trujillo|10308<br /><br /> 10625<br /><br /> 10759<br /><br /> 10926|1996-09-18<br /><br /> 1997-08-08<br /><br /> 1997-11-28<br /><br /> 1998-03-04|ANATR<br /><br /> ANATR<br /><br /> ANATR<br /><br /> ANATR|  
  
 In un comando SHAPE, Accodamento viene utilizzato per creare un elemento figlio **Recordset** correlate all'elemento padre **Recordset** (come restituito dal comando specifico del provider subito dopo la parola chiave forma descritta precedente) dalla clausola RELATE. L'elemento padre e figlio in genere hanno almeno una colonna in comune: il valore della colonna in una riga dell'elemento padre è identico al valore della colonna in tutte le righe dell'elemento figlio.  
  
 È possibile utilizzare i comandi di forma secondo: in particolare, per generare un elemento padre **Recordset** da un elemento figlio **Recordset**. I record figlio **Recordset** vengono raggruppati, in genere utilizzando la clausola BY e una riga viene aggiunto all'elemento padre **Recordset** per ogni gruppo risultante l'elemento figlio. Se la clausola BY viene omessa, l'elemento figlio **Recordset** verrà modulo padre e un singolo gruppo **Recordset** conterrà esattamente una riga. Ciò è utile per il calcolo di aggregazioni "totale complessivo" sull'intero figlio **Recordset**.  
  
 Il costrutto di comando forma consente inoltre di creare una forma a livello di programmazione **Recordset**. È quindi possibile accedere ai componenti del **Recordset** a livello di codice o tramite un controllo visual appropriato. Viene eseguito un comando di forma come qualsiasi testo comando ADO. Per ulteriori informazioni, vedere [forma comandi in genere](../../../ado/guide/data/shape-commands-in-general.md).  
  
 Indipendentemente dalla modalità padre **Recordset** è valido, sarà presente una colonna capitolo che viene utilizzata per essere correlata a un elemento figlio **Recordset**. Se si desidera, l'elemento padre **Recordset** può anche avere colonne che contengono funzioni di aggregazione (SUM, MIN, MAX e così via) sulle righe figlio. Sia l'elemento padre e figlio **Recordset** può includere colonne che contengono un'espressione sulla riga di **Recordset**, nonché le colonne che sono nuovi sia inizialmente vuota.  
  
 In questa sezione continua con l'argomento seguente.  
  
-   [Esempio di data shaping in Visual Basic](../../../ado/guide/data/visual-basic-example-of-data-shaping.md)
