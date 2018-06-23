---
title: L'accesso a tipi definiti dall'utente in ADO.NET | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
caps.latest.revision: 12
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f9df05bab46774ebd9e033c47565294ee9c46857
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35696732"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Accesso ai tipi definiti dall'utente in ADO .NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Tipi definiti dall'utente (UDT) vengono scritti utilizzando uno dei linguaggi supportati dal [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) che producono codice verificabile. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. I tipi definiti dall'utente consentono l'archiviazione di oggetti e strutture di dati personalizzate in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I dati vengono esposti come membri pubblici di una classe o struttura .NET mentre i comportamenti vengono definiti dai metodi della classe o della struttura. Un tipo definito dall'utente può essere utilizzato come definizione di colonna di una tabella, come una variabile in un [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, o come un argomento di un [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure o funzione.  
  
 In ADO.NET, il **SqlClient** provider espone i tipi definiti dall'utente nei modi seguenti:  
  
-   Tramite il **System.Data.SqlClient.SqlDataReader** come oggetto.  
  
-   Tramite il **SqlDataReader** come byte non elaborati.  
  
-   Come parametro di un **SqlParameter** oggetto.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Il recupero dei dati di tipo definito dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Viene illustrato come recuperare i dati dei tipi definiti dall'utente e come specificare i parametri.  
  
 [L'aggiornamento delle colonne di tipo definito dall'utente con DataAdapter](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Viene descritto come utilizzare i tipi definiti dall'utente in **DataSet** e su come aggiornare i dati di tipo definito dall'utente utilizzando **DataAdapter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi definiti dall'utente per CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
