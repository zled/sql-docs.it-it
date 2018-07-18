---
title: Creazione di tabelle di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- SQL Server Native Client OLE DB provider, tables
- DBCOLUMNDESC usage
- adding tables
- CreateTable function
ms.assetid: a7b8d142-d76a-44d9-a583-86ac5109fbe8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5809cf0f602072b0bf1174ded2ed2502f7d9c277
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423930"
---
# <a name="creating-sql-server-tables"></a>Creazione di tabelle di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone il **itabledefinition:: CreateTable** funzione, consentendo ai consumer di creare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle. I consumer utilizzano **CreateTable** per creare tabelle permanenti denominate consumer e tabelle permanenti o temporanee con nomi univoci generati dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client.  
  
 Quando il consumer chiama **itabledefinition:: CreateTable**, se il valore della proprietà DBPROP_TBL_TEMPTABLE è VARIANT_TRUE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client genera un nome di tabella temporanea per il consumer. Il consumer imposta il *pTableID* parametro delle **CreateTable** metodo su NULL. Le tabelle temporanee con nomi generati dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non vengono visualizzati nei **tabelle** set di righe, ma sono accessibili tramite il **IOpenRowset** interfaccia.  
  
 Quando gli utenti specificano il nome della tabella nel *pwszName* membro del *uName* union nel *pTableID* parametro, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client Crea un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella con lo stesso nome. Vengono applicati i vincoli di denominazione di tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il nome tabella può indicare una tabella permanente o una tabella temporanea locale o globale. Per altre informazioni, vedere [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md). Il *ppTableID* parametro può essere NULL.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client può generare i nomi delle tabelle permanenti o temporanee. Quando il consumer imposta il *pTableID* parametro su NULL e set *ppTableID* in modo che punti a un DBID valido\*, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce il nome generato del Nella tabella di *pwszName* membro del *uName* unione del DBID a cui fa riferimento il valore di *ppTableID*. Per creare una password temporanea, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelle denominate dal provider OLE DB Native Client, il consumer include la proprietà di tabella OLE DB DBPROP_TBL_TEMPTABLE in una proprietà di tabella impostata cui fa riferimento il *rgPropertySets* parametro. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider le tabelle temporanee denominate sono locali.  
  
 **CreateTable** restituisce DB_E_BADTABLEID se il *eKind* membro del *pTableID* parametro non indica DBKIND_NAME.  
  
## <a name="dbcolumndesc-usage"></a>Utilizzo di DBCOLUMNDESC  
 Il consumer può indicare un tipo di dati di colonna utilizzando il *pwszTypeName* membro o la *wType* membro. Se il consumer specifica il tipo di dati *pwszTypeName*, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client ignora il valore di *wType*.  
  
 Se si usa la *pwszTypeName* membro, il consumer specifica il tipo di dati tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i nomi del tipo di dati. I nomi dei tipi di dati validi sono quelli restituiti nella colonna TYPE_NAME del set di righe dello schema PROVIDER_TYPES.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client riconosce un subset di valori DBTYPE enumerati da OLE DB di *wType* membro. Per altre informazioni, vedere [Mapping di tipo di dati in ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).  
  
> [!NOTE]  
>  **CreateTable** restituisce DB_E_BADTYPE se il consumer imposta il il *pTypeInfo* oppure *pclsid* membro per specificare il tipo di dati di colonna.  
  
 Il consumer specifica il nome della colonna nel *pwszName* membro delle *uName* union di DBCOLUMNDESC *dbcid* membro. Il nome di colonna viene specificato come stringa di caratteri Unicode. Il *eKind* appartenente *dbcid* deve essere DBKIND_NAME. **CreateTable** restituisce DB_E_BADCOLUMNID se *eKind* non è valido *pwszName* è NULL, o se il valore del *pwszName* non è valida [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificatore.  
  
 Tutte le proprietà delle colonne sono disponibili in tutte le colonne definite per la tabella. **CreateTable** può restituire DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED se i valori delle proprietà vengono impostati in conflitto. **CreateTable** restituisce un errore quando impostazioni delle proprietà di colonne non valide provocano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errore di creazione tabella.  
  
 Le proprietà delle colonne in un parametro DBCOLUMNDESC vengono interpretate nel modo seguente.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE Descrizione: imposta la proprietà Identity nella colonna creata. Per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la proprietà Identity è valida per una singola colonna all'interno di una tabella. Impostazione della proprietà su VARIANT_TRUE per più di una singola colonna genera un errore durante il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client tenta di creare la tabella nel server.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proprietà identity è valida solo per il **integer**, **numerico**, e **decimal** tipi quando la scala è 0. Impostazione della proprietà su VARIANT_TRUE in una colonna di qualsiasi altro tipo di dati genera un errore durante il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client tenta di creare la tabella nel server.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce DB_S_ERRORSOCCURRED quando le proprietà DBPROP_COL_AUTOINCREMENT e DBPROP_COL_NULLABLE sono entrambe VARIANT_TRUE e il *dwOption* di DBPROP_COL_NULLABLE non è DBPROPOPTIONS_ Obbligatorio. DB_E_ERRORSOCCURRED viene restituito quando DBPROP_COL_AUTOINCREMENT e DBPROP_COL_NULLABLE sono entrambe VARIANT_TRUE e il *dwOption* di DBPROP_COL_NULLABLE è uguale a DBPROPOPTIONS_REQUIRED. La colonna viene definita con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proprietà di identità e di DBPROP_COL_NULLABLE *dwStatus* membro è impostato su DBPROPSTATUS_CONFLICTING.|  
|DBPROP_COL_DEFAULT|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: crea un vincolo DEFAULT di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la colonna.<br /><br /> Il *vValue* membro DBPROP può essere uno dei diversi tipi. Il *vValue* membro deve specificare un tipo compatibile con il tipo di dati della colonna. La definizione di BSTR N/A come valore predefinito per una colonna definita come DBTYPE_WSTR rappresenta una corrispondenza compatibile. Definire lo stesso valore predefinito su una colonna definita come DBTYPE_R8 genera un errore durante il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client tenta di creare la tabella nel server.|  
|DBPROP_COL_DESCRIPTION|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: La proprietà della colonna DBPROP_COL_DESCRIPTION non è implementata dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client.<br /><br /> Il *dwStatus* membro della struttura DBPROP restituisce DBPROPSTATUS_NOTSUPPORTED quando il consumer tenta di scrivere il valore della proprietà.<br /><br /> Impostazione della proprietà non costituisce un errore irreversibile per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client. Se tutti gli altri valori di parametro sono validi, viene creata la tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|DBPROP_COL_FIXEDLENGTH|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client utilizza DBPROP_COL_FIXEDLENGTH per determinare i mapping dei tipi di dati quando il consumer definisce un tipo di dati colonna usando la *wType* membro di DBCOLUMNDESC. Per altre informazioni, vedere [Mapping di tipo di dati in ITableDefinition](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md).|  
|DBPROP_COL_NULLABLE|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: La creazione della tabella, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client indica se la colonna deve accettare i valori null se la proprietà è impostata. Quando la proprietà non è impostata, la possibilità di accettare valori NULL per la colonna è determinata dall'opzione di database predefinita ANSI_NULLS di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client è un provider conforme allo standard ISO. Le sessioni connesse adottano comportamenti ISO. Se il consumer non imposta DBPROP_COL_NULLABLE, le colonne accettano valori Null.|  
|DBPROP_COL_PRIMARYKEY|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE descrizione: se impostata su VARIANT_TRUE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client crea la colonna con un vincolo PRIMARY KEY.<br /><br /> Se definita come proprietà della colonna, solo una singola colonna può determinare il vincolo. Impostazione della proprietà su VARIANT_TRUE per più di una singola colonna restituisce un errore quando la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client tenta di creare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella.<br /><br /> Nota: Il consumer può utilizzare **iindexdefinition:: CreateIndex** per creare un vincolo PRIMARY KEY in due o più colonne.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce DB_S_ERRORSOCCURRED quando le proprietà DBPROP_COL_PRIMARYKEY e DBPROP_COL_UNIQUE sono entrambe VARIANT_TRUE e il *dwOption* di DBPROP_COL_UNIQUE non è DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED viene restituito quando DBPROP_COL_PRIMARYKEY e DBPROP_COL_UNIQUE sono entrambe VARIANT_TRUE e il *dwOption* di DBPROP_COL_UNIQUE è uguale a DBPROPOPTIONS_REQUIRED. La colonna viene definita con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proprietà identity e il *dwStatus* membro è impostato su DBPROPSTATUS_CONFLICTING.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce un errore quando DBPROP_COL_PRIMARYKEY e DBPROP_COL_NULLABLE sono entrambe VARIANT_TRUE.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce un errore da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando il consumer tenta di creare un vincolo PRIMARY KEY in una colonna di valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati. Non è possibile definire vincoli PRIMARY KEY in colonne create con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati **bit**, **testo**, **ntext**, e **immagine**.|  
|DBPROP_COL_UNIQUE|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE Descrizione: applica un vincolo UNIQUE di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alla colonna.<br /><br /> Se è definita come proprietà della colonna, il vincolo viene applicato solo a una singola colonna. Il consumer può utilizzare **iindexdefinition:: CreateIndex** per applicare un vincolo UNIQUE nei valori combinati di due o più colonne.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce DB_S_ERRORSOCCURRED quando le proprietà DBPROP_COL_PRIMARYKEY e DBPROP_COL_UNIQUE sono entrambe VARIANT_TRUE e *dwOption* non è DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED viene restituito quando DBPROP_COL_PRIMARYKEY e DBPROP_COL_UNIQUE sono entrambe VARIANT_TRUE e *dwOption* è uguale a DBPROPOPTIONS_REQUIRED. La colonna viene definita con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proprietà identity e il *dwStatus* membro è impostato su DBPROPSTATUS_CONFLICTING.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce DB_S_ERRORSOCCURRED quando DBPROP_COL_NULLABLE e DBPROP_COL_UNIQUE sono entrambe VARIANT_TRUE e *dwOption* non è DBPROPOPTIONS_REQUIRED.<br /><br /> DB_E_ERRORSOCCURRED viene restituito quando DBPROP_COL_NULLABLE e DBPROP_COL_UNIQUE sono entrambe VARIANT_TRUE e *dwOption* è uguale a DBPROPOPTIONS_REQUIRED. La colonna viene definita con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proprietà di identità e di DBPROP_COL_NULLABLE *dwStatus* membro è impostato su DBPROPSTATUS_CONFLICTING.<br /><br /> Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce un errore da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando il consumer tenta di creare un vincolo UNIQUE in una colonna di valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati. Non è possibile definire vincoli UNIQUE in colonne create con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bit** tipo di dati.|  
  
 Quando il consumer chiama **itabledefinition:: CreateTable**, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client interpreta le proprietà di tabella, come indicato di seguito.  
  
|ID proprietà|Description|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|L/S: Lettura/Scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE descrizione: per impostazione predefinita, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client crea tabelle denominate dal consumer. Quando impostata su VARIANT_TRUE, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client genera un nome di tabella temporanea per il consumer. Il consumer imposta il *pTableID* del parametro **CreateTable** su NULL. Il *ppTableID* parametro deve contenere un puntatore valido.|  
  
 Se il consumer richiede che un set di righe aperto in una tabella è stata creata, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client consente di aprire un set di righe supportato dal cursore. Qualsiasi proprietà del set di righe può essere indicata nei set di proprietà passati.  
  
 In questo esempio viene creata una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
// This CREATE TABLE statement shows the details of the table created by   
// the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//    CONSTRAINT PK_OrderDetails  
//         PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
// The PRIMARY KEY constraint is created in an additional example.  
HRESULT CreateTable  
    (  
    ITableDefinition* pITableDefinition  
    )  
    {  
    DBID            dbidTable;  
    const ULONG     nCols = 5;  
    ULONG           nCol;  
    ULONG           nProp;  
    DBCOLUMNDESC    dbcoldesc[nCols];  
  
    HRESULT         hr;  
  
    // Set up column descriptions. First, set default property values for  
    //  the columns.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbcoldesc[nCol].pwszTypeName = NULL;  
        dbcoldesc[nCol].pTypeInfo = NULL;  
        dbcoldesc[nCol].rgPropertySets = new DBPROPSET;  
        dbcoldesc[nCol].pclsid = NULL;  
        dbcoldesc[nCol].cPropertySets = 1;  
        dbcoldesc[nCol].ulColumnSize = 0;  
        dbcoldesc[nCol].dbcid.eKind = DBKIND_NAME;  
        dbcoldesc[nCol].wType = DBTYPE_I4;  
        dbcoldesc[nCol].bPrecision = 0;  
        dbcoldesc[nCol].bScale = 0;  
  
        dbcoldesc[nCol].rgPropertySets[0].rgProperties =   
            new DBPROP[NCOLPROPS_MAX];  
        dbcoldesc[nCol].rgPropertySets[0].cProperties = NCOLPROPS_MAX;  
        dbcoldesc[nCol].rgPropertySets[0].guidPropertySet =  
            DBPROPSET_COLUMN;  
  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                dwOptions = DBPROPOPTIONS_REQUIRED;  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].colid  
                 = DB_NULLID;  
  
            VariantInit(  
                &(dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                    vValue));  
  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt = VT_BOOL;  
            }  
        }  
  
    // Set the column-specific information.  
    dbcoldesc[0].dbcid.uName.pwszName = L"OrderID";  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[0].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[1].dbcid.uName.pwszName = L"ProductID";  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[1].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[2].dbcid.uName.pwszName = L"UnitPrice";  
    dbcoldesc[2].wType = DBTYPE_CY;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[2].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[3].dbcid.uName.pwszName = L"Quantity";  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[3].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[4].dbcid.uName.pwszName = L"Discount";  
    dbcoldesc[4].wType = DBTYPE_NUMERIC;  
    dbcoldesc[4].bPrecision = 2;  
    dbcoldesc[4].bScale = 2;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].dwPropertyID =   
        DBPROP_COL_DEFAULT;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.vt = VT_BSTR;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.bstrVal =  
        SysAllocString(L"0");  
    dbcoldesc[4].rgPropertySets[0].cProperties = 2;  
  
    // Set up the dbid for OrderDetails.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    if (FAILED(hr = pITableDefinition->CreateTable(NULL, &dbidTable,  
        nCols, dbcoldesc, NULL, 0, NULL, NULL, NULL)))  
        {  
        DumpError(pITableDefinition, IID_ITableDefinition);  
        goto SAFE_EXIT;  
        }  
  
SAFE_EXIT:  
    // Clean up dynamic allocation in the property sets.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            if (dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt == VT_BSTR)  
                {  
                SysFreeString(dbcoldesc[nCol].rgPropertySets[0].  
                    rgProperties[nProp].vValue.bstrVal);  
                }  
            }  
  
        delete [] dbcoldesc[nCol].rgPropertySets[0].rgProperties;  
        delete [] dbcoldesc[nCol].rgPropertySets;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
