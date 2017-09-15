---
title: "Proprietà dinamiche ADO | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic properties [ADO]
- properties [ADO], dynamic
ms.assetid: d7b06d72-f792-4328-93a2-5006b9e2c581
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fca9f032f5a72df58b18206c8441365ce3c8a746
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="ado-dynamic-properties"></a>Proprietà dinamiche ADO
Possono essere aggiunte le proprietà dinamiche di [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insiemi di [connessione](../../../ado/reference/ado-api/connection-object-ado.md), [comando](../../../ado/reference/ado-api/command-object-ado.md), o [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti. L'origine per queste proprietà è di provider di dati, ad esempio il [il Provider OLE DB per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), o un provider di servizi, ad esempio il [servizio cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md). Consultare la documentazione di provider del servizio per ulteriori informazioni su una proprietà dinamica specifica o un provider di dati appropriato.  
  
 Il [ADO Dynamic Property Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md) fornisce un riferimento incrociato tra i nomi ADO e OLE DB per ogni proprietà dinamica di provider OLE DB standard.  
  
 Le proprietà dinamiche seguenti sono particolarmente interessanti e sono documentate anche nelle origini indicate in precedenza. Funzionalità speciali con ADO è documentata negli argomenti della Guida ADO nell'elenco seguente.  
  
|||  
|-|-|  
|[Ottimizzazione](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)|Specifica se è necessario creare un indice su questo campo.|  
|[Richiesta](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)|Specifica se il provider OLE DB deve richiedere all'utente le informazioni di inizializzazione.|  
|[Modificare la forma di nome](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)|Specifica un nome per il **Recordset** oggetto.|  
|[Risincronizzazione di comando](../../../ado/reference/ado-api/resync-command-property-dynamic-ado.md)|Specifica una stringa di un comando fornito dall'utente di **Resync** i problemi dei metodi di aggiornamento dei dati nella tabella denominata nel **tabella univoca** proprietà dinamiche.|  
|[Tabella univoca, univoco dello Schema, catalogo univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md)|**Tabella univoca** specifica il nome della tabella di base su cui sono consentite aggiornamenti, inserimenti ed eliminazioni.<br /><br /> **Schema univoco** specifica lo schema, o nome del proprietario della tabella.<br /><br /> **Catalogo univoca** specifica il catalogo o nome del database che contiene la tabella.|  
|[Risincronizzazione di aggiornamento](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md)|Specifica se il **UpdateBatch** metodo è seguito da implicita **Resync** operazione del metodo e in tal caso, l'ambito dell'operazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Raccolte di ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Costanti enumerate ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Appendice b: errori ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Eventi ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Metodi ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Le interfacce e gli oggetti ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Proprietà ADO](../../../ado/reference/ado-api/ado-properties.md)
