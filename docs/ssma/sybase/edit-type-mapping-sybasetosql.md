---
title: Modificare i Mapping dei tipi (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 513f071a-d5e6-4ed5-acca-269bf76323c5
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e1b11fde38d4a7dce1a7a3f2f1ccdd47091c440
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="edit-type-mapping-sybasetosql"></a>Modificare i Mapping dei tipi (SybaseToSQL)
Il **modifica del Mapping di tipo** la finestra di dialogo consente di specificare la modalità di mapping dei tipi tra gli oggetti di database di origine e di destinazione.  
  
È possibile accedere a questa finestra di dialogo in diverse posizioni:  
  
-   Quando si seleziona un database di origine o di un oggetto di database, il **del mapping dei tipi** scheda viene visualizzata a destra del Visualizzatore metadati. Fare clic su **Aggiungi** per aggiungere un nuovo mapping dei tipi oppure fare clic su **modifica** per modificare un mapping del tipo esistente.  
  
-   Nel **strumenti** dal menu **impostazioni progetto** o **impostazioni di progetto predefinite**. Nella finestra di dialogo risultante selezionare **del mapping dei tipi**. Fare clic su **Aggiungi** per aggiungere un nuovo mapping dei tipi oppure fare clic su **modifica** per modificare un mapping del tipo esistente.  
  
Mapping dei tipi specifici della tabella di database di eseguire l'override e mapping dei tipi di progetto. Mapping specifico del database di eseguire l'override dei mapping project.  
  
## <a name="options"></a>Opzioni  
**Tipo di origine**  
Selezionare il tipo di dati di origine per eseguire il mapping a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati.  
  
Se il tipo di dati è di lunghezza variabile, i campi seguenti verranno visualizzati in **tipo di origine**:  
  
**From**  
Specificare la lunghezza minima per questo mapping. Ad esempio, per il **nchar** tipo di dati, è possibile immettere 10 per specificare che il mapping è per un intervallo a partire da **nchar (10)**.  
  
**Per**  
Specificare la lunghezza massima per questa associazione. Ad esempio, per il **nchar** tipo di dati, è possibile immettere 20 per specificare che il mapping è per un intervallo termina **nchar(20)**.  
  
**Tipo di destinazione**  
Selezionare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] il tipo di dati a cui è mappato il tipo di dati di origine. Quando SSMA crea la tabella o una stored procedure in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], verrà modificato il tipo di dati di origine per questo tipo di dati.  
  
Se il tipo di dati è di lunghezza variabile, il seguente campo verrà visualizzato in **tipo di destinazione**:  
  
**Replace with**  
Specificare la lunghezza di destinazione per questo mapping. Ad esempio, per il **nvarchar** tipo di dati, è possibile immettere 20 per specificare che il tipo di dati di origine specificato deve essere mappato a **nvarchar (20)**.  
  
