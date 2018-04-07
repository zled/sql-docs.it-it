---
title: Esecuzione di Stored procedure (OLE DB) | Documenti Microsoft
description: Esecuzione di stored procedure (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea2d2faf2626ef4a2b0a01282471618ea34087c1
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="stored-procedures---running"></a>Stored procedure - esecuzione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Durante l'esecuzione di istruzioni, la chiamata a una stored procedure nell'origine dati, in alternativa all'esecuzione o alla preparazione diretta di un'istruzione nell'applicazione client, può offrire i vantaggi seguenti:  
  
-   Prestazioni più elevate.  
  
-   Overhead di rete ridotto.  
  
-   Maggiore consistenza.  
  
-   Maggiore precisione.  
  
-   Maggior numero di funzionalità.  
  
 Il Driver OLE DB per SQL Server supporta tre dei meccanismi che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzano stored procedure per restituire dati:  
  
-   Ogni istruzione SELECT nella procedura genera un set di risultati.  
  
-   La procedura può restituire dati tramite parametri di output.  
  
-   La procedura può avere un codice restituito di tipo integer.  
  
 L'applicazione deve essere in grado di gestire tutti questi output dalle stored procedure.  
  
 Provider OLE DB diversi restituiscono parametri di output e valori in momenti diversi durante l'elaborazione dei risultati. In caso del Driver OLE DB per SQL Server, i parametri di output e codici restituiti non vengono forniti fino a quando il consumer ha recuperato o annullato i set di risultati restituiti dalla stored procedure. I codici e i parametri di output vengono restituiti nell'ultimo pacchetto TDS dal server.  
  
 I provider utilizzano la proprietà DBPROP_OUTPUTPARAMETERAVAILABILITY per segnalare la restituzione di parametri di output e valori. Questa proprietà è inclusa nel set di proprietà DBPROPSET_DATASOURCEINFO.  
  
 Il Driver OLE DB per SQL Server imposta la proprietà DBPROP_OUTPUTPARAMETERAVAILABILITY su DBPROPVAL_OA_ATROWRELEASE per indicare che i codici restituiti e parametri di output non vengono restituiti fino a quando il set di risultati viene elaborato o rilasciato.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure](../../oledb/ole-db/stored-procedures.md)  
  
  
