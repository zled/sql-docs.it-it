---
title: Informazioni sulle proprietà OLE DB | Microsoft Docs
description: Informazioni sulle proprietà OLE DB
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- OLE DB Driver for SQL Server, properties
- properties [OLE DB]
- property values [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 48d85439f485621d7967b72e1f3ddaf60f61ef4e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43018097"
---
# <a name="about-ole-db-properties"></a>Informazioni sulle proprietà OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  I consumer impostano i valori delle proprietà per richiedere specifici comportamenti degli oggetti. Utilizzano, ad esempio, proprietà per specificare le interfacce che devono essere esposte da un set di righe. I consumer recuperano i valori delle proprietà per determinare le funzionalità di un oggetto, ad esempio un set di righe, una sessione o un oggetto origine dati.  
  
 Ogni proprietà presenta un valore, un tipo, una descrizione e un attributo di lettura/scrittura e, per le proprietà del set di righe, un indicatore che specifica se la proprietà può essere applicata alle singole colonne.  
  
 Una proprietà viene identificata da un GUID e da un numero intero che rappresenta l'ID della proprietà. Un set di proprietà è un set di tutte le proprietà che condividono lo stesso GUID. Oltre ai set di proprietà OLE DB predefiniti, il driver OLE DB per SQL Server implementa proprietà e set di proprietà specifici del provider. Ogni proprietà appartiene a uno o più gruppi di proprietà. Un gruppo di proprietà è il gruppo di tutte le proprietà che si applicano a un particolare oggetto. Alcuni gruppi di proprietà includono i seguenti gruppi di proprietà: di inizializzazione, dell'origine dati, di sessione, del set di righe, di tabella e di colonna. In ognuno di questi gruppi sono presenti proprietà.  
  
 L'impostazione dei valori delle proprietà comporta:  
  
1.  Determinazione delle proprietà per le quali impostare i valori.  
  
2.  Determinazione dei set di proprietà che contengono le proprietà identificate.  
  
3.  Allocazione di una matrice di strutture DBPROPSET, una per ogni set di proprietà identificato.  
  
4.  Allocazione di una matrice di strutture DBPROP, una per ogni set di proprietà. Il numero di elementi di ogni matrice è il numero di proprietà (identificate nel passaggio 1) che appartengono al set di proprietà.  
  
5.  Inserimento di dati nella struttura DBPROP per ogni proprietà.  
  
6.  Inserimento di informazioni (GUID del set di proprietà, conteggio del numero di elementi e un puntatore alla matrice DBPROP corrispondente) nella struttura DBPROPSET per ogni set di proprietà.  
  
7.  Chiamata a un metodo per impostare proprietà e passaggio del conteggio e della matrice delle strutture DBPROPSET.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un driver OLE DB per applicazione SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [Proprietà (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
