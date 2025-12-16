# utl-altair-slc-chapter-III-verifying-training-logistic-using-holdout
Altair slc chapter III verifying training logistic using holdout
    %let pgm=utl-altair-slc-chapter-III-verifying-training-logistic-using-holdout;

    %stop_submission;

    Altair slc chapter III verifying training logistic using holdout

    Too long to pos on a listserve, see github

    github
    https://github.com/rogerjdeangelis/utl-altair-slc-chapter-III-verifying-training-logistic-using-holdout

    github verification lify cpmparison
    https://github.com/rogerjdeangelis/utl-altair-slc-chapter-III-verifying-training-logistic-using-holdout/blob/main/liftplots.png

      CONTENTS

         1  Best Model from Chater II
            RESPONSE =_MARRIED _ACSGENDER _DIVISIONCDE _INCOME _LOANHOME

         2  Training Logistic

         3  Create SAS code to bin variables
            Basically, If then else code that will bin the Holdout sample.
            Code is created using the binning done by the optimalbin macro on the training data.

         4  Map char vars  (create sas if then code)

         5  Map num vars   (create sas if then code)

         6  Applly if then elses to holdout to bin data

         7  Run logistic on holdout sample  \

         8  Rank probabilities and modeled probablities

         9  Verify training logistic using holdout

        10  Compare Lift plots Training and Holdout

        11  Ascii plot verification of Training and Holdout

        12  Output datasets

    /*              _  __ _           _   _                     _       _
    __   _____ _ __(_)/ _(_) ___ __ _| |_(_) ___  _ __    _ __ | | ___ | |_ ___
    \ \ / / _ \ `__| | |_| |/ __/ _` | __| |/ _ \| `_ \  | `_ \| |/ _ \| __/ __|
     \ V /  __/ |  | |  _| | (_| (_| | |_| | (_) | | | | | |_) | | (_) | |_\__ \
      \_/ \___|_|  |_|_| |_|\___\__,_|\__|_|\___/|_| |_| | .__/|_|\___/ \__|___/
                                                         |_|
    Its had to beast a table with fancy plots?
    */

          Plot of Probability*Decile$ltr.

                                     Decile
                   1    2    3    4    5    6    7    8    9   10
                ---+----+----+----+----+----+----+----+----+----+---
    Probability |                                                  |
                |  Comparison Using the Model Probabilities        |
           0.45 +  add 1 to count each sum of predicted increases  + 0.45
                |  by one save use the count for each decile    T  |
                |                                               H  |
                |  Decile   Sample   Probability                   |
                |                                H=Holdout         |
           0.40 +     1   Difference    0.00134                    + 0.40
                |     2   Difference    0.00076  T=Training        |
                |     3   Difference    0.00005                    |
                |     4   Difference   -0.00126  D=Difference      |
                |     5   Difference    0.00089                    |
           0.35 +     6   Difference    0.00127                    + 0.35
                |     7   Difference   -0.00384                    |
                |     8   Difference   -0.00297           HT       |
                |     9   Difference   -0.00385                    |
                |    10   Difference    0.00762                    |
           0.30 +                                                  + 0.30
                |     1   Holdout       0.01587                    |
                |     2   Holdout       0.03175                    |
                |     3   Holdout       0.03628                    |
                |     4   Holdout       0.03855                    |
           0.25 +     5   Holdout       0.04308                    + 0.25
                |     6   Holdout       0.05896                    |
                |     7   Holdout       0.07937                    |
                |     8   Holdout       0.10431                    |
                |     9   Holdout       0.15873                    |
           0.20 +    10   Holdout       0.43311                    + 0.20
                |                                                  |
                |     1   Training      0.01721                    |
                |     2   Training      0.03250                    |
                |     3   Training      0.03633      H             |
           0.15 +     4   Training      0.03728      T             + 0.15
                |     5   Training      0.04398                    |
                |     6   Training      0.06023                    |
                |     7   Training      0.07553                    |
                |     8   Training      0.10134                    |
           0.10 +     9   Training      0.15488     HT             + 0.10
                |    10   Training      0.44073                    |
                |                                H                 |
                |                                                  |
                |                           TH                     |
           0.05 +                      T                           + 0.05
                |            H    T    H                           |
                |       T    T                                     |
                |  H                                               |
                |                                               D  |
           0.00 +  D    D    D    D    D    D    D    D    D       + 0.00
                |                                                  |
                ---+----+----+----+----+----+----+----+----+----+---
                   1    2    3    4    5    6    7    8    9   10

                                       Decile


          Plot of Probability*Decile$ltr

                                     Decile
                   1    2    3    4    5    6    7    8    9   10
                ---+----+----+----+----+----+----+----+----+----+---
    Probability |                                                  |
                |                                                  |
           0.50 +                                                  +  0.50
                | Decile    Sample    Probability                  |
                |                                                  |
                |    1    Difference     0.00012                   |
           0.45 +    2    Difference     0.00820                H  +  0.45
                |    3    Difference    -0.01288                T  |
                |    4    Difference    -0.01835                   |
                |    5    Difference    -0.01379                   |
           0.40 +    6    Difference     0.00775                   +  0.40
                |    7    Difference     0.01553                   |
                |    8    Difference     0.01333                   |
                |    9    Difference     0.01875                   |
           0.35 +   10    Difference    -0.01866                   +  0.35
                |                                                  |
                |    1    Holdout        0.01806                   |
                |    2    Holdout        0.00903                   |
           0.30 +    3    Holdout        0.04063                   +  0.30
                |    4    Holdout        0.04515                   |
                |    5    Holdout        0.06546                   |
                |    6    Holdout        0.04966                   |
           0.25 +    7    Holdout        0.06772                   +  0.25
                |    8    Holdout        0.09481                   |
                |    9    Holdout        0.15350                   |
                |                   |
           0.20 +   10    Holdout        0.45598                   +  0.20
                |    1    Training       0.01818                   |
                |    2    Training       0.01722           T       |
                |    3    Training       0.02775                   |
           0.15 +    4    Training       0.02679           H       +  0.15
                |    5    Training       0.05167                   |
                |    6    Training       0.05742                   |
                |    7    Training       0.08325      T            |
           0.10 +    8    Training       0.10813      H            +  0.10
                |    9    Training       0.17225   T               |
                |   10    Training       0.43732                   |
                |                      H    T    H                 |
           0.05 +                 H    T    H                      +  0.05
                |            H                                     |
                |            T    T                                |
                |  T    T                   D    D    D    D       |
           0.00 +  D                                               +  0.00
                |            D    D    D                        D  |
                |                                                  |
                |                                                  |
          -0.05 +                                                  + -0.05
                |                                                  |
                ---+----+----+----+----+----+----+----+----+----+---
                   1    2    3    4    5    6    7    8    9   10
                                       Decile



    /*                   _
    (_)_ __  _ __  _   _| |_ ___
    | | `_ \| `_ \| | | | __/ __|
    | | | | | |_) | |_| | |_\__ \
    |_|_| |_| .__/ \__,_|\__|___/
            |_|
    */

    see chapter I
    https://github.com/rogerjdeangelis/utl-altair-slc-chapter-I-optimum-binning-in-preparation-for-logistic-regression

       DESCRIPTION                   OBS      TABLE                             COMMENT

    1.  RAW TRAINING (no binning)    70,000   d/:lgs/lgs_rawTrain.sas7bdat
    2.  RAW HOLDOUT  (no binning)    30,000   d/:lgs/lgs_rawHold.sas7bdat
    3.  LOGISTIC INPUT BINNED        70,000   d/:lgs/lgs_MgmAllChrNum.sas7bdat
    4.  NORMAILIZED CHAR BINNED     980,000   d:/lgs/lgs_mgmNrmChr.sas7bdat     14 vars*70000 observation
    5.  NORMAILIZED NUM  BINNED     910,000   d:/lgs/lgs_mgmNrmNumSrt.sas7bdat  13 vars*70000 observation
    6   CHR EXCEL REPORT INPUT          40    d:/lgs/lgs_mgmChrCutRpt           14 vars 40 obs
    7   NUM EXCEL REPORT INPUT          46    d:/lgs/lgs_mgmNumCut              13 vars 46 obs

    Chapter II

    1 Top 100 4-7 predictor models   2,200    d:/lgs/LGS_POSMGMMODNRM           4*100 + 5*100 + 6*100 + 7*100 = 2,200

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_ ___
     / _ \| | | | __| `_ \| | | | __/ __|
    | (_) | |_| | |_| |_) | |_| | |_\__ \
     \___/ \__,_|\__| .__/ \__,_|\__|___/
                    |_|
    */

    CHAPTER III

    1 TRAINING vs HOLDOUT Plot and table Verification  d:/lgs/lgs_liftnormalized.sas7bdat
    1 TRAINING vs HOLDOUT Plot and table Verification  d:/lgs/lgs_liftdenormalized.sas7bdat


    /*   _               _                         _      _
    / | | |__   ___  ___| |_   _ __ ___   ___   __| | ___| |
    | | | `_ \ / _ \/ __| __| | `_ ` _ \ / _ \ / _` |/ _ \ |
    | | | |_) |  __/\__ \ |_  | | | | | | (_) | (_| |  __/ |
    |_| |_.__/ \___||___/\__| |_| |_| |_|\___/ \__,_|\___|_|

    */

    /*--- WE ARE GOING TO USE THE BEST TOP 5 PARAMETER MODEL FROM CHAPTER II ---*/

    libname lgs sas7bdat "d:/lgs";
    proc print data=lgs.lgs_posmgmmodnrm(where=(ins=5 and cnt=1));
    run;quit;

    Altair SLC

    Altair SLC

    Obs    INS        RSQ         CNT        NAM             VAL

    401     5     0.0228672865     1     _MARRIED        0.0072914124
    402     5     0.0228672865     1     _ACSGENDER      0.0069123531
    403     5     0.0228672865     1     _DIVISIONCDE    0.0136691768
    404     5     0.0228672865     1     _INCOME         0.0113035035
    405     5     0.0228672865     1     _LOANHOME       0.0063074151


    /*___   _             _       _               _             _     _   _
    |___ \ | |_ _ __ __ _(_)_ __ (_)_ __   __ _  | | ___   __ _(_)___| |_(_) ___
      __) || __| `__/ _` | | `_ \| | `_ \ / _` | | |/ _ \ / _` | / __| __| |/ __|
     / __/ | |_| | | (_| | | | | | | | | | (_| | | | (_) | (_| | \__ \ |_| | (__
    |_____| \__|_|  \__,_|_|_| |_|_|_| |_|\__, | |_|\___/ \__, |_|___/\__|_|\___|
                                          |___/           |___/
    */


    proc lib=workx kill;
    run;quit;

    /*--- TRAINING 70.000 ---*/

    proc logistic data=lgs.lgs_MgmAllChrNum descending;
    model response(event='1')=
        _MARRIED
        _ACSGENDER
        _DIVISIONCDE
        _INCOME
        _LOANHOME
    /lackfit;
    output out=workx.lgs_fulest p=ful_score;
    run;quit;

    /*---
            TRAIN          |        HOLDOUT
         RESPONSE = 1      |      RESPONSE = 1
     Observed    Expected  |  Observed    Expecte
                           |
           19       18.13  |    8        6.88
           16       31.63  |    4       14.45
           42       60.30  |   32       25.49
           62       47.58  |   28       20.57
           46       64.08  |   19       24.49
           93       72.57  |   34       35.82
          100       94.35  |   37       43.36
          150      141.37  |   67       62.88
          517      515.01  |  214      209.07
    ---*/

    /*---
    Observation(zip9n=330193725 ) of table = workx.lgs_fulest - Total Obs 70,000 14DEC2025:14:21:56

     -- CHARACTER --

    Variable            Typ    Value

    ZIP9N                N6    330193725
    RESPONSE             N3    0
    FUL_SCORE            N8    0.0077178695

    MARRIED              C1    S
    DWELLING             C1    S
    HHINCOME             C21   $100,000 - $124,999
    HOMEYRS              C16   10 YEARS
    OCUPASHN             C41   ?
    AGE                  C15   24 - 25
    ACSMARRIED           C16   MARRIED
    ACSGENDER            C6    MALE
    ACSADULTS            C21   4
    CHILDREN             C1    Y
    RETAILCARD           C39   ?
    DEBITCARD            C39   ?
    REGIONCDE            C5    3
    DIVISIONCDE          C5    5

     -- NUMERIC --

    _MARRIED             N8    0.5358851685
    _DWELLING            N8    1.2057416291
    _HHINCOME            N8    1.5406698594
    _HOMEYRS             N8    1.4736842133
    _OCUPASHN            N8    0.8038277527
    _AGE                 N8    0.0669856461
    _ACSMARRIED          N8    1.3397129212
    _ACSGENDER           N8    1.7416267976
    _ACSADULTS           N8    1.2727272752
    _CHILDREN            N8     1.138755983
    _RETAILCARD          N8    0.8708133988
    _DEBITCARD           N8    0.8038277527
    _REGIONCDE           N8     1.071770337
    _DIVISIONCDE         N8     1.138755983
    _INCOME              N8    0.0669856461
    _RENT                N8    0.5358851685
    _INTEREST            N8    0.5358851685
    _INCOM_USED          N8    0.6698564606
    _CENINCOME           N8     1.071770337
    _HOMES               N8    1.0047846909
    _PURYER              N8    1.6076555055
    _LOANHOME            N8    0.7368421067
    _SINGLEWIDOW         N8    1.0047846909
    _OWNHOME             N8    1.0047846909
    _NOCHILDREN          N8    0.9377990449
    _AGEGTR65            N8    0.8708133988
    SELECTED             N8    0
    INCOME               N8    1777.48
    RENT                 N8    41745
    INTEREST             N8    852674.76
    INCOM_USED           N8    88873.8
    HOMES                N3    1
    CENINCOME            N4    56500
    OWNHOME              N3    .
    LOANHOME             N4    237500
    PURYER               N3    2000
    SINGLEWIDOW          N3    0
    NOCHILDREN           N3    0
    AGEGTR65             N3    0
    _LEVEL_              N3    1

    ---*/

    proc sort data=workx.lgs_fulest(keep=zip9n response ful_score) out=workx.lgs_fulmdlsrt;
     by descending ful_score;
    run;

                                       FUL_
      Obs      ZIP9N     RESPONSE     SCORE

        1    11062114        0       0.14750   Largest prob
        2    15681120        0       0.14750
        3    15810000        0       0.14750
        4    17762807        0       0.14750
        5    18103438        1       0.14750
     ...
    69996   920289082        0       .0014930  Lowest prob
    69997   926729485        0       .0014930
    69998   940402224        0       .0014930
    69999   945601413        0       .0014930
    70000   946114525        0       .0014930

    proc sql;
       select count(*) into :lgs_cnt from lgs.lgs_MgmAllChrNum
    ;quit;

    %put &=lgs_cnt;

    /*--- LGS_CNT=   70000 ---*/

    /*--- put scores in consecutive deciles eacj 70000/10 or about 7000 perdecile ---*/
    /*--- expect is predicted from logistic probabilities                         ---*/
    /*--- response is sum of actual 0/1 responses in sorted deciles               ---*/

    data workx.lgs_fuldec (keep=zip9n decile response ful_score expect cnt);
        retain decile 10 cnt 1 sum_scr 0;
        do until ((mod(rec,(ceil(&lgs_cnt/10))))=0 or dne);
          set workx.lgs_fulmdlsrt end=dne;
          rec+1;
          sum_scr + ful_score;
        end;
        put sum_scr=;
        do until ((mod(cntrec,(ceil(&lgs_cnt/10))))=0 or dne1);
          set workx.lgs_fulmdlsrt end=dne1;
          cntrec+1;
          if cntrec <= round(sum_scr,1) then expect=1;
          else expect=0;
          if  (mod(cntrec,(ceil(&lgs_cnt/10))))=0 or dne1 then do;
             if not dne1 then cnt=cnt+1;
             decile=11-cnt;
             sum_scr=0;
          end;
          output;
        end;
        cntrec=0;
    run;

    /*---

    Up to 40 obs from WORKX.LGS_FULDEC total obs=70,000 14DEC2025:14:30:23
                                            FUL_
      Obs    DECILE    CNT      ZIP9N      SCORE     EXPECT

        1      10       1     11062114    0.14750       1
        2      10       1     15681120    0.14750       1
        3      10       1     15810000    0.14750       1
        4      10       1     17762807    0.14750       1
        5      10       1     18103438    0.14750       1
    ...
    69996      1       10     920289082   .0014930      0
    69997      1       10     926729485   .0014930      0
    69998      1       10     940402224   .0014930      0
    69999      1       10     945601413   .0014930      0
    70000      1       10     946114525   .0014930      0
    ---*/

    proc freq data=workx.lgs_fuldec;
    tables decile*expect / nocol nopercent;
    run;

    /*---

    DECILE     EXPECT

    Frequency|
    Row Pct  |       0|       1|  Total
    ---------+--------+--------+
           1 |   6983 |     18 |   7001
             |  99.74 |   0.26 |
    ---------+--------+--------+
           2 |   6966 |     34 |   7000
             |  99.51 |   0.49 |
    ---------+--------+--------+
           3 |   6962 |     38 |   7000
             |  99.46 |   0.54 |
    ---------+--------+--------+
           4 |   6961 |     39 |   7000
             |  99.44 |   0.56 |
    ---------+--------+--------+
           5 |   6954 |     46 |   7000
             |  99.34 |   0.66 |
    ---------+--------+--------+
           6 |   6937 |     63 |   7000
             |  99.10 |   0.90 |
    ---------+--------+--------+
           7 |   6921 |     79 |   7000
             |  98.87 |   1.13 |
    ---------+--------+--------+
           8 |   6894 |    106 |   7000
             |  98.49 |   1.51 |
    ---------+--------+--------+
           9 |   6838 |    162 |   7000
             |  97.69 |   2.31 |
    ---------+--------+--------+
          10 |   6538 |    461 |   6999
             |  93.41 |   6.59 |
    ---------+--------+--------+
    Total       68954     1046    70000

    ---*/

    proc means data=workx.lgs_fuldec sum n mean;
    class decile;
    var response expect;
    run;quit;


    /*---
    Up to 40 obs from WORKX.LGS_FULDEC total obs=70,000 15DEC2025:13:08:06

    The MEANS Procedure
                                      Count in
     DECILE    N Obs    Variable       Decile            Mean
    ---------------------------------------------------------
          1     7001    RESPONSE      19.0000000    0.0027139 sorted on score and mean of response(1s) 0.27%
                        EXPECT        18.0000000    0.0025711 from logistic mode

          2     7000    RESPONSE      18.0000000    0.0025714
                        EXPECT        34.0000000    0.0048571

          3     7000    RESPONSE      29.0000000    0.0041429
                        EXPECT        38.0000000    0.0054286

          4     7000    RESPONSE      28.0000000    0.0040000
                        EXPECT        39.0000000    0.0055714

          5     7000    RESPONSE      54.0000000    0.0077143
                        EXPECT        46.0000000    0.0065714

          6     7000    RESPONSE      60.0000000    0.0085714
                        EXPECT        63.0000000    0.0090000

          7     7000    RESPONSE      87.0000000    0.0124286
                        EXPECT        79.0000000    0.0112857

          8     7000    RESPONSE     113.0000000    0.0161429
                        EXPECT       106.0000000    0.0151429

          9     7000    RESPONSE     180.0000000    0.0257143
                        EXPECT       162.0000000    0.0231429

         10     6999    RESPONSE     457.0000000    0.0652950
                        EXPECT       461.0000000    0.0658666
    ---------------------------------------------------------

    ---*/

    /*____ _           _             _                        _         _     _
    |___ /| |__   ___ | | ___  _   _| |_   ___ _ __ ___  __ _| |_ ___  | |__ (_)_ __     ___ ___   __| | ___
      |_ \| `_ \ / _ \| |/ _ \| | | | __| / __| `__/ _ \/ _` | __/ _ \ | `_ \| | `_ \   / __/ _ \ / _` |/ _ \
     ___) | | | | (_) | | (_) | |_| | |_ | (__| | |  __/ (_| | ||  __/ | |_) | | | | | | (_| (_) | (_| |  __/
    |____/|_| |_|\___/|_|\___/ \__,_|\__| \___|_|  \___|\__,_|\__\___| |_.__/|_|_| |_|  \___\___/ \__,_|\___|
    */


    /*--- use training mapping functions to use with holdout sample ---*/

    /*--- lgs.lgs_MgmAllChrNum  ---*/

    libname lgs sas7bdat "d:/lgs";
    libname lgs  "d:/lgs";

    %let lgs_inp=lgs_MgmAllChrNum;

    %let lgs_finmod=_MARRIED _ACSGENDER _DIVISIONCDE _INCOME _LOANHOME;

    proc sql noprint;
      select sum(response ne .) into :lgs_cntrec separated by '' from lgs.&lgs_inp
    ;quit;

    %put &=lgs_cntrec;

    /*---  LGS_CNTREC=70000 ---*/

    proc sql noprint;
      select sum(response=1)/sum(response ne .)                             into :lgs_avgrsp    from lgs.&lgs_inp;
      select compress(put(100*sum(response=1)/sum(response ne .),5.3)!!'%') into :lgs_avgrspfmt from lgs.&lgs_inp;
      select sum(response ne .)                                             into :lgs_totcnt    from lgs.&lgs_inp;
      select sum(response=1)                                                into :lgs_rspcnt    from lgs.&lgs_inp;
    ;quit;

    %put &=lgs_avgrsp   ;
    %put &=lgs_avgrspfmt;
    %put &=lgs_totcnt   ;
    %put &=lgs_rspcnt   ;

    /*---
    LGS_AVGRSP    = 0.014929
    LGS_AVGRSPFMT =   1.493%
    LGS_TOTCNT    =    70000
    LGS_RSPCNT    =     1045
    ---*/

    %let lgs_orgvar  = MARRIED  ACSGENDER  DIVISIONCDE  INCOME  LOANHOME;
    %let lgs_finmod  = _MARRIED _ACSGENDER _DIVISIONCDE _INCOME _LOANHOME;

    %let lgs_chr     = MARRIED ACSGENDER DIVISIONCDE;
    %let lgs_chrund  = _MARRIED _ACSGENDER _DIVISIONCDE;
    %let lgs_num     = INCOME LOANHOME;
    %let lgs_numund  = _INCOME _LOANHOME;

    %let lgs_all     = INCOME MARRIED ACSGENDER LOANHOME DIVISIONCDE;
    %let lgs_qot     = %str("MARRIED","","ACSGENDER","","DIVISIONCDE","","INCOME","","LOANHOME");

    /*--- VAR NEWVAL VAL ---*/

    data workx.lgs_numrdo (keep=response var val newval)
         workx.lgs_chrrdo (keep=response var valchr newval rename=valchr=val);
      length valchr $32 var $32;
      set lgs.&lgs_inp;
      array chr[*] &lgs_chr;
      array num[*] &lgs_num;
      array chrund[*] &lgs_chrund;
      array numund[*] &lgs_numund;
      do i=1 to dim(chr);
        typ='C';
        var=vname(chr[i]);
        valchr=chr[i];
        newval=chrund[i];
        output workx.lgs_chrrdo;
      end;
      do i=1 to dim(num);
        typ='N';
        var=vname(num[i]);
        val=num[i];
        newval=numund[i];
        output workx.lgs_numrdo;
      end;
    run;

    /*---
    WORKX.LGS_NUMRDO total obs=140,000 14DEC2025:15:10:32

       Obs      VAR       RESPONSE     NEWVAL          VAL

         1    INCOME          0       0.73684     15749.93
         2    LOANHOME        0       0.46890    112500.00
         3    INCOME          0       1.74163     37632.90
         4    LOANHOME        0       1.00478    287500.00
         5    INCOME          0       1.74163     43094.27
    ...
    139996    LOANHOME        0       0.73684          .
    139997    INCOME          0       4.28708    129090.86
    139998    LOANHOME        0       0.73684          .
    139999    INCOME          0       0.73684     13468.03
    140000    LOANHOME        0       0.46890    137500.00


    WORKX.LGS_CHRRDO total obs=210,000 14DEC2025:15:13:10

       Obs    VAL       VAR            RESPONSE     NEWVAL

         1    S         MARRIED            0       0.53589
         2    MALE      ACSGENDER          0       1.74163
         3    5         DIVISIONCDE        0       1.13876
         4    S         MARRIED            0       0.53589
         5    FEMALE    ACSGENDER          0       0.73684
    ,,,
    209996    ?         ACSGENDER          0       0.73684
    209997    5         DIVISIONCDE        0       1.13876
    209998    S         MARRIED            0       0.53589
    209999    MALE      ACSGENDER          0       1.74163
    210000    5         DIVISIONCDE        0       1.13876
    ---*/

    proc sort data=workx.lgs_numrdo (drop=response) out=workx.lgs_numrdosrt nodupkey;
    by var newval val;
    run;

    proc means data=workx.lgs_numrdosrt missing min max;
    class var newval ;
    var val;
    run;

    /*--- THE MEANS PROCEDURE  (NODUPKEY HAS REMOVED REPEATED VAR BY NEWVAL COMBINATION

                Analysis Variable : VAL

    VAR                   NEWVAL    N Obs         Minimum         Maximum
    ---------------------------------------------------------------------
    INCOME          0.0669856461     3976      10.0000000         4528.32
                    0.3349282303     8286         4531.17        12269.27
                    0.7368421067    18093        12270.24        34481.54
                    1.7416267976    10249        34482.84        66865.89
                    4.2870813479     5747        66874.68      3178262.19
                                    46351.00


    LOANHOME        0.4688995224        9        12500.00       212500.00  many repeats removed
                    0.7368421067        2       237500.00       237500.00
                    1.0047846909        3       262500.00       325000.00
                    1.8086124437        3       375000.00       475000.00
                    3.3492823031        3       625000.00      1000000.00
    ---------------------------------------------------------------------
    ---*/

    proc sort data=workx.lgs_chrrdo(drop=response) out=workx.lgs_chrrdosrt nodupkey;
    by var newval val;
    run;

    proc freq data=workx.lgs_chrrdosrt;
    tables var*val*newval/list missing;
    run;

    /*---

    VAR            VAL             NEWVAL    Frequency
    ------------------------------------------------------
    ACSGENDER      ?         0.7368421067           1
    ACSGENDER      FEMALE    0.7368421067           1
    ACSGENDER      MALE      1.7416267976           1

    DIVISIONCDE    1         0.5358851685           1
    DIVISIONCDE    2         0.5358851685           1
    DIVISIONCDE    3         0.3349282303           1
    DIVISIONCDE    4         0.3349282303           1
    DIVISIONCDE    5          1.138755983           1
    DIVISIONCDE    6         0.3349282303           1
    DIVISIONCDE    7         0.3349282303           1
    DIVISIONCDE    8         0.5358851685           1
    DIVISIONCDE    9         0.3349282303           1
    DIVISIONCDE    OTHER      1.138755983           1

    MARRIED        M         1.8086124437           1
    MARRIED        S         0.5358851685           1
    ---*/

    /*  _                                 _
    | || |   _ __ ___   __ _ _ __     ___| |__   __ _ _ __  __   ____ _ _ __ ___
    | || |_ | `_ ` _ \ / _` | `_ \   / __| `_ \ / _` | `__| \ \ / / _` | `__/ __|
    |__   _|| | | | | | (_| | |_) | | (__| | | | (_| | |     \ V / (_| | |  \__ \
       |_|  |_| |_| |_|\__,_| .__/   \___|_| |_|\__,_|_|      \_/ \__,_|_|  |___/
                            |_|
    */

    data lgs_grpchr (keep=var grp newval);
      length grp $255;
      retain grp '' spc "/**/ /**/";
      set workx.lgs_chrrdosrt;
      by var newval;
      lagval=lag(val);
      if val ne lagval then grp=catx(',',grp,quote(strip(val)));
      if last.newval then do;
         cmd=resolve(cats('if',spc,var,spc,'in (',grp,')',spc,'then',spc,'x',var,'=',put(newval,best.),';'));
         put cmd;
         grp='';
      end;
    run;

    /*--- caracter mappings
    if ACSGENDER in ("?","FEMALE") then xACSGENDER=0.7368421067;
    if ACSGENDER in ("MALE") then xACSGENDER=1.7416267976;
    if DIVISIONCDE in ("3","4","6","7","9") then xDIVISIONCDE=0.3349282303;
    if DIVISIONCDE in ("1","2","8") then xDIVISIONCDE=0.5358851685;
    if DIVISIONCDE in ("5","OTHER") then xDIVISIONCDE=1.138755983;
    if MARRIED in ("S") then xMARRIED=0.5358851685;
    if MARRIED in ("M") then xMARRIED=1.8086124437;
    ---*/

    /*___
    | ___|  _ __ ___   __ _ _ __    _ __  _   _ _ __ ___   __   ____ _ _ __ ___
    |___ \ | `_ ` _ \ / _` | `_ \  | `_ \| | | | `_ ` _ \  \ \ / / _` | `__/ __|
     ___) || | | | | | (_| | |_) | | | | | |_| | | | | | |  \ V / (_| | |  \__ \
    |____/ |_| |_| |_|\__,_| .__/  |_| |_|\__,_|_| |_| |_|   \_/ \__,_|_|  |___/
                           |_|
    */

    options ls=171 ps=60;
    data workx.lgs_grpnum(keep=grp);
      retain min 1e300 max -1e300 spc '/**/ /**/';
      length grp $128;
      retain grp '' ;
      do until (last.newval);
        set workx.lgs_numrdosrt;
        by var newval;
        if first.newval then do;
          min    = 1e300;
          max    =-1e300;
        end;
        if not missing(val) then do;
           if val<min then min=val;
           if val>max then max=val;
        end;
        else gotmis=1;
      end;
      *put var= newval= min= max=;
      if not(missing(min)) and gotmis then grp=resolve(cats('if missing(',var,') or',spc,
           put(min,best.),'<=',var,'<=',put(max,best.),spc,'then _',var,'=',put(newval,best.),';'));
      else grp=resolve(cats('if',spc,put(min,best.),'<=',var,'<=',put(max,best.),spc,'then',spc,'_',var,'=',put(newval,best.),';'));
      put grp;
      if min=1e300  then min=.;
      if max=-1e300 then max=.;
    run;

    /*--- number mappings
    if 10<=INCOME<=4528.32 then xINCOME=0.0669856461;
    if missing(INCOME) or 4531.17<=INCOME<=12269.27 then _INCOME=0.3349282303;
    if 12270.24<=INCOME<=34481.54 then xINCOME=0.7368421067;
    if 34482.84<=INCOME<=66865.89 then xINCOME=1.7416267976;
    if 66874.68<=INCOME<=3178262.19 then xINCOME=4.2870813479;
    if 12500<=LOANHOME<=212500 then xLOANHOME=0.4688995224;
    if missing(LOANHOME) or 237500<=LOANHOME<=237500 then _LOANHOME=0.7368421067;
    if 262500<=LOANHOME<=325000 then xLOANHOME=1.0047846909;
    if 375000<=LOANHOME<=475000 then xLOANHOME=1.8086124437;
    if 625000<=LOANHOME<=1000000 then xLOANHOME=3.3492823031;
    ---*/

    /*__                      _                                    _
     / /_    __ _ _ __  _ __ | |_   _  _ __ ___   __ _ _ __  _ __ (_)_ __   __ _ ___
    | `_ \  / _` | `_ \| `_ \| | | | || `_ ` _ \ / _` | `_ \| `_ \| | `_ \ / _` / __|
    | (_) || (_| | |_) | |_) | | |_| || | | | | | (_| | |_) | |_) | | | | | (_| \__ \
     \___/  \__,_| .__/| .__/|_|\__, ||_| |_| |_|\__,_| .__/| .__/|_|_| |_|\__, |___/
                 |_|   |_|      |___/                 |_|   |_|            |___/
    */

    libname lgs sas7bdat "d:/lgs";
    libname lgs "d:/lgs";

    data workx.lgs_holdmodel;
     set lgs.lgs_rawhold
      (keep=zip9n response MARRIED ACSGENDER DIVISIONCDE INCOME LOANHOME);

    /*--- NUM BINS
                                                             ---*/
    if 10<=INCOME<=4528.32 then xINCOME=0.0669856461;
    if missing(INCOME) or 4531.17<=INCOME<=12269.27 then xINCOME=0.3349282303;
    if 12270.24<=INCOME<=34481.54 then xINCOME=0.7368421067;
    if 34482.84<=INCOME<=66865.89 then xINCOME=1.7416267976;
    if 66874.68<=INCOME<=3178262.19 then xINCOME=4.2870813479;

    if 12500<=LOANHOME<=212500 then xLOANHOME=0.4688995224;
    if missing(LOANHOME) or 237500<=LOANHOME<=237500 then xLOANHOME=0.7368421067;
    if 262500<=LOANHOME<=325000 then xLOANHOME=1.0047846909;
    if 375000<=LOANHOME<=475000 then xLOANHOME=1.8086124437;
    if 625000<=LOANHOME<=1000000 then xLOANHOME=3.3492823031;

    /*--- CHR BINS                                                              ---*/

    if ACSGENDER in ("?","FEMALE") then xACSGENDER=0.7368421067;
    if ACSGENDER in ("MALE") then xACSGENDER=1.7416267976;

    if DIVISIONCDE in ("3","4","6","7","9") then xDIVISIONCDE=0.3349282303;
    if DIVISIONCDE in ("1","2","8") then xDIVISIONCDE=0.5358851685;
    if DIVISIONCDE in ("5","OTHER") then xDIVISIONCDE=1.138755983;

    if MARRIED in ("S") then xMARRIED=0.5358851685;
    if MARRIED in ("M") then xMARRIED=1.8086124437;

    run;quit;

    proc freq data=workx.lgs_holdmodel;
      tables response*acsgender*xacsgender
             response*married*xmarried
             response*divisioncde*xdivisioncde /list;
    run;quit;

    /*---
    RESPONSE    ACSGENDER      XACSGENDER    Frequency     Percent
    --------------------------------------------------------------
           0    ?            0.7368421067       14680       48.93
           0    FEMALE       0.7368421067        7107       23.69
           0    MALE         1.7416267976        7770       25.90
           1    ?            0.7368421067         173        0.58
           1    FEMALE       0.7368421067          71        0.24
           1    MALE         1.7416267976         199        0.66
                                               30,000
    ---*/

    /*____  _           _     _             _    _             _     _   _
    |___  || |__   ___ | | __| | ___  _   _| |_ | | ___   __ _(_)___| |_(_) ___
       / / | `_ \ / _ \| |/ _` |/ _ \| | | | __|| |/ _ \ / _` | / __| __| |/ __|
      / /  | | | | (_) | | (_| | (_) | |_| | |_ | | (_) | (_| | \__ \ |_| | (__
     /_/   |_| |_|\___/|_|\__,_|\___/ \__,_|\__||_|\___/ \__, |_|___/\__|_|\___|
                                                         |___/
    */

    proc logistic data=workx.lgs_holdmodel descending;
    model response(event='1')=
        xMARRIED
        xACSGENDER
        xDIVISIONCDE
        xINCOME
        xLOANHOME
    /lackfit;
    output out=workx.lgs_holfulest p=ful_score;
    run;quit;

    proc sort data=workx.lgs_holfulest(keep=zip9n response ful_score) out=workx.lgs_holmdlsrt;
     by descending ful_score;
    run;

    proc sql;
       select count(*) into :lgs_holcnt from workx.lgs_holdmodel
    ;quit;

    /*--- put scores in consecutive deciles eacj 30000/10 or about 7000 perdecile ---*/

    data workx.lgs_holdec (keep=zip9n decile response ful_score expect cnt);
        retain decile 10 cnt 1 sum_scr 0;
        do until ((mod(rec,(ceil(&lgs_holcnt/10))))=0 or dne);
          set workx.lgs_holmdlsrt end=dne;
          rec+1;
          sum_scr + ful_score;
        end;
        put  sum_scr=;
        do until ((mod(cntrec,(ceil(&lgs_holcnt/10))))=0 or dne1);
          set workx.lgs_holmdlsrt end=dne1;
          cntrec+1;
          if cntrec <= round(sum_scr,1) then expect=1;
          else expect=0;
          if  (mod(cntrec,(ceil(&lgs_holcnt/10))))=0 or dne1 then do;
             if not dne1 then cnt=cnt+1;
             decile=11-cnt;
             sum_scr=0;
          end;
          output;
        end;
        cntrec=0;
    run;

    /*---
    Up to 40 obs from WORKX.LGS_FULDEC total obs=70,000 14DEC2025:14:30:23
                                            FUL_
      Obs    DECILE    CNT      ZIP9N      SCORE     EXPECT

        1      10       1     11062114    0.14750       1
        2      10       1     15681120    0.14750       1
        3      10       1     15810000    0.14750       1
        4      10       1     17762807    0.14750       1
        5      10       1     18103438    0.14750       1
    ...
    69996      1       10     920289082   .0014930      0
    69997      1       10     926729485   .0014930      0
    69998      1       10     940402224   .0014930      0
    69999      1       10     945601413   .0014930      0
    70000      1       10     946114525   .0014930      0
    ---*/


    proc means data=workx.lgs_holdec sum n mean;
    class decile;
    var response expect;
    run;quit;

    /*---
    WORKX.LGS_HOLDEC total obs=30,000 15DEC2025:13:21:30

    The MEANS Procedure

          DECILE    N Obs    Variable             Sum        N            Mean
    --------------------------------------------------------------------------
               1     3001    RESPONSE       8.0000000     3001       0.0026658
                             EXPECT         7.0000000     3001       0.0023326

               2     3000    RESPONSE       4.0000000     3000       0.0013333
                             EXPECT        14.0000000     3000       0.0046667

               3     3000    RESPONSE      18.0000000     3000       0.0060000
                             EXPECT        16.0000000     3000       0.0053333

               4     3000    RESPONSE      20.0000000     3000       0.0066667
                             EXPECT        17.0000000     3000       0.0056667

               5     3000    RESPONSE      29.0000000     3000       0.0096667
                             EXPECT        19.0000000     3000       0.0063333

               6     3000    RESPONSE      22.0000000     3000       0.0073333
                             EXPECT        26.0000000     3000       0.0086667

               7     3000    RESPONSE      30.0000000     3000       0.0100000
                             EXPECT        35.0000000     3000       0.0116667

               8     3000    RESPONSE      42.0000000     3000       0.0140000
                             EXPECT        46.0000000     3000       0.0153333

               9     3000    RESPONSE      68.0000000     3000       0.0226667
                             EXPECT        70.0000000     3000       0.0233333

              10     2999    RESPONSE     202.0000000     2999       0.0673558
                             EXPECT       191.0000000     2999       0.0636879
    --------------------------------------------------------------------------
    ---*/


    /*--- 70,000 TRAINING ---*/

    proc freq data=workx.lgs_fuldec;
    tables decile*expect / nocol nopercent;
    run;

    /*--- 30,000 TRAINING ---*/

    proc freq data=workx.lgs_holdec;
     tables decile*expect/ nocol nopercent;
    run;quit;

    /*---
               TRAIN                                 HOLD
    DECILE     EXPECT                     DECILE     EXPECT

    Frequency|                            Frequency|
    Row Pct  |       0|       1|  Total   Row Pct  |       0|       1|  Total
    ---------+--------+--------+          ---------+--------+--------+
           1 |   6983 |     18 |   7001          1 |   2994 |      7 |   3001
             |  99.74 |   0.26 |                   |  99.77 |   0.23 |
    ---------+--------+--------+          ---------+--------+--------+
           2 |   6966 |     34 |   7000          2 |   2986 |     14 |   3000
             |  99.51 |   0.49 |                   |  99.53 |   0.47 |
    ---------+--------+--------+          ---------+--------+--------+
           3 |   6962 |     38 |   7000          3 |   2984 |     16 |   3000
             |  99.46 |   0.54 |                   |  99.47 |   0.53 |
    ---------+--------+--------+          ---------+--------+--------+
           4 |   6961 |     39 |   7000          4 |   2983 |     17 |   3000
             |  99.44 |   0.56 |                   |  99.43 |   0.57 |
    ---------+--------+--------+          ---------+--------+--------+
           5 |   6954 |     46 |   7000          5 |   2981 |     19 |   3000
             |  99.34 |   0.66 |                   |  99.37 |   0.63 |
    ---------+--------+--------+          ---------+--------+--------+
           6 |   6937 |     63 |   7000          6 |   2974 |     26 |   3000
             |  99.10 |   0.90 |                   |  99.13 |   0.87 |
    ---------+--------+--------+          ---------+--------+--------+
           7 |   6921 |     79 |   7000          7 |   2965 |     35 |   3000
             |  98.87 |   1.13 |                   |  98.83 |   1.17 |
    ---------+--------+--------+          ---------+--------+--------+
           8 |   6894 |    106 |   7000          8 |   2954 |     46 |   3000
             |  98.49 |   1.51 |                   |  98.47 |   1.53 |
    ---------+--------+--------+          ---------+--------+--------+
           9 |   6838 |    162 |   7000          9 |   2930 |     70 |   3000
             |  97.69 |   2.31 |                   |  97.67 |   2.33 |
    ---------+--------+--------+          ---------+--------+--------+
          10 |   6538 |    461 |   6999         10 |   2808 |    191 |   2999
             |  93.41 |   6.59 |                   |  93.63 |   6.37 |
    ---------+--------+--------+          ---------+--------+--------+
    Total       68954     1046    70000   Total       29559      441    30000

    ---*/

                            _            _   ___                        _      _      _           _ _
    /*___   _ __ __ _ _ __ | | _____  __| | ( _ )   _ __ ___   ___   __| | ___| |  __| | ___  ___(_) | ___  ___
     ( _ ) | `__/ _` | `_ \| |/ / _ \/ _` | / _ \/\| `_ ` _ \ / _ \ / _` |/ _ \ | / _` |/ _ \/ __| | |/ _ \/ __|
     / _ \ | | | (_| | | | |   <  __/ (_| || (_>  <| | | | | | (_) | (_| |  __/ || (_| |  __/ (__| | |  __/\__ \
    | (_) ||_|  \__,_|_| |_|_|\_\___|\__,_| \___/\/|_| |_| |_|\___/ \__,_|\___|_| \__,_|\___|\___|_|_|\___||___/
     \___/

    */
    proc format;
      value rsp2des
          0 = 'ACTDEV_0'  /*---  ACTUAL    DEV  0 is TRAINING 70,000  response=0 ---*/
          1 = 'ACTDEV_1'  /*---  ACTUAL    DEV  1 is TRAINING 70,000  response=1 ---*/

         -2 = 'ACTHLD_0'  /*---  ACTUAL    HLD -2 is HOLDOUT  30,000  response=0 ---*/
         -1 = 'ACTHLD_1'  /*---  ACTUAL    HLD -1 is HOLDOUT  30,000  response=1 ---*/

         -6 = 'ESTDEV_0'  /*---  PREDICTED DEV -6 is TRAINING 70,000  response=0 ---*/
         -5 = 'ESTDEV_1'  /*---  PREDICTED DEV -5 is TRAINING 70,000  response=1 ---*/

         -4 = 'ESTHLD_0'  /*---  PREDICTED HLD -4 is HOLDOUT  30,000  response=0 ---*/
         -3 = 'ESTHLD_1'  /*---  PREDICTED HLD -3 is HOLDOUT  30,000  response=1 ---*/
      ;
    run;quit;

    data workx.lgs_holrsp (
       keep=descnt despct decile zip9n resp
       ) ;
       retain fro descnt despct;
       length descnt despct $16. ;
       set
          workx.lgs_fuldec (in=train)
          workx.lgs_holdec (in=hold) ;
          if train then fro='DEV';
          else fro='HLD';
          if hold then do;
              typ="ACT";
              response =  response-2;
              descnt=cats('CNT',put(response,rsp2des.));
              despct=cats('PCT',put(response,rsp2des.));
              resp=input(scan(descnt,2,'_'),2.);
              output;
              typ="EST";
              response=expect-4;
              descnt=cats('CNT',put(response,rsp2des.));
              despct=cats('PCT',put(response,rsp2des.));
              resp=input(scan(descnt,2,'_'),2.);
              output;
          end;
          if train then do;
              typ="ACT";
              descnt=cats('CNT',put(response,rsp2des.));
              despct=cats('PCT',put(response,rsp2des.));
              resp=input(scan(descnt,2,'_'),2.);
              output;
              typ="EST";
              response=expect-6;
              descnt=cats('CNT',put(response,rsp2des.));
              despct=cats('PCT',put(response,rsp2des.));
              resp=input(scan(descnt,2,'_'),2.);
              output;
          end;
    run;quit;

    ods exclude all;;
    Ods Output observed = workx.lgs_cnt(where=(upcase(label) ne 'SUM') drop=sum)  ;
    Proc Corresp Data=workx.lgs_holrsp Observed dim=1 print=both cp;
       Tables decile, descnt ;
    Run;
    ods select all;

    options ls=255;
    proc print data=workx.lgs_cnt /*heading=vertical*/;
    run;quit;


    /*---

    Altair SLC

    LABEL    CNTACTDEV_0    CNTACTDEV_1    CNTACTHLD_0    CNTACTHLD_1    CNTESTDEV_0    CNTESTDEV_1    CNTESTHLD_0    CNTESTHLD_1

     1             6982             19           2993              8           6983             18           2994              7
     2             6982             18           2996              4           6966             34           2986             14
     3             6971             29           2982             18           6962             38           2984             16
     4             6972             28           2980             20           6961             39           2983             17
     5             6946             54           2971             29           6954             46           2981             19
     6             6940             60           2978             22           6937             63           2974             26
     7             6913             87           2970             30           6921             79           2965             35
     8             6887            113           2958             42           6894            106           2954             46
     9             6820            180           2932             68           6838            162           2930             70
     10            6542            457           2797            202           6538            461           2808            191


    Middle Observation(5) of table = workx.lgs_cnt - Total Obs 10 16DEC2025:09:49:53

      -- NUMERIC --
                             SAMPLE
     VAR            TYPE     COUNT

     cntActDev_0     N8      6946   *---  ACTUAL  COUNTS  DEV  0 is TRAINING 70,000    response=0 ---;
     cntActDev_1     N8        54   *---  ACTUAL  COUNTS  DEV  1 is TRAINING 70,000    response=1 ---;

     cntActHld_0     N8      2971   *---  ACTUAL  COUNTS  HLD -2 is HOLDOUT  30,000    response=0 ---;
     cntActHld_1     N8        29   *---  ACTUAL  COUNTS  HLD -1 is HOLDOUT  30,000    response=1 ---;

     cntEstDev_0     N8      6954   *---  PREDICTED COUNTS  DEV -6 is TRAINING 70,000  response=0 ---;
     cntEstDev_1     N8        46   *---  PREDICTED COUNTS  DEV -5 is TRAINING 70,000  response=1 ---;

     cntEstHld_0     N8      2981   *---  PREDICTED COUNTS HLD -4 is HOLDOUT  30,000   response=0 ---;
     cntEstHld_1     N8        19   *---  PREDICTED COUNTS HLD -3 is HOLDOUT  30,000   response=1 ---;

    ---*/

     COUNTS

    ods exclude all;;
    Ods Output observed = workx.lgs_cnt(where=(upcase(label) ne 'SUM') drop=sum)  ;
    Proc Corresp Data=workx.lgs_holrsp Observed dim=1 print=both cp;
       Tables decile, descnt ;
    Run;
    ods select all;

    ods exclude all;;
    Ods Output ColProfilesPct = workx.lgs_pct;
    Proc Corresp Data=workx.lgs_holrsp Observed dim=1 print=both cp;
       Tables decile, despct ;
    Run;
    ods select all;

    options ls=255;
    proc print data=workx.lgs_pct /*heading=vertical*/;
    run;quit;


    /*---
    Altair SLC

    WORKX.LGS_PCT total obs=10 16DEC2025:10:00:27

    LABEL    PCTACTDEV_0    PCTACTDEV_1    PCTACTHLD_0    PCTACTHLD_1    PCTESTDEV_0    PCTESTDEV_1    PCTESTHLD_0    PCTESTHLD_1

     1          10.1254         1.8182        10.1262         1.8059        10.1270         1.7208        10.1289         1.5873
     2          10.1254         1.7225        10.1363         0.9029        10.1024         3.2505        10.1018         3.1746
     3          10.1095         2.7751        10.0890         4.0632        10.0966         3.6329        10.0951         3.6281
     4          10.1109         2.6794        10.0822         4.5147        10.0951         3.7285        10.0917         3.8549
     5          10.0732         5.1675        10.0518         6.5463        10.0850         4.3977        10.0849         4.3084
     6          10.0645         5.7416        10.0754         4.9661        10.0603         6.0229        10.0612         5.8957
     7          10.0254         8.3254        10.0484         6.7720        10.0371         7.5526        10.0308         7.9365
     8           9.9877        10.8134        10.0078         9.4808         9.9980        10.1338         9.9936        10.4308
     9           9.8905        17.2249         9.9198        15.3499         9.9168        15.4876         9.9124        15.8730
     10          9.4873        43.7321         9.4631        45.5982         9.4817        44.0727         9.4996        43.3107


     -- NUMERIC --
                            SAMPLE
    VAR            TYPE     PERCENT

     PCTACTDEV_0   N8    10.073236169  *---  ACTUAL  PERCENT  DEV  0 is TRAINING 70,000    response=0 ---;
     PCTACTDEV_1   N8    5.1674641148  *---  ACTUAL  PERCENT  DEV  1 is TRAINING 70,000    response=1 ---;

     PCTACTHLD_0   N8    10.051764387  *---  ACTUAL  PERCENT  HLD -2 is HOLDOUT  30,000    response=0 ---;
     PCTACTHLD_1   N8     6.546275395  *---  ACTUAL  PERCENT  HLD -1 is HOLDOUT  30,000    response=1 ---;

     PCTESTDEV_0   N8    10.084984192  *---  PREDICTED PERCENT  DEV -6 is TRAINING 70,000  response=0 ---;
     PCTESTDEV_1   N8    4.3977055449  *---  PREDICTED PERCENT  DEV -5 is TRAINING 70,000  response=1 ---;

     PCTESTHLD_0   N8    10.084914916  *---  PREDICTED PERCENT HLD -4 is HOLDOUT  30,000   response=0 ---;
     PCTESTHLD_1   N8    4.3083900227  *---  PREDICTED PERCENT HLD -3 is HOLDOUT  30,000   response=1 ---;

    ---*/

    /*___     _       _                               _         ___                                  _
     / _ \   (_) ___ (_)_ __     ___ ___  _   _ _ __ | |_ ___  ( _ )   _ __   ___ _ __ ___ ___ _ __ | |_ ___
    | (_) |  | |/ _ \| | `_ \   / __/ _ \| | | | `_ \| __/ __| / _ \/\| `_ \ / _ \ `__/ __/ _ \ `_ \| __/ __|
     \__, |  | | (_) | | | | | | (_| (_) | |_| | | | | |_\__ \| (_>  <| |_) |  __/ | | (_|  __/ | | | |_\__ \
       /_/  _/ |\___/|_|_| |_|  \___\___/ \__,_|_| |_|\__|___/ \___/\/| .__/ \___|_|  \___\___|_| |_|\__|___/
           |__/                                                       |_|
    */

    proc sql;
      create
         table workx.lgs_cntpct as
      select
         l.*
        ,r.*
      from
        workx.lgs_cnt as l left join workx.lgs_pct as r
      on
        strip(l.label) = strip(r.label)
      order
        by label
    ;quit;

    /*---

    Middle Observation(4 ) of table = workx.lgs_cntpct - Total Obs 10 16DEC2025:10:33:42


     -- CHARACTER --

                          SAMPE
    Variable       Typ    Value

    LABEL           C3    4


     -- NUMERIC --
    CNTACTDEV_0     N8    6972           TRAINING 0 RESPONSE RANKED BY SCORE
    CNTACTDEV_1     N8    28             TRAINING 1 RESPONSE RANKED BY SCORE

    CNTACTHLD_0     N8    2980           HOLDOUT  0 RESPONSE RANKED BY SCORE
    CNTACTHLD_1     N8    20             HOLDOUT  1 RESPONSE RANKED BY SCORE

    CNTESTDEV_0     N8    6961           TRAINING 0 RESPONSE USING MODELED PROBABITIES DIRECTLY
    CNTESTDEV_1     N8    39             TRAINING 1 RESPONSE USING MODELED PROBABITIES DIRECTLY

    CNTESTHLD_0     N8    2983           HOLDOUT  0 RESPONSE USING MODELED PROBABITIES DIRECTLY
    CNTESTHLD_1     N8    17             HOLDOUT  1 RESPONSE USING MODELED PROBABITIES DIRECTLY

    PCTACTDEV_0     N8    10.110941919   SAME AS ABOVE BUT PERCENT
    PCTACTDEV_1     N8    2.6794258373

    PCTACTHLD_0     N8    10.082214027
    PCTACTHLD_1     N8    4.5146726862

    PCTESTDEV_0     N8    10.095135888
    PCTESTDEV_1     N8    3.7284894837

    PCTESTHLD_0     N8    10.091681045
    PCTESTHLD_1     N8    3.8548752834

    ---*/

    /*  ___                         _     _                      _  __ _           _   _
    / |/ _ \   __ _ _ __ __ _ _ __ | |__ (_) ___ __   _____ _ __(_)/ _(_) ___ __ _| |_(_) ___  _ __
    | | | | | / _` | `__/ _` | `_ \| `_ \| |/ __|\ \ / / _ \ `__| | |_| |/ __/ _` | __| |/ _ \| `_ \
    | | |_| || (_| | | | (_| | |_) | | | | | (__  \ V /  __/ |  | |  _| | (_| (_| | |_| | (_) | | | |
    |_|\___/  \__, |_|  \__,_| .__/|_| |_|_|\___|  \_/ \___|_|  |_|_| |_|\___\__,_|\__|_|\___/|_| |_|
              |___/          |_|
    */


    options validvarname=v7;
    data workx.lgs_est(drop=pct: label);
      do until (dne);
         set workx.lgs_cntpct (keep=label pctactdev_1 pctacthld_1) end=dne;
         Method='RANKED SCORE  ';
         Decile=input(label,3.);
         Training=pctactdev_1/100;
         Holdout=pctacthld_1/100;
         Difference=(pctactdev_1 - pctacthld_1)/100;
         output;
      end;
      do until (dne1);
         set workx.lgs_cntpct(keep=label pctestdev_1 pctesthld_1) end=dne1;
         Method='MODEL PREDICT';
         Decile=input(label,3.);
         Training=pctestdev_1/100;
         Holdout=pctesthld_1/100;
         Difference=(pctestdev_1 - pctesthld_1)/100;
         output;
      end;
    run;quit;

    proc transpose data=workx.lgs_est out=lgs_estXpo(rename=(_name_=Sample col1=Probability));
       by  Method Decile notsorted;
       var Training Holdout Difference;
    run;quit;

    proc sort data=lgs_estXpo out=workx.estSrt;
       by Method Sample Decile;
    run;quit;

    /*---
    Table WORKX.ESTSRT total obs=60 16DEC2025:14:26:08

    Obs       Method        Decile      Sample      Probability

      1    MODEL PREDICT       1      Difference       0.00134
      2    MODEL PREDICT       2      Difference       0.00076
      3    MODEL PREDICT       3      Difference       0.00005
      4    MODEL PREDICT       4      Difference      -0.00126
      5    MODEL PREDICT       5      Difference       0.00089
    ...
     56    RANKED SCORE        6      Training         0.05742
     57    RANKED SCORE        7      Training         0.08325
     58    RANKED SCORE        8      Training         0.10813
     59    RANKED SCORE        9      Training         0.17225
     60    RANKED SCORE       10      Training         0.43732
    ---*/

    %utlfkil(d:\png\liftplots.png);

    filename gout temp;
    ods html(id=add_dest) body=gout gpath="d:\png";
    ods graphics on / imagename="liftplots" reset=all;

    proc sgpanel data=workx.estSrt;
     panelby Method / rows=1;
     rowaxis grid
       labelattrs=(size=12pt ) valueattrs=(size=10pt);
     colaxis values=(1 to 10 by 1) grid
           labelattrs=(size=12pt)
             valueattrs=(size=10pt);
     series x=Decile y=Probability / group=Sample
       markers
       markerattrs=(size=11px symbol=circlefilled)
       lineattrs=(thickness=2px);

     run;quit;

    filename gout clear;
    ods graphics off;
    ods _all_ close;
    ods listing;

    /* _                 _ _         _       _                   _  __ _           _   _
    / / |  __ _ ___  ___(_|_)  _ __ | | ___ | |_ __   _____ _ __(_)/ _(_) ___ __ _| |_(_) ___  _ __
    | | | / _` / __|/ __| | | | `_ \| |/ _ \| __|\ \ / / _ \ `__| | |_| |/ __/ _` | __| |/ _ \| `_ \
    | | || (_| \__ \ (__| | | | |_) | | (_) | |_  \ V /  __/ |  | |  _| | (_| (_| | |_| | (_) | | | |
    |_|_| \__,_|___/\___|_|_| | .__/|_|\___/ \__|  \_/ \___|_|  |_|_| |_|\___\__,_|\__|_|\___/|_| |_|
                              |_|
    */


    data lgs.lynplt;
     length ltr $1;
     set workx.estSrt;
       ltr=sample;
    run;quit;

    options ls=65 ps=64;
    proc plot data=lgs.lynplt(where=(method =: "MODEL"));
      plot probability*decile=' ' $ ltr /box;
    run;quit;

    options ls=65 ps=64;
    proc plot data=lgs.lynplt(where=(method =: "RANKED"));
      plot probability*decile=' ' $ ltr /box;
    run;quit;


    proc print data=lgs.lynplt(where=(method =: "MODEL"));
    run;quit;

    proc print data=lgs.lynplt(where=(method =: "RANK"));
    run;quit;


          Plot of Probability*Decile$ltr.

                                     Decile
                   1    2    3    4    5    6    7    8    9   10
                ---+----+----+----+----+----+----+----+----+----+---
    Probability |                                                  |
                |  Comparison Using the Model Probabilities        |
           0.45 +  add 1 to count each sum of predicted increases  + 0.45
                |  by one save use the count for each decile    T  |
                |                                               H  |
                |  Decile   Sample   Probability                   |
                |                                H=Holdout         |
           0.40 +     1   Difference    0.00134                    + 0.40
                |     2   Difference    0.00076  T=Training        |
                |     3   Difference    0.00005                    |
                |     4   Difference   -0.00126  D=Difference      |
                |     5   Difference    0.00089                    |
           0.35 +     6   Difference    0.00127                    + 0.35
                |     7   Difference   -0.00384                    |
                |     8   Difference   -0.00297           HT       |
                |     9   Difference   -0.00385                    |
                |    10   Difference    0.00762                    |
           0.30 +                                                  + 0.30
                |     1   Holdout       0.01587                    |
                |     2   Holdout       0.03175                    |
                |     3   Holdout       0.03628                    |
                |     4   Holdout       0.03855                    |
           0.25 +     5   Holdout       0.04308                    + 0.25
                |     6   Holdout       0.05896                    |
                |     7   Holdout       0.07937                    |
                |     8   Holdout       0.10431                    |
                |     9   Holdout       0.15873                    |
           0.20 +    10   Holdout       0.43311                    + 0.20
                |                                                  |
                |     1   Training      0.01721                    |
                |     2   Training      0.03250                    |
                |     3   Training      0.03633      H             |
           0.15 +     4   Training      0.03728      T             + 0.15
                |     5   Training      0.04398                    |
                |     6   Training      0.06023                    |
                |     7   Training      0.07553                    |
                |     8   Training      0.10134                    |
           0.10 +     9   Training      0.15488     HT             + 0.10
                |    10   Training      0.44073                    |
                |                                H                 |
                |                                                  |
                |                           TH                     |
           0.05 +                      T                           + 0.05
                |            H    T    H                           |
                |       T    T                                     |
                |  H                                               |
                |                                               D  |
           0.00 +  D    D    D    D    D    D    D    D    D       + 0.00
                |                                                  |
                ---+----+----+----+----+----+----+----+----+----+---
                   1    2    3    4    5    6    7    8    9   10

                                       Decile


          Plot of Probability*Decile$ltr

                                     Decile
                   1    2    3    4    5    6    7    8    9   10
                ---+----+----+----+----+----+----+----+----+----+---
    Probability |                                                  |
                |                                                  |
           0.50 +                                                  +  0.50
                | Decile    Sample    Probability                  |
                |                                                  |
                |    1    Difference     0.00012                   |
           0.45 +    2    Difference     0.00820                H  +  0.45
                |    3    Difference    -0.01288                T  |
                |    4    Difference    -0.01835                   |
                |    5    Difference    -0.01379                   |
           0.40 +    6    Difference     0.00775                   +  0.40
                |    7    Difference     0.01553                   |
                |    8    Difference     0.01333                   |
                |    9    Difference     0.01875                   |
           0.35 +   10    Difference    -0.01866                   +  0.35
                |                                                  |
                |    1    Holdout        0.01806                   |
                |    2    Holdout        0.00903                   |
           0.30 +    3    Holdout        0.04063                   +  0.30
                |    4    Holdout        0.04515                   |
                |    5    Holdout        0.06546                   |
                |    6    Holdout        0.04966                   |
           0.25 +    7    Holdout        0.06772                   +  0.25
                |    8    Holdout        0.09481                   |
                |    9    Holdout        0.15350                   |
                |                   |
           0.20 +   10    Holdout        0.45598                   +  0.20
                |    1    Training       0.01818                   |
                |    2    Training       0.01722           T       |
                |    3    Training       0.02775                   |
           0.15 +    4    Training       0.02679           H       +  0.15
                |    5    Training       0.05167                   |
                |    6    Training       0.05742                   |
                |    7    Training       0.08325      T            |
           0.10 +    8    Training       0.10813      H            +  0.10
                |    9    Training       0.17225   T               |
                |   10    Training       0.43732                   |
                |                      H    T    H                 |
           0.05 +                 H    T    H                      +  0.05
                |            H                                     |
                |            T    T                                |
                |  T    T                   D    D    D    D       |
           0.00 +  D                                               +  0.00
                |            D    D    D                        D  |
                |                                                  |
                |                                                  |
          -0.05 +                                                  + -0.05
                |                                                  |
                ---+----+----+----+----+----+----+----+----+----+---
                   1    2    3    4    5    6    7    8    9   10
                                       Decile


    /* ____               _               _
    / |___ \   ___  _   _| |_ _ __  _   _| |_ ___
    | | __) | / _ \| | | | __| `_ \| | | | __/ __|
    | |/ __/ | (_) | |_| | |_| |_) | |_| | |_\__ \
    |_|_____| \___/ \__,_|\__| .__/ \__,_|\__|___/
                             |_|
    d:/lgs/lgs_liftnormalized.sas7bdat
    d:/lgs/lgs_liftdenormalized.sas7bdat
    */

    /*--- DENORMALIZED ---*/

    data lgs.lgs_liftdenormalized;
      set workx.lgs_cntpct;
    run;quit;

    Middle Observation(4 ) of table = workx.lgs_cntpct - Total Obs 10 16DEC2025:10:33:42


     -- CHARACTER --

                          SAMPE
    Variable       Typ    Value

    LABEL           C3    4

    COUNTS

     -- NUMERIC --
    CNTACTDEV_0     N8    6972           TRAINING 0 RESPONSE RANKED BY SCORE
    CNTACTDEV_1     N8    28             TRAINING 1 RESPONSE RANKED BY SCORE

    CNTACTHLD_0     N8    2980           HOLDOUT  0 RESPONSE RANKED BY SCORE
    CNTACTHLD_1     N8    20             HOLDOUT  1 RESPONSE RANKED BY SCORE

    CNTESTDEV_0     N8    6961           TRAINING 0 RESPONSE USING MODELED PROBABITIES DIRECTLY
    CNTESTDEV_1     N8    39             TRAINING 1 RESPONSE USING MODELED PROBABITIES DIRECTLY

    CNTESTHLD_0     N8    2983           HOLDOUT  0 RESPONSE USING MODELED PROBABITIES DIRECTLY
    CNTESTHLD_1     N8    17             HOLDOUT  1 RESPONSE USING MODELED PROBABITIES DIRECTLY

    PERCENTS

    PCTACTDEV_0     N8    10.110941919   SAME AS ABOVE BUT PERCENT
    PCTACTDEV_1     N8    2.6794258373

    PCTACTHLD_0     N8    10.082214027
    PCTACTHLD_1     N8    4.5146726862

    PCTESTDEV_0     N8    10.095135888
    PCTESTDEV_1     N8    3.7284894837

    PCTESTHLD_0     N8    10.091681045
    PCTESTHLD_1     N8    3.8548752834


    /*--- NORMALIZED ---*/

    libname lgs "d:/lgs;

    data lgs.lgs_liftnormalized; /*--- just percents ---*/
      set workx.lgs.lynplt;
    run;quit;

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
