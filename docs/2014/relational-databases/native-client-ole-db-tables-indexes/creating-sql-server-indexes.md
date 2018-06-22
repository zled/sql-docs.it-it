---
title: Creazione di indici SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fa0d11ced42d58b7c1b75c2aef7755cbf64b7b69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063102"
---
# <a name="creating-sql-server-indexes"></a>Creazione di indici SQL Server
  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone il **iindexdefinition:: CreateIndex** funzione, che consente agli utenti di definire nuovi indici nelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client crea indici di tabella come indici o vincoli. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce privilegio di creazione del vincolo al proprietario della tabella, del database e ai membri di determinati ruoli amministrativi. Per impostazione predefinita, solo il proprietario di tabella può creare un indice in una tabella. Pertanto, l'esito positivo o negativo del **CreateIndex** dipende non solo i diritti di accesso dell'utente dell'applicazione, ma anche sul tipo di indice creato.  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pTableID* parametro. Il *eKind* appartenente *pTableID* deve essere DBKIND_NAME.  
  
 Il *pIndexID* parametro può essere NULL e se è, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client crea un nome univoco per l'indice. Il consumer può acquisire il nome dell'indice specificando un puntatore valido a un DBID nel *ppIndexID* parametro.  
  
 Il consumer può specificare il nome dell'indice come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione del *pIndexID* parametro. Il *eKind* appartenente *pIndexID* deve essere DBKIND_NAME.  
  
 Il consumer specifica la colonna o le colonne utilizzate nell'indice in base al nome. Per ogni struttura DBINDEXCOLUMNDESC utilizzata in **CreateIndex**, la *eKind* appartenente il *pColumnID* deve essere DBKIND_NAME. Il nome della colonna viene specificato come stringa di caratteri Unicode nel *pwszName* appartenente il *uName* unione nel *pColumnID*.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider OLE DB e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporto ordine crescente nei valori nell'indice. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce E_INVALIDARG se il consumer specifica DBINDEX_COL_ORDER_DESC in una qualsiasi struttura DBINDEXCOLUMNDESC.  
  
 **CreateIndex** interpreta le proprietà di indice come indicato di seguito.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta questa proprietà. Tenta di impostare la proprietà **CreateIndex** causano un valore restituito DB_S_ERRORSOCCURRED. Il *dwStatus* membro della struttura di proprietà indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_CLUSTERED|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: controlla il clustering dell'indice.<br /><br /> VARIANT_TRUE: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client tenta di creare un indice cluster sul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta al massimo un indice con cluster su una tabella.<br /><br /> VARIANT_FALSE: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client tenta di creare un indice non cluster per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.|  
|DBPROP_INDEX_FILLFACTOR|L/S: Lettura/Scrittura<br /><br /> Predefinito: 0<br /><br /> Descrizione: specifica la percentuale di una pagina di indice utilizzata per l'archiviazione. Per altre informazioni, vedere [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql).<br /><br /> Il tipo della variante è VT_I4. Deve essere maggiore o uguale a 1 e minore o uguale a 100.|  
|DBPROP_INDEX_INITIALIZE|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta questa proprietà. Tenta di impostare la proprietà **CreateIndex** causano un valore restituito DB_S_ERRORSOCCURRED. Il *dwStatus* membro della struttura di proprietà indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLCOLLATION|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta questa proprietà. Tenta di impostare la proprietà **CreateIndex** causano un valore restituito DB_S_ERRORSOCCURRED. Il *dwStatus* membro della struttura di proprietà indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLS|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta questa proprietà. Tenta di impostare la proprietà **CreateIndex** causano un valore restituito DB_S_ERRORSOCCURRED. Il *dwStatus* membro della struttura di proprietà indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_PRIMARYKEY|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: descrizione VARIANT_FALSE: crea l'indice come integrità referenziale, vincolo PRIMARY KEY.<br /><br /> VARIANT_TRUE: l'indice viene creato per supportare il vincolo PRIMARY KEY della tabella. È necessario che le colonne non ammettano valori Null.<br /><br /> VARIANT_FALSE: l'indice non viene utilizzato come vincolo PRIMARY KEY per i valori di riga nella tabella.|  
|DBPROP_INDEX_SORTBOOKMARKS|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta questa proprietà. Tenta di impostare la proprietà **CreateIndex** causano un valore restituito DB_S_ERRORSOCCURRED. Il *dwStatus* membro della struttura di proprietà indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TEMPINDEX|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta questa proprietà. Tenta di impostare la proprietà **CreateIndex** causano un valore restituito DB_S_ERRORSOCCURRED. Il *dwStatus* membro della struttura di proprietà indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TYPE|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta questa proprietà. Tenta di impostare la proprietà **CreateIndex** causano un valore restituito DB_S_ERRORSOCCURRED. Il *dwStatus* membro della struttura di proprietà indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_UNIQUE|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: crea l'indice come vincolo UNIQUE nella colonna o nelle colonne utilizzate.<br /><br /> VARIANT_TRUE: l'indice viene utilizzato per vincolare in modo univoco i valori della tabella.<br /><br /> VARIANT_FALSE: l'indice non vincola in modo univoco i valori di riga.|  
  
 Nel provider specifici set di proprietà DBPROPSET_SQLSERVERINDEX il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client definisce la seguente proprietà di informazioni di origine dati.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|Tipo: VT_BOOL (L/S)<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: quando questa proprietà viene specificata con un valore VARIANT_TRUE con IIndexDefinition::CreateIndex, determina la creazione di un indice xml primario corrispondente alla colonna indicizzata. Se questa proprietà è VARIANT_TRUE, cIndexColumnDescs deve essere 1, in caso contrario si tratta di un errore.|  
  
 In questo esempio viene creato un indice di chiave primaria:  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
