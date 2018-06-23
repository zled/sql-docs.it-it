---
title: L'accesso a tipi definiti dall'utente in ADO.NET | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c4266cde6caa32aaee9eeabc5ead52dfd94bbd14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156940"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Accesso ai tipi definiti dall'utente in ADO .NET
  Tipi definiti dall'utente (UDT) vengono scritti utilizzando uno dei linguaggi supportati dal [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) che producono codice verificabile. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. I tipi definiti dall'utente consentono l'archiviazione di oggetti e strutture di dati personalizzate in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I dati vengono esposti come membri pubblici di una classe o struttura .NET mentre i comportamenti vengono definiti dai metodi della classe o della struttura. Un tipo definito dall'utente può essere utilizzato come definizione di colonna di una tabella, come una variabile in un [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, o come un argomento di un [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure o funzione.  
  
 In ADO.NET il provider `System.Data.SqlClient` espone i tipi definiti dall'utente nei modi seguenti:  
  
-   Mediante `System.Data.SqlClient.SqlDataReader` come oggetto.  
  
-   Mediante `SqlDataReader` come byte non elaborati.  
  
-   Come parametro di un oggetto `System.Data.SqlClient.SqlParameter`.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Il recupero dei dati di tipo definito dall'utente](accessing-user-defined-types-retrieving-udt-data.md)  
 Viene illustrato come recuperare i dati dei tipi definiti dall'utente e come specificare i parametri.  
  
 [L'aggiornamento delle colonne di tipo definito dall'utente con DataAdapter](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Viene illustrato come utilizzare i tipi definiti dall'utente in `DataSets` e come aggiornarli utilizzando `DataAdapters`.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi definiti dall'utente per CLR](clr-user-defined-types.md)  
  
  