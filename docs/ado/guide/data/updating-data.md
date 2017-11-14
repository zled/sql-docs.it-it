---
title: L'aggiornamento dei dati | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8138aeea7e5ea40e659a6fed5f5d5f551b1c69d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="updating-data"></a>Aggiornamento dei dati
Comportamento di aggiornamento e le funzionalità non dipendono in gran parte di aggiornamento modalità (tipo di blocco), tipo di cursore e posizione del cursore.  
  
 Utilizzare il **aggiornamento** per salvare le modifiche apportate al record corrente di un **Recordset** oggetto dopo la chiamata di **AddNew** (metodo) o dopo la modifica dei valori di campo in un record esistente. Il **Recordset** oggetto deve supportare gli aggiornamenti.  
  
 Se il **Recordset** oggetto supporta l'aggiornamento in batch, è possibile memorizzare nella cache più modifiche a uno o più record localmente finché non si chiama il **UpdateBatch** metodo. Se si modifica il record corrente o aggiungendo un nuovo record quando si chiama il **UpdateBatch** (metodo), ADO chiamerà automaticamente il **aggiornamento** per salvare le modifiche in sospeso per il record corrente prima di trasmettere le modifiche in blocco al provider.  
  
 Il record corrente rimane invariato dopo la chiamata di **aggiornamento** o **UpdateBatch** metodi.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Modalità immediata](../../../ado/guide/data/immediate-mode.md)  
  
-   [Modalità batch](../../../ado/guide/data/batch-mode.md)  
  
-   [Elaborazione delle transazioni](../../../ado/guide/data/transaction-processing.md)

