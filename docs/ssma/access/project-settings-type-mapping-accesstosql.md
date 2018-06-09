---
title: Impostazioni (Mapping dei tipi) del progetto (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bd5bc6a0db71d2836c068a261681d813bc2011b3
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34774467"
---
# <a name="project-settings-type-mapping-accesstosql"></a>Impostazioni (Mapping dei tipi) del progetto (AccessToSQL)
Le impostazioni di Mapping dei tipi del progetto consentono di impostare i mapping dei tipi predefiniti per il progetto SSMA. È inoltre possibile specificare i mapping dei tipi per singoli oggetti di database. Per ulteriori informazioni, vedere [Mapping tipi di origine e destinazione dati](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9).  
  
Mapping dei tipi è disponibile nel **impostazioni progetto** e **impostazioni di progetto predefinite** finestre di dialogo:  
  
-   Utilizzare il **impostazioni progetto** la finestra di dialogo per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di mapping di tipo, nel **strumenti** dal menu **impostazioni progetto**e quindi fare clic su **Mapping dei tipi** nel riquadro a sinistra.  
  
-   Utilizzare il **impostazioni di progetto predefinite** la finestra di dialogo per impostare le opzioni di configurazione per tutti i progetti. Per accedere alle impostazioni di mapping di tipo, nel **strumenti** dal menu **impostazioni di progetto predefinite**, selezionare il tipo di progetto di migrazione per i quali impostazioni sono necessarie per essere visualizzati o modificati da **versione di destinazione della migrazione** elenco a discesa e quindi fare clic su **Mapping dei tipi** nel riquadro a sinistra.  
  
## <a name="options"></a>Opzioni  
**Tipo origine**  
Il tipo di dati di accesso per eseguire il mapping.  
  
**Tipo di destinazione**  
La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tipo di dati di SQL Azure per il tipo di dati di accesso specificato.  
  
Nella tabella seguente viene illustrato il mapping predefinito tra i tipi di dati di origine e di destinazione.  
  
|Tipo di dati di accesso|Tipo di dati di SQL Server|  
|--------------------|------------------------|  
|**binario [\*... \*]**|**varbinary [\*]**|  
|**boolean**|**bit**|  
|**Byte**|**tinyint**|  
|**Valuta**|**money**|  
|**data**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**guid**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**Long**|**int**|  
|**longbinary**|**varbinary(max)**|  
|**memo**|**nvarchar(max)**|  
|**Memo** - per Access 97|**ntext**|  
|**Singolo**|**real**|  
|**testo [\*... \*]**|**nvarchar [\*]**|  
|**testo [\*... \*]** - per Access 97|**varchar [\*]**|  
  
**Aggiungi**  
Fare clic per aggiungere un tipo di dati nell'elenco di mapping.  
  
**Modifica**  
Fare clic per modificare un tipo di dati nell'elenco di mapping.  
  
**Rimuovi**  
Fare clic per rimuovere il mapping dei tipi di dati selezionato dall'elenco di mapping.  
  
**Ripristina predefiniti**  
Fare clic per reimpostare tutti i mapping dei tipi di dati di SSMA predefinite.  
  
## <a name="see-also"></a>Vedere anche  
[Mapping dei tipi di dati origine e destinazione](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9)  
[Reference(Access) dell'interfaccia utente](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
