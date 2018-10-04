---
title: Pulsanti di Address Book navigazione | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS scenarios [ADO], navigation buttons
- address book application scenario [ADO], navigation buttons
ms.assetid: f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be8020f5a9ce826fbe4f92864d8d580bbcb6ae5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696940"
---
# <a name="address-book-navigation-buttons"></a>Pulsanti di spostamento di Address Book
L'applicazione Address Book Visualizza i pulsanti di navigazione nella parte inferiore della pagina Web. È possibile utilizzare i pulsanti di navigazione per spostarsi tra i dati nella visualizzazione della griglia HTML selezionando prima o ultima riga di dati o righe adiacenti per la selezione corrente.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="navigation-sub-procedures"></a>Navigazione Sub (routine)  
 L'applicazione Address Book contiene varie procedure che consentono agli utenti di scegliere il **prima**, **successiva**, **Indietro**, e **ultimo** pulsanti per spostarsi tra i dati.  
  
 Ad esempio, è sufficiente scegliere il **primo** pulsante viene attivata la Sub First_OnClick VBScript. La routine viene eseguita una [MoveFirst](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) metodo, che rende la prima riga di dati della selezione corrente. Facendo clic sui **ultima** pulsante Attiva la routine Sub Last_OnClick, che consente di visualizzare i [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) metodo, rendendo l'ultima riga di dati della selezione corrente. Gli altri pulsanti di spostamento funzionano in modo analogo.  
  
```  
' Move to the first record in the bound Recordset.  
Sub First_OnClick  
   DC1.Recordset.MoveFirst  
End Sub  
  
' Move to the next record from the current position   
' in the bound Recordset.  
Sub Next_OnClick  
   If Not DC1.Recordset.EOF Then    ' Cannot move beyond bottom record.  
      DC1.Recordset.MoveNext  
      Exit Sub  
   End If     
End Sub  
  
' Move to the previous record from the current position in the bound   
' Recordset.  
Sub Prev_OnClick  
   If Not DC1.Recordset.BOF Then    ' Cannot move beyond top record.  
      DC1.Recordset.MovePrevious  
      Exit Sub  
   End If  
End Sub  
  
' Move to the last record in the bound Recordset.  
Sub Last_OnClick  
   DC1.Recordset.MoveLast  
End Sub  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Metodi MoveFirst, MoveLast, MoveNext e MovePrevious (Servizi Desktop remoto)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)



