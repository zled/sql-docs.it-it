---
title: Restituzione di parametri di matrice da Stored procedure | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 2018069b-da5d-4cee-a971-991897d4f7b5
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: edd159a04c069889568454c793523188160392ad
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="returning-array-parameters-from-stored-procedures"></a>Restituzione di parametri di matrice da Stored procedure
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 In Oracle 7.3, non è possibile per un tipo di Record PL/SQL, ad eccezione di accesso da un programma PL/SQL. Se una funzione o procedura nel pacchetto dispone di un argomento formale definito come un tipo di Record PL/SQL, non è possibile associare l'argomento formale come un parametro. Utilizzare il tipo di tabella PL/SQL nel Driver ODBC di Microsoft per Oracle per richiamare i parametri di matrice dalle procedure che contiene le sequenze di escape corretto.  
  
 Per richiamare la routine, usare la sintassi seguente:  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  Il \<max record richiesti > parametro deve essere maggiore o uguale al numero di righe presenti nel set di risultati. In caso contrario, Oracle restituisce un errore che viene passato all'utente dal driver.  
>   
>  I record di PL/SQL non possono essere usati come parametri di matrice. Ogni parametro di matrice può rappresentare solo una colonna di una tabella di database.  
  
 Nell'esempio seguente definisce un pacchetto che contiene due procedure che restituiscono set di risultati diversi e quindi fornisce due metodi per restituire i set di risultati dal pacchetto.  
  
## <a name="package-definition"></a>Definizione del pacchetto:  
  
```  
CREATE OR REPLACE PACKAGE SimplePackage AS  
  
TYPE t_id is TABLE of  NUMBER(5)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Course is TABLE of VARCHAR2(10)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Dept is TABLE of VARCHAR2(5)  
    INDEX BY BINARY_INTEGER;  
  
PROCEDURE proc1  
   (  
   o_id             OUT    t_id,  
   ao_course       OUT    t_Course,  
   ao_dept         OUT    t_Dept  
   );  
  
TYPE t_pk1Type1 IS TABLE OF VARCHAR2(100) INDEX BY BINARY_INTEGER;  
TYPE t_pk1Type2 IS TABLE OF NUMBER INDEX BY BINARY_INTEGER;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   );  
  
END SimplePackage;  
  
CREATE OR REPLACE PACKAGE BODY SimplePackage AS  
    PROCEDURE  proc1 ( o_id OUT t_id,  
    ao_course OUT t_Course, ao_dept OUT t_Dept   ) AS  
    BEGIN  
          o_id(1):= 200;  
          ao_course(1) :=  'M101';  
          ao_dept(1) :=  'EEE' ;  
  
          o_id(2) := 201;  
          ao_course(2) :=  'PHY320';  
          ao_dept(2) :=  'ECE' ;  
  
     END proc1;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   )  
AS  
   i   NUMBER;  
BEGIN  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg2(i) := 'Row Number ' || to_char(i);  
   END LOOP;  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg3(i) := i;  
   END LOOP;  
END proc2;  
END SimplePackage;  
```  
  
#### <a name="to-invoke-procedure-proc1"></a>Per richiamare procedure PROC1  
  
1.  Restituire tutte le colonne in un unico set di risultati:  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  Restituire ogni colonna come un unico set di risultati:  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     Restituisce tre set di risultati, uno per ogni colonna.  
  
#### <a name="to-invoke-procedure-proc2"></a>Per richiamare la routine PROC2  
  
1.  Restituire tutte le colonne in un unico set di risultati:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  Restituire ogni colonna come un unico set di risultati:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 Verificare che le applicazioni recupero tutti i set di risultati utilizzando il [SQLMoreResults](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) API. Per ulteriori informazioni, vedere il *riferimento per programmatori ODBC*.  
  
> [!NOTE]  
>  Nel Driver ODBC per Oracle versione 2.0, funzioni di Oracle che restituiscono matrici PL/SQL non possono essere utilizzate per restituire i set di risultati.
