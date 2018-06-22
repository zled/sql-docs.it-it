---
title: Destinazione recordset | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
caps.latest.revision: 47
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: bedd18c7aa79420c23c935058e4b23d584b6fa1a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062915"
---
# <a name="recordset-destination"></a>recordset - destinazione
  La destinazione recordset crea e popola un recordset ADO in memoria. La forma del recordset è definita dall'input della destinazione recordset in fase di progettazione.  
  
## <a name="configuration-of-the-recordset-destination"></a>Configurazione della destinazione recordset  
 Per configurare la destinazione recordset, è necessario specificare la variabile in cui è memorizzato il recordset ADO.  
  
 In fase di esecuzione, nella variabile di tipo Oggetto, specificata nella proprietà VariableName della destinazione recordset, viene scritto un recordset ADO. La variabile rende quindi disponibile il recordset all'esterno del flusso di dati, dove può essere utilizzato da script e altri elementi del pacchetto.  
  
 Questa origine include un solo input. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../common-properties.md)  
  
-   [Proprietà personalizzate della destinazione recordset](recordset-destination-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Usare una destinazione recordset](recordset-destination.md)  
  
  