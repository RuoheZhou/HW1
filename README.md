README
================

``` r
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 4.0.2

``` r
library(tidyverse)
```

    ## Warning: package 'tidyverse' was built under R version 4.0.2

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.3     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.4     ✓ dplyr   1.0.4
    ## ✓ tidyr   1.1.2     ✓ stringr 1.4.0
    ## ✓ readr   1.4.0     ✓ forcats 0.5.0

    ## Warning: package 'ggplot2' was built under R version 4.0.2

    ## Warning: package 'tibble' was built under R version 4.0.2

    ## Warning: package 'tidyr' was built under R version 4.0.2

    ## Warning: package 'readr' was built under R version 4.0.2

    ## Warning: package 'purrr' was built under R version 4.0.2

    ## Warning: package 'dplyr' was built under R version 4.0.2

    ## Warning: package 'forcats' was built under R version 4.0.2

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter()         masks stats::filter()
    ## x readr::guess_encoding() masks rvest::guess_encoding()
    ## x dplyr::lag()            masks stats::lag()

``` r
library(readr)
library(dplyr)
webpage <- read_html("https://guide.wisc.edu/faculty/")
```

``` r
result <- webpage %>% html_nodes(".uw-people") %>% html_text2()
```

``` r
split1 = strsplit(result, '\n\n\n') 
df <- data.frame(name = character(), position = character(), department = character(), degree = character())
```

``` r
for (n in 1:length(split1)){
  for (i in 1:length(split1[[n]])){
    individual <- strsplit(split1[[n]][i], '\n')
    if (length(individual[[1]]) == 4){
      df[nrow(df) + 1, ] = individual[[1]]
    }
  }
}
df
```

    ##                                        name                    position
    ## 1                           ABBOTT,DAVID H.                   Professor
    ## 2                        ABD-ELSAYED,ALAA A       Assoc Professor (Chs)
    ## 3                          ABDUALLAH,FAISAL                   Professor
    ## 4                      ABRAHAM,OLUFUNMILOLA         Assistant Professor
    ## 5                           ABRAMS,SAMANTHA              Assoc Lecturer
    ## 6                              ABRAMSON,LYN                   Professor
    ## 7                             ACKER,LINDSAY                    Lecturer
    ## 8                           ACKERMAN,STEVEN                   Professor
    ## 9                    ADAMCZYK,PETER GABRIEL         Assistant Professor
    ## 10                   ADAMES-CORRALIZA,ANGEL         Assistant Professor
    ## 11                              ADAMS,AERON          Clinical Asst Prof
    ## 12                              ADAMS,MEGAN          Asst Faculty Assoc
    ## 13                             ADCOCK,SARAH         Assistant Professor
    ## 14                   ADDINGTON,REBECCA LYNN             Senior Lecturer
    ## 15                              ADDO,FENABA         Associate Professor
    ## 16                             ADELL,SANDRA                   Professor
    ## 17                               AFFI,ABOUD  Clinical Adjunct Professor
    ## 18                         AGARWAL,PRIYANKA         Assistant Professor
    ## 19                            AGASIE,ROBERT       Instrmt Innovator/Ins
    ## 20                             AGOKE,ADEOLA          Asst Faculty Assoc
    ## 21                     AHLQUIST,PAUL GERALD                   Professor
    ## 22                              AHMAD,NIHAL                   Professor
    ## 23                          AHMED,AZAM SYED       Assoc Professor (Chs)
    ## 24                               AHN,JAERIN         Assoc Faculty Assoc
    ## 25                                  AHN,SUE                   Professor
    ## 26                              AHN,YEOHYUN         Assistant Professor
    ## 27                   AHRENS,SARAH ELIZABETH         Clinical Assoc Prof
    ## 28                              AI,ALBERT L          Visiting Asst Prof
    ## 29                          AIKEN,JEFFREY P          Adjunct Instructor
    ## 30                             AIZAWA,NAOKI         Assistant Professor
    ## 31                             AJMANI,VIVEK         Assoc Faculty Assoc
    ## 32                            AKELLA,ADITYA                   Professor
    ## 33                            AL-ADRA,DAVID         Assistant Professor
    ## 34                           AL-SUBU,AWNI M        Asst Professor (Chs)
    ## 35                           ALAGOZ,OGUZHAN                   Professor
    ## 36                            ALARID,ELAINE                   Professor
    ## 37                          ALATOUT,SAMER N         Associate Professor
    ## 38                         ALBARGHOUTHI,AWS         Assistant Professor
    ## 39                             ALBERS,CRAIG         Associate Professor
    ## 40                             ALBERT,LAURA                   Professor
    ## 41                   ALBERTINI,MARK RICHARD                   Professor
    ## 42                    ALCALA GALAN,MERCEDES         Associate Professor
    ## 43                                ALDAG,RAY                   Professor
    ## 44                       ALDER,SIMEON DAVID           Faculty Associate
    ## 45               ALEXANDER,ANDREW LAFAYETTE                   Professor
    ## 46                         ALEXANDER,ANGELA           Faculty Associate
    ## 47                      ALEXANDER,LACEY ANN          Clinical Asst Prof
    ## 48                            ALI,SHANTEL D        Asst Prof Of Mil Sci
    ## 49                        ALI,SYED EKHTEYAR             Senior Lecturer
    ## 50                        ALIBALI,MARTHA W.                   Professor
    ## 51                            ALISCH,REID S         Assistant Professor
    ## 52                           ALLEN,CAITILYN                   Professor
    ## 53                              ALLEN,DAVID                   Professor
    ## 54                            ALLEN,HEATHER         Associate Professor
    ## 55                               ALLEN,MATT                   Professor
    ## 56                        ALLEWAERT,MONIQUE         Associate Professor
    ## 57                             ALLIE,MARK C           Faculty Associate
    ## 58                           ALONSO,ARACELI                Dis Lecturer
    ## 59                     ALTINO,SOH-HYUN PARK         Associate Professor
    ## 60                           ALTSCHAFL,BETH           Faculty Associate
    ## 61                            ALTSECH,MOSES                    Lecturer
    ## 62                              ALTWIES,JOY           Faculty Associate
    ## 63                      ALVAREZ,ELIZABETH E          Clinical Asst Prof
    ## 64                           ALVAREZ,SAYLIN             Senior Lecturer
    ## 65                     AMADOR-NOGUEZ,DANIEL         Associate Professor
    ## 66                               AMANN,KURT         Associate Professor
    ## 67                       AMASINO,RICHARD M.                   Professor
    ## 68                   AMATO,FELICE CATHERINE                    Lecturer
    ## 69                              AMINE,LAILA         Associate Professor
    ## 70                             AMSBARY,PAUL          Adjunct Assoc Prof
    ## 71                               AN,PANDUAN          Visiting Asst Prof
    ## 72                              AN,ZHE GIGI         Assistant Professor
    ## 73                     ANANTHARAMAN,KARTHIK         Assistant Professor
    ## 74                       ANCOS GARCIA,PABLO         Associate Professor
    ## 75                         ANDERSEN,CLAUS E         Assistant Professor
    ## 76                           ANDERSON,DAVID                   Professor
    ## 77                         ANDERSON,DAVID F                   Professor
    ## 78                         ANDERSON,KATHRYN                    Lecturer
    ## 79                            ANDERSON,LORI         Assistant Professor
    ## 80                            ANDERSON,MARK         Assistant Professor
    ## 81                           ANDERSON,PETER             Senior Lecturer
    ## 82                      ANDERSON,RICHARD A.                   Professor
    ## 83                         ANDERSON,ROZALYN         Associate Professor
    ## 84                           ANDES,DAVID R.                   Professor
    ## 85                          ANDREAE,SUSAN J         Assistant Professor
    ## 86                    ANDRESEN,CHRISTIAN G.         Assistant Professor
    ## 87                           ANDREWS,JOSEPH         Assistant Professor
    ## 88                           ANDREWS,LISA M         Assoc Faculty Assoc
    ## 89                              ANDREWS,URI         Associate Professor
    ## 90                        ANDRZEJEWSKI,ANNA                   Professor
    ## 91                               ANE,CECILE                   Professor
    ## 92                          ANE,JEAN-MICHEL                   Professor
    ## 93                              ANEX,ROBERT                   Professor
    ## 94                       ANGENENT,SIGURD B.                   Professor
    ## 95             ANGULO BRACHO,HERNAN LIZARDO         Clinical Instructor
    ## 96                           ANGUS,JENNIFER                   Professor
    ## 97                             ANIBAS,CALLI         Assoc Research Spec
    ## 98                           ANIBAS,MELISSA          Clinical Asst Prof
    ## 99                               ANJUM,UMAR         Research Specialist
    ## 100                              ANNA,ERIKA          Asst Faculty Assoc
    ## 101                          ANSARI,ASEEM Z                   Professor
    ## 102                         ANTONY,KATHLEEN        Asst Professor (Chs)
    ## 103                        ARCHAMBAULT,JOHN            Assistant Dean/L
    ## 104                    ARCHDEACON,THOMAS J.                   Professor
    ## 105                                  ARD,BJ         Assistant Professor
    ## 106                           AREFEVA,ALINA         Assistant Professor
    ## 107                             ARENDT,LISA         Assistant Professor
    ## 108                             ARFA,SANDRA           Faculty Associate
    ## 109                            ARINKIN,DIMA                   Professor
    ## 110                       ARMSTRONG,GRANT W         Associate Professor
    ## 111                        ARMSTRONG,JOSHUA         Associate Professor
    ## 112                    ARNDT,KIMBERLY KEGEL  Clinical Adjunct Asst Prof
    ## 113                          ARNOLD,MICHAEL                   Professor
    ## 114                 ARNOLDY,COURTNEY JEANNE         Clinical Instructor
    ## 115                            ARORA,NEERAJ                   Professor
    ## 116                ARPACI-DUSSEAU,ANDREA C.                   Professor
    ## 117                 ARPACI-DUSSEAU,REMZI H.                   Professor
    ## 118                       ARRIAGA,FRANCISCO         Associate Professor
    ## 119               ARRIOLA APELO,SEBASTIAN I         Assistant Professor
    ## 120                            ARTHUR,EMILY         Associate Professor
    ## 121                 ASCHENBROICH,SOPHIE ANN          Clinical Asst Prof
    ## 122                             ASEN,ROBERT                   Professor
    ## 123           ASHTON,LYDIA MAGDALENA TEJEDA         Assistant Professor
    ## 124                         ASHTON,RANDOLPH         Associate Professor
    ## 125                           ASIF,MUHAMMAD                    Lecturer
    ## 126                        ASMUS,JENNIFER M                   Professor
    ## 127           ASSADI-PORTER,FARIBA MASOUMEH              Assoc Lecturer
    ## 128                            ASTOR,BRAD C                   Professor
    ## 129                          ASTRELLA,JULIE         Clinical Assoc Prof
    ## 130                         ATAPATTU,SUMUDU         Dis Admin Prgm Spec
    ## 131                        ATTIE,ALAN DAVID                   Professor
    ## 132                            ATUCHA,AMAYA         Assistant Professor
    ## 133                            AUDHYA,ANJON                   Professor
    ## 134                     AUERBACH,EMILY KATE                   Professor
    ## 135                           AUGER,ANTHONY                   Professor
    ## 136                     AUGHENBAUGH,WILLIAM             Professor (Chs)
    ## 137                        AULIK,NICOLE ANN          Clinical Asst Prof
    ## 138                          AUNG,HTET HTET              Assoc Lecturer
    ## 139                          AUSDERAU,KARLA         Associate Professor
    ## 140                          AUSTERWEIL,JOE         Assistant Professor
    ## 141                            AVEY,GREGORY       Assoc Professor (Chs)
    ## 142                       AVRAMENKO,RICHARD                   Professor
    ## 143              AYARI BEN HADJ KACEM,MOUNA         Assoc Faculty Assoc
    ## 144                            AYD,SHARON W          Adjunct Assoc Prof
    ## 145                 AZOCAR,SAMUEL ALEJANDRO             Senior Lecturer
    ## 146                            AZODI,JAHANA          Asst Faculty Assoc
    ## 147                           BABAL,JESSICA        Asst Professor (Chs)
    ## 148                              BABAR,YASH         Assistant Professor
    ## 149                             BABCOCK,SUE                   Professor
    ## 150                               BACH,ERIC                   Professor
    ## 151                        BACH,JONATHAN F.         Clinical Assoc Prof
    ## 152                        BACH,TAIYA RENAE          Asst Faculty Assoc
    ## 153                          BACK,LARISSA E         Associate Professor
    ## 154                        BAHIA,HUSSAIN U.                   Professor
    ## 155                                BAI,YANG         Associate Professor
    ## 156                         BAILEY,HANNAH E            Assistant Dean/M
    ## 157                        BAIR,JESSE JONAS          Adjunct Instructor
    ## 158                               BAIRD,IAN                   Professor
    ## 159                             BAKER,ANGIE         Clinical Instructor
    ## 160                        BAKER,BERNADETTE                   Professor
    ## 161                             BAKER,TRACY         Associate Professor
    ## 162                             BAKKEN,LORI       Honorary Assoc/Fellow
    ## 163                       BAKSHI,VAISHALI P         Associate Professor
    ## 164                               BAL,AYDIN                   Professor
    ## 165                        BALANTEKIN,A. B.                   Professor
    ## 166                        BALDACCHINO,JOHN                   Professor
    ## 167                           BALDO,BRIAN A         Associate Professor
    ## 168                     BALDRIDGE,BIANCA J.         Associate Professor
    ## 169                   BALDRIDGE,ELIZABETH M                    Lecturer
    ## 170                            BALDWIN,CODY           Faculty Associate
    ## 171              BALLESTEROS CHAVEZ,JESUS A              Assoc Lecturer
    ## 172                            BALSTER,NICK                   Professor
    ## 173                            BANERJEE,MOU         Assistant Professor
    ## 174                          BANERJEE,SUMAN                   Professor
    ## 175                     BANKS,MATTHEW ISAAC                   Professor
    ## 176                           BARAK,PHILLIP                   Professor
    ## 177                   BARAK-CUNNINGHAM,JERI                   Professor
    ## 178                     BARBATO,ERIN MURPHY          Clinical Asst Prof
    ## 179                          BARCELOS,CHRIS         Assistant Professor
    ## 180                            BARCZI,STEVE             Professor (Chs)
    ## 181                         BARFORD,CAROL L             Senior Lecturer
    ## 182                          BARFORD,PAUL R                   Professor
    ## 183                    BARGER,AMY JOSEPHINE                   Professor
    ## 184                           BARGER,VERNON                   Professor
    ## 185                         BARHAM,BRADFORD                   Professor
    ## 186                           BARICH,JOSEPH             Senior Lecturer
    ## 187                            BARLETT,CARL                    Lecturer
    ## 188                           BARNARD,ERLIN       Dis Faculty Associate
    ## 189                            BARNARD,MARK                    Lecturer
    ## 190                             BARNES,JILL         Assistant Professor
    ## 191                         BARNETT,SUSANNE       Assoc Professor (Chs)
    ## 192                   BARRETT,BRUCE PATRICK                   Professor
    ## 193                           BARRETT,KEVIN              Assoc Lecturer
    ## 194                 BARRETT,PATRICK STEPHEN         Assoc Faculty Assoc
    ## 195                          BARRY,AMY QUAN                   Professor
    ## 196                             BARRY,LYNDA                   Professor
    ## 197                           BART,DAVID J.         Associate Professor
    ## 198                             BARTA,CHERI           Faculty Associate
    ## 199                         BARTFELD,JUDITH                   Professor
    ## 200                           BARTH,MICHAEL              Assoc Lecturer
    ## 201                     BARTHOLOMAY,LYRIC C                   Professor
    ## 202                        BARTHOLOMEW,KYLE         Clinical Instructor
    ## 203                      BARTLETT,HEATHER L             Professor (Chs)
    ## 204                         BARTLETT,LESLEY                   Professor
    ## 205                       BARTOL,LAURA JEAN         Assoc Faculty Assoc
    ## 206                              BARZEN,JEB           Adjunct Asst Prof
    ## 207                       BASHIRULLAH,ARASH         Associate Professor
    ## 208                       BASKAYA,MUSTAFA K                   Professor
    ## 209                        BATES,DESIREE M.       Inform Process Conslt
    ## 210                              BATES,ERIK          Visiting Asst Prof
    ## 211                                BATT,BOB         Associate Professor
    ## 212                    BATZLI,JANET MC CRAY       Dis Faculty Associate
    ## 213                              BAUER,ADAM        Asst Professor (Chs)
    ## 214                             BAUER,ANNIE         Assistant Professor
    ## 215                            BAUER,DANIEL                   Professor
    ## 216                  BAUER-ARMSTRONG,CHERYL           Faculty Associate
    ## 217                              BAUM,DAVID                   Professor
    ## 218           BAUTISTA MENDOZA,GLORIA ROCIO             Senior Lecturer
    ## 219                      BAUTISTA,LEONELO E         Associate Professor
    ## 220                           BAVAFA,HESSAM         Assistant Professor
    ## 221                          BAYOUTH,JOHN E                   Professor
    ## 222                    BAZALAKOVA,MIHAELA H        Asst Professor (Chs)
    ## 223                       BEA,MEGAN DOHERTY         Assistant Professor
    ## 224                       BEACH,JEREMY PAUL         Assoc Faculty Assoc
    ## 225                         BEAMSLEY,MARK B         Clinical Assoc Prof
    ## 226                      BEAN,DEREK MERRILL         Assoc Faculty Assoc
    ## 227                     BEARDEN,ELIZABETH B                   Professor
    ## 228                          BEATTIE,ROBERT           Faculty Associate
    ## 229                           BECHTOL,KEITH         Assistant Professor
    ## 230                    BECKER,AMY ELIZABETH           Faculty Associate
    ## 231                              BECKER,MEL                    Lecturer
    ## 232                           BECKHAM,SARAH          Asst Faculty Assoc
    ## 233                 BEDNAREK,SEBASTIAN YORK                   Professor
    ## 234                         BEDNARZ,BRYAN P         Associate Professor
    ## 235                           BEEBE,DAVID J                   Professor
    ## 236                           BEEBE,REBECCA       Sr Student Serv Coord
    ## 237                        BEGAM,RICHARD J.                   Professor
    ## 238                            BEHDAD,NADER                   Professor
    ## 239                         BEHM,JENNA LYNN                    Lecturer
    ## 240                           BEHNKE,RACHEL              Assoc Lecturer
    ## 241                            BEIA,SUZANNE         Artist-In-Residence
    ## 242                      BEILIN,KATARZYNA O                   Professor
    ## 243                            BELL,DAVID R         Associate Professor
    ## 244                          BELL,MICHAEL M                   Professor
    ## 245                         BELLING,SHAWN D                    Lecturer
    ## 246                            BELLMORE,AMY                   Professor
    ## 247                  BELTRAN PORTALES,DAVID          Visiting Asst Prof
    ## 248                       BEMENT,WILLIAM M.                   Professor
    ## 249            BENALLY THOMPSON,BRET ROBERT          Clinical Asst Prof
    ## 250                       BENDLIN,BARBARA B         Associate Professor
    ## 251                            BENEKER,JEFF                   Professor
    ## 252                          BENGSON,JOHN T         Associate Professor
    ## 253              BENGURIA DEPASSIER,SOLEDAD          Asst Faculty Assoc
    ## 254                       BENNETT,ALLYSON J                   Professor
    ## 255                      BENSKY,ANNE MARYSE          Adjunct Instructor
    ## 256                           BENSON,MARK E       Assoc Professor (Chs)
    ## 257                             BENT,ANDREW                   Professor
    ## 258                         BENTLEY,ELLISON          Clinical Professor
    ## 259                         BENTZ,MICHAEL L                   Professor
    ## 260                       BERGER,LAWRENCE M                   Professor
    ## 261                            BERGMANN,UWE                   Professor
    ## 262                           BERKELMAN,JIM           Faculty Associate
    ## 263                           BERLAND,LEEMA         Associate Professor
    ## 264                         BERLAND,MATTHEW         Associate Professor
    ## 265                         BERNARD,KRISTEN                   Professor
    ## 266                  BERNARD-DONALS,MICHAEL                   Professor
    ## 267                         BERNER,COURTNEY         Assoc Faculty Assoc
    ## 268                      BERNHARDT,DAVID T.             Professor (Chs)
    ## 269                          BERRIDGE,CRAIG                   Professor
    ## 270                     BERRY,JOHN FERGUSON                   Professor
    ## 271                     BERSHADY,MATTHEW A.                   Professor
    ## 272                       BERSON,ARGANTHAEL                    Lecturer
    ## 273                   BERSU,EDWARD THORWALD              Professor Emer
    ## 274                     BERTELSON,RYAN JOHN                    Lecturer
    ## 275                            BERTRAM,LISA         Associate Professor
    ## 276                      BERTRAM,TIMOTHY H.                   Professor
    ## 277                       BERVEN,NORMAN LEE              Professor Emer
    ## 278                      BESAW,LUKE ANTHONY          Adjunct Instructor
    ## 279                              BEST,KAREN             Senior Lecturer
    ## 280                             BETHKE,PAUL         Associate Professor
    ## 281                       BETZ,NATALIE ANNE           Faculty Associate
    ## 282                     BHATTACHARYYA,ANITA         Assistant Professor
    ## 283                         BHAVNANI,RIKHIL         Associate Professor
    ## 284                              BIER,VICKI                   Professor
    ## 285                         BILBIJA,KSENIJA                   Professor
    ## 286                   BILDER,ANNE ELIZABETH          Adjunct Instructor
    ## 287                      BILEN-ROSAS,GUELAY        Asst Professor (Chs)
    ## 288                     BINKLEY,JENNIFER L.          Clinical Asst Prof
    ## 289                             BIRD,IAN M.                   Professor
    ## 290               BIRKELAND,LAURA ELIZABETH       Sr Clin Genetic Couns
    ## 291                             BIRN,RASMUS         Associate Professor
    ## 292                           BISHOP,LAUREN         Assistant Professor
    ## 293                     BISHOP,MALACHY LIAM                   Professor
    ## 294                             BISHOP,SEAN           Faculty Associate
    ## 295                             BITZAN,AMOS         Assistant Professor
    ## 296                            BJORK,CLAIRE                    Lecturer
    ## 297                        BJORLING,DALE E.                   Professor
    ## 298                             BLACK,KEVIN                   Professor
    ## 299                      BLACKWELL,HELEN E.                   Professor
    ## 300                              BLAIR,SETH                   Professor
    ## 301                     BLAKE,JOCELYN MARIE        Asst Professor (Chs)
    ## 302                      BLANCHARD,DEANNA S         Clinical Instructor
    ## 303                          BLASIUS,LESLIE                   Professor
    ## 304                    BLAZEK,JENNIFER RUTH                    Lecturer
    ## 305                           BLEAM,WILLIAM                   Professor
    ## 306                          BLEEDORN,JASON         Clinical Assoc Prof
    ## 307                           BLOCH,BRANDON         Assistant Professor
    ## 308                              BLOCK,PAUL         Associate Professor
    ## 309                  BLOCK,STEPHEN BENJAMIN           Faculty Associate
    ## 310                             BLOCK,WALLY                   Professor
    ## 311                         BLONIEN,NATALIE           Faculty Associate
    ## 312                           BLOOM,VICKI D              Assoc Lecturer
    ## 313                      BLUE,JACOB MICHAEL              Assoc Lecturer
    ## 314                              BLUM,BARAK         Assistant Professor
    ## 315                        BLUM,HANNAH BETH         Assistant Professor
    ## 316                            BLYTHE,VERDA           Faculty Associate
    ## 317                     BOADO,JOEL MAGDALES              Assoc Lecturer
    ## 318                       BOCHSLER,PHILIP N          Clinical Professor
    ## 319                             BOCK,ADAM J                    Lecturer
    ## 320               BOCK-SHONKWILER,JULIE ANN              Assoc Lecturer
    ## 321                            BOEDER,STEVE           Faculty Associate
    ## 322           BOEKHOFF-FALK,GRACE ELISABETH         Associate Professor
    ## 323                     BOELDT,DEREK STEVEN         Assistant Professor
    ## 324                            BOERSMA,JOHN              Assoc Lecturer
    ## 325                BOGGESS,JACQUELYN LOUISE                    Lecturer
    ## 326                       BOHLIG,AMANDA JAN  Clinical Adjunct Asst Prof
    ## 327                      BOLDYREV,STANISLAV                   Professor
    ## 328                  BOLLING,BRADLEY WARREN         Associate Professor
    ## 329                             BOLT,DANIEL                   Professor
    ## 330                            BOLY,MELANIE         Assistant Professor
    ## 331                        BOMKAMP,TAMMY M.         Clinical Instructor
    ## 332                          BONAMICI,CHLOE         Assistant Professor
    ## 333                        BONAZZA,RICCARDO                   Professor
    ## 334                          BONK,NICOLE A.        Asst Professor (Chs)
    ## 335                         BOOK,EMILY KATE           Adjunct Asst Prof
    ## 336                          BOOSKE,JOHN H.                   Professor
    ## 337                              BOOTH,ERIC                    Lecturer
    ## 338                     BOOTHALINGAM,SRIRAM         Assistant Professor
    ## 339                      BOROWSKI,KRZYSZTOF              Assoc Lecturer
    ## 340                             BOSE,TULIKA                   Professor
    ## 341                          BOSWELL,EDWARD         Assoc Faculty Assoc
    ## 342                           BOSWELL,LAIRD                   Professor
    ## 343                    BOTERO,BEATRIZ LUCIA                    Lecturer
    ## 344                               BOTEZ,DAN                   Professor
    ## 345                            BOTHAM,SARAH           Faculty Associate
    ## 346                  BOUCHER,JOSEPH WILLIAM             Senior Lecturer
    ## 347                           BOUGHTON,SARA              Assoc Lecturer
    ## 348                             BOUNDY,TERI                    Lecturer
    ## 349           BOURG HACKER,DOMINIQUE CORINE                    Lecturer
    ## 350                         BOUSQUET,GILLES                   Professor
    ## 351                     BOUTILIER,JUSTIN J.         Assistant Professor
    ## 352                              BOW,LESLIE                   Professor
    ## 353                              BOWE,SCOTT                   Professor
    ## 354                           BOWEN,JEFF J.          Adjunct Instructor
    ## 355                      BOWER,GLENN ROBERT           Faculty Associate
    ## 356                          BOWERS,BARBARA                   Professor
    ## 357                      BOWIE,KATHERINE A.                   Professor
    ## 358                          BOWLING,JOSEPH                    Lecturer
    ## 359                             BOWMAN,MATT             Senior Lecturer
    ## 360                             BOYDSTON,AJ                   Professor
    ## 361                             BRACE,CHRIS         Associate Professor
    ## 362                         BRACHMAN,LAURIE             Senior Lecturer
    ## 363                      BRADBURY,ELIZABETH              Assoc Lecturer
    ## 364                     BRADEN,MAIA NYSTRUM       Honorary Assoc/Fellow
    ## 365                   BRADFIELD,CHRISTOPHER                   Professor
    ## 366                     BRADLEY,KRISTIN ANN             Professor (Chs)
    ## 367                          BRANCH,KRISTIN           Faculty Associate
    ## 368                     BRANCHAW,JANET LYNN         Assistant Professor
    ## 369                        BRANDT,CURTIS R.                   Professor
    ## 370                           BRANTLY,SUSAN                   Professor
    ## 371                          BRAR,VICTOR W.         Assistant Professor
    ## 372                         BRASIER,ALLAN R                   Professor
    ## 373                            BRATZKE,LISA         Associate Professor
    ## 374                           BRAUER,MARKUS                   Professor
    ## 375                         BRAUNGINN,JENNY         Assoc Faculty Assoc
    ## 376                           BRAUS,MICHAEL       Honorary Assoc/Fellow
    ## 377                           BRAVER,JOSHUA         Assistant Professor
    ## 378                             BRAY,LORA N              Assoc Lecturer
    ## 379                     BREEDLOVE,TRISTAN S         Clinical Instructor
    ## 380                      BREKKE,LINDSAY RAE              Assoc Lecturer
    ## 381                         BRENNAN,MICHAEL           Adjunct Professor
    ## 382                          BRENNER,RACHEL                   Professor
    ## 383                     BRESCHAK,JON THOMAS           Faculty Associate
    ## 384                          BRESLOW,ROBERT       Assoc Professor (Chs)
    ## 385                       BRESNICK,EMERY H.                   Professor
    ## 386                        BREUER,RYAN MARK          Clinical Asst Prof
    ## 387                   BRIEL,HALEY ELIZABETH          Asst Faculty Assoc
    ## 388                 BRIGGS,KATHERINE CHAREK                    Lecturer
    ## 389                         BRIGHOUSE,HARRY                   Professor
    ## 390                       BRINSKO,ELEANOR O              Assoc Lecturer
    ## 391                          BRITLAND,KAREN                   Professor
    ## 392                             BRITO,TONYA                   Professor
    ## 393                       BROCKLISS,WILLIAM         Associate Professor
    ## 394                             BROMAN,KARL                   Professor
    ## 395                      BRONKHORST,CURT A.                   Professor
    ## 396                           BROOKE,STEVEN         Assistant Professor
    ## 397                       BROOKS,ERIN GRACE             Professor (Chs)
    ## 398               BROOKS,NATHANIEL PHILLIPS       Assoc Professor (Chs)
    ## 399                        BROOKSBY,RICHARD         Clinical Instructor
    ## 400                      BROSSARD,DOMINIQUE                   Professor
    ## 401                   BROUNTS,SABRINA HELEN          Clinical Professor
    ## 402                           BROW,DAVID A.                   Professor
    ## 403                          BROWN,BRADFORD                   Professor
    ## 404                          BROWN,DAVID P.                   Professor
    ## 405                            BROWN,DUSTIN              Assoc Lecturer
    ## 406                     BROWN,HEIDI WENDELL         Assistant Professor
    ## 407                            BROWN,JOSHUA          Clinical Asst Prof
    ## 408                        BROWN,LAWRENCE T         Visiting Assoc Prof
    ## 409                           BROWN,MATTHEW        Asst Professor (Chs)
    ## 410                           BROWN,MATTHEW         Assistant Professor
    ## 411                      BROWN,RANDALL TODD         Associate Professor
    ## 412                      BRUCE,MICHAEL JOHN              Assoc Lecturer
    ## 413                        BRUNKARD,JACOB O         Assistant Professor
    ## 414                        BRUNOLD,THOMAS C                   Professor
    ## 415                        BRYAN,GINA MARIE          Clinical Professor
    ## 416                               BRYAN,TOM          Asst Faculty Assoc
    ## 417                        BUCCINI,STEFANIA                   Professor
    ## 418             BUCHBERGER JONES,AMANDA RAE          Asst Faculty Assoc
    ## 419                      BUCK,DOUGLAS SCOTT          Adjunct Instructor
    ## 420      BUCKINGHAM,TANYA MICHELLE ANDERSEN       Instructl Prg Mgr Iii
    ## 421                         BUDGE,STEPHANIE         Associate Professor
    ## 422                             BUGNI,TIM S                   Professor
    ## 423                                BUHL,TIM                    Lecturer
    ## 424                        BUHNEMANN,GUDRUN                   Professor
    ## 425                     BUHR-LAWLER,MELANIE          Clinical Professor
    ## 426                          BUISCH,DERRICK                   Professor
    ## 427                         BULLER,ANDREW R         Assistant Professor
    ## 428                         BULLOCK,ERIKA C         Assistant Professor
    ## 429                       BULLTAIL,GRACE A.         Assistant Professor
    ## 430                           BUNN,HENRY T.                   Professor
    ## 431                            BURDEN,BARRY                   Professor
    ## 432                          BURGER,CORINNA         Associate Professor
    ## 433                         BURGESS,RICHARD              Professor Emer
    ## 434                         BURGOYNE,JOSEPH              Assoc Lecturer
    ## 435                       BURIVALOVA,ZUZANA         Assistant Professor
    ## 436                             BURK,LINNEA         Clinical Assoc Prof
    ## 437                     BURKARD,MARK EDWARD                   Professor
    ## 438                       BURKHOLDER,KRISTY           Faculty Associate
    ## 439                      BURKI,KRISTIN ANNE          Asst Faculty Assoc
    ## 440                   BURLINGHAM,WILLIAM J.                   Professor
    ## 441                              BURNS,ERIK         Assoc Faculty Assoc
    ## 442              BURNS,MARGUERITE ELIZABETH         Associate Professor
    ## 443                       BURSTYN,JUDITH N.                   Professor
    ## 444                           BURT,BRIAN A.         Assistant Professor
    ## 445                   BURTON,ALEXANDRA JANE          Clinical Asst Prof
    ## 446                           BURTON,BRIANA         Associate Professor
    ## 447                         BURTON,ROBERT J              Assoc Lecturer
    ## 448                      BURTON,SKYLAR TREE          Visiting Asst Prof
    ## 449                                BUSH,LIZ         Assistant Professor
    ## 450                        BUSSE,WILLIAM W.                   Professor
    ## 451                  BUTCHER,KACIE LUCCHINI           Adjunct Asst Prof
    ## 452                       BUTCHER,SAMUEL E.                   Professor
    ## 453                    BUTLER,JEFFREY DAVID                    Lecturer
    ## 454                         BUTLER,MARGARET         Associate Professor
    ## 455                        BYKHOVSKAYA,ANNA              Assoc Lecturer
    ## 456                        BYKOVSKYI,ANDREA         Assistant Professor
    ## 457                        BYKOWSKI,ERIN F.                    Lecturer
    ## 458                     BYRD-MCPHEE,MICHELE          Adjunct Instructor
    ## 459                        CABRERA,VICTOR E                   Professor
    ## 460                   CAHILL,MICHAEL EDWARD         Assistant Professor
    ## 461                             CAHILL,NICK                   Professor
    ## 462                              CAI,JIN-YI                   Professor
    ## 463                               CAI,WEIBO                   Professor
    ## 464                        CALDARARU,ANDREI                   Professor
    ## 465                  CALDERON,CLAUDIA IRENE         Assoc Faculty Assoc
    ## 466                         CALDERON,JAVIER                   Professor
    ## 467                     CALDWELL,MICHAEL F.             Senior Lecturer
    ## 468                          CALHOUN,JOSHUA         Associate Professor
    ## 469                           CALLACI,EMILY         Associate Professor
    ## 470                      CALOMINO,SALVATORE         Associate Professor
    ## 471                  CAMAL,JEROME SEBASTIEN         Associate Professor
    ## 472                     CAMARA,NJAMEH MARIA                    Lecturer
    ## 473                         CAMERON,KENNETH                   Professor
    ## 474                           CAMERON,STARR          Clinical Asst Prof
    ## 475                               CAMP,BILL             Senior Lecturer
    ## 476                         CAMPAGNOLA,PAUL                   Professor
    ## 477                           CAMPBELL,ANNA         Associate Professor
    ## 478                      CAMPBELL,JEFFERY L       Instructor Of Mil Sci
    ## 479                             CANON,DAVID                   Professor
    ## 480                         CANTOR,JASON R.         Assistant Professor
    ## 481                           CANTWELL,TONY              Assoc Lecturer
    ## 482                      CAPITINI,CHRISTIAN         Associate Professor
    ## 483                        CAPTAIN,AMANDA K          Asst Faculty Assoc
    ## 484                         CARAYON,PASCALE                   Professor
    ## 485                 CARAZA-HARTER,TYLER RAY          Asst Faculty Assoc
    ## 486                           CARCHMAN,EVIE         Assistant Professor
    ## 487                       CARDA,RONNIE DEAN           Faculty Associate
    ## 488                         CARDIFF,MICHAEL         Associate Professor
    ## 489                         CAREY,HANNAH V.                   Professor
    ## 490                          CARL,BRADLEY R                    Lecturer
    ## 491                        CARLSMITH,DUNCAN                   Professor
    ## 492                            CARLSON,JANE           Adjunct Professor
    ## 493                           CARLSON,MARCY                   Professor
    ## 494              CARLSSON,CYNTHIA MCDONNELL                   Professor
    ## 495                           CARLSSON,ERIC                    Lecturer
    ## 496                        CARNE,DANIELLE L          Adjunct Instructor
    ## 497                              CARR,SUSAN         Clinical Instructor
    ## 498                     CARROLL,ALAN ROBERT                   Professor
    ## 499                          CARROLL,RACHEL                    Lecturer
    ## 500                        CARSTENSEN,PETER              Professor Emer
    ## 501                       CARTER,SARAH ANNE          Visiting Professor
    ## 502                      CASCIO,CHRISTOPHER         Assistant Professor
    ## 503                              CASID,JILL                   Professor
    ## 504                      CASIMIR,DAVID ALAN          Adjunct Instructor
    ## 505                         CASTRONOVO,RUSS                   Professor
    ## 506                          CATTAPAN,MOIRA         Clinical Instructor
    ## 507                       CATTAPAN,STEVEN E         Clinical Assoc Prof
    ## 508                         CAUL,KIMBERLY J         Clinical Assoc Prof
    ## 509                        CAVAGNERO,SILVIA                   Professor
    ## 510                         CAVINESS,JULIET         Clinical Instructor
    ## 511                 CEDERSTROM,B. MARCUS L.          Asst Faculty Assoc
    ## 512                            CENGIZ,PELIN       Assoc Professor (Chs)
    ## 513                       CENTOLA,MICHAEL J        Asst Prof Of Mil Sci
    ## 514                   CEREZO PAREDES,ALICIA         Associate Professor
    ## 515                              CERO,SHAUN        Asst Prof Of Mil Sci
    ## 516                         CERULLI,ANTHONY         Associate Professor
    ## 517                           CHACON,MARCUS       Assoc Professor (Chs)
    ## 518                   CHAIET,SCOTT RANDOLPH        Asst Professor (Chs)
    ## 519                  CHAMBERLAIN,CONNIE SUE         Associate Scientist
    ## 520            CHAMBERS,ANTHONY CHRISTOPHER             Senior Lecturer
    ## 521                       CHAMEDES,GIULIANA         Associate Professor
    ## 522                             CHAN,STELLA                    Lecturer
    ## 523                             CHANA,NADIA         Assistant Professor
    ## 524                            CHANCE,RON L           Faculty Associate
    ## 525                            CHANDA,BARON       Honorary Assoc/Fellow
    ## 526                       CHANDARANA,SHARAD             Senior Lecturer
    ## 527                           CHANDLER,BRAD           Faculty Associate
    ## 528                            CHANG,BRIANA         Associate Professor
    ## 529                               CHANG,HAO         Assistant Professor
    ## 530                              CHANG,LIZA          Research Associate
    ## 531                             CHANG,QIANG                   Professor
    ## 532                           CHANG,YU-CHAN          Visiting Asst Prof
    ## 533                        CHAPMAN,EDWIN R.                   Professor
    ## 534                CHAPMAN,ELIZABETH NICOLE          Clinical Asst Prof
    ## 535                     CHAPPELL,RICHARD J.                   Professor
    ## 536                        CHARLES,PAJARITA         Assistant Professor
    ## 537                              CHARO,ALTA                   Professor
    ## 538                        CHATTERJEE,RAHUL         Assistant Professor
    ## 539                            CHATTI,LEILA         Assoc Faculty Assoc
    ## 540                        CHAVAS,JEAN-PAUL                   Professor
    ## 541                           CHAVEZ,MONIKA                   Professor
    ## 542                 CHAVEZ-CONTRERAS,RAFAEL                Dis Lecturer
    ## 543                           CHAWLA,SHUCHI                   Professor
    ## 544                         CHEADLE,MICHAEL             Senior Lecturer
    ## 545                                CHEN,GAO         Assistant Professor
    ## 546                         CHEN,GUANG-HONG                   Professor
    ## 547                            CHEN,GUANHUA         Assistant Professor
    ## 548                           CHEN,HUI-CHUN                    Lecturer
    ## 549                            CHEN,KAIPING         Assistant Professor
    ## 550                             CHEN,LIANYI         Assistant Professor
    ## 551                                CHEN,NAN         Assistant Professor
    ## 552                          CHENEY,SCOTT B        Professor Of Mil Sci
    ## 553                           CHENG,CINDY I                   Professor
    ## 554                          CHEONG,YEONHEE                    Lecturer
    ## 555                      CHERWIN,KARIE LYNN              Assoc Lecturer
    ## 556                           CHESLER,NAOMI                   Professor
    ## 557                          CHEWNING,BETTY                   Professor
    ## 558                         CHIANG,HAROLD D         Assistant Professor
    ## 559                             CHIEN,PETER                   Professor
    ## 560                      CHILDERS,MICHAEL R                   Professor
    ## 561                         CHINN,MENZIE D.                   Professor
    ## 562                            CHINN,SEDONA         Assistant Professor
    ## 563                          CHISHOLM,SALLY                   Professor
    ## 564                               CHIU,BILL                   Professor
    ## 565                               CHO,JACEE         Assistant Professor
    ## 566                        CHOI,CHRISTOPHER                   Professor
    ## 567                        CHOI,KYOUNG-SHIN                   Professor
    ## 568                             CHOI,WILLIE         Associate Professor
    ## 569                           CHOPRA,PREETI                   Professor
    ## 570                     CHOQUETTE,MATTHEW P       Assoc Prof Of Mil Sci
    ## 571                          CHOWDHARY,ZARA              Assoc Lecturer
    ## 572                           CHOY,JENNIFER         Assistant Professor
    ## 573                              CHOY,PEGGY         Associate Professor
    ## 574                       CHRISTENSEN,CRAIG          Adjunct Instructor
    ## 575                     CHRISTENSON,BRIDGET                    Lecturer
    ## 576                CHRISTIAN,BRADLEY THOMAS                   Professor
    ## 577                  CHRISTOPHERSON,MELISSA         Assoc Faculty Assoc
    ## 578                      CHRISTY,KATHERYN R         Assistant Professor
    ## 579                           CHUI,MICHELLE                   Professor
    ## 580                              CHUN,JI NA         Assistant Professor
    ## 581                           CHUN,RUTHANNE          Clinical Professor
    ## 582                          CHUNG,DANIEL J                   Professor
    ## 583                             CHUNG,KEVIN         Assistant Professor
    ## 584                             CHUNG,MOO K         Associate Professor
    ## 585                         CHYLLA,SAMANTHA              Assoc Lecturer
    ## 586                         CIANCIA,KATHRYN         Associate Professor
    ## 587                          CIRELLI,CHIARA                   Professor
    ## 588                        CIRUZZI,DOMINICK              Assoc Lecturer
    ## 589                             CISLER,JOSH         Associate Professor
    ## 590                         CIUCCI,MICHELLE         Associate Professor
    ## 591                         CLAESSENS,AMY E         Associate Professor
    ## 592                    CLARK,HEIDI JENNIFER                    Lecturer
    ## 593                              CLARK,JOEL                    Lecturer
    ## 594                       CLARK,LAURIE BETH                   Professor
    ## 595                           CLARK,LINDSAY         Assistant Professor
    ## 596                          CLARK,ROSEANNE                   Professor
    ## 597                             CLARK,SHARI           Faculty Associate
    ## 598                              CLARK,TERI                    Lecturer
    ## 599                    CLARK-PUJARA,CHRISTY         Associate Professor
    ## 600                    CLARKE,LORELEI LYNNE          Clinical Asst Prof
    ## 601                      CLATTERBUCK,HAYLEY         Assistant Professor
    ## 602                               CLAUS,JIM                   Professor
    ## 603                      CLAUSS,ARRIETTA W.           Faculty Associate
    ## 604                         CLAYTON,SARAH C         Associate Professor
    ## 605                           CLOSE,GLEN S.                   Professor
    ## 606                         COBEY,COLLEEN E           Faculty Associate
    ## 607                         COBIAN,DANIEL G        Asst Professor (Chs)
    ## 608                          COBURN,JESSICA          Clinical Asst Prof
    ## 609                             COCHRAN,AMY         Assistant Professor
    ## 610                 CODLYN,ROCHELLE ALLEXIA         Clinical Instructor
    ## 611                             CODNER,ERIC         Assoc Faculty Assoc
    ## 612                           CODY,PAULA JO       Assoc Professor (Chs)
    ## 613                         COE,CHRISTOPHER                   Professor
    ## 614                       COENEN,JAN WILLEM           Adjunct Professor
    ## 615                               COFF,RUSS                   Professor
    ## 616                            COFFEY,PATTI           Faculty Associate
    ## 617                  COHEN,ADRIAN NATHANIEL          Adjunct Instructor
    ## 618                             COHEN,STACY         Clinical Assoc Prof
    ## 619                       COLE,JUSTIN DAVID         Assoc Faculty Assoc
    ## 620                     COLEMAN,FRANCISKA A         Assistant Professor
    ## 621                            COLLIER,LARA         Associate Professor
    ## 622                    COLLINS,ELIZABETH A.         Clinical Instructor
    ## 623                      COLLINS,J. MICHAEL                   Professor
    ## 624                         COLLINS,JANE L.                   Professor
    ## 625                       COLLINS,MARY BETH                    Lecturer
    ## 626                         COLLINS,MICHAEL              Professor Emer
    ## 627                      COLLINS,SUSAN LYNN          Adjunct Instructor
    ## 628                       COLMAN,RICKI JEAN         Assistant Professor
    ## 629                             COLOPY,SARA          Clinical Asst Prof
    ## 630                           COLQUHOUN,JED                   Professor
    ## 631                          COLUMNA,LUIS A         Associate Professor
    ## 632                             COMBS,DAVID                   Professor
    ## 633                 CONAWAY,JESSICA DEBORAH         Assoc Faculty Assoc
    ## 634                            CONLEY,SHAWN                   Professor
    ## 635                          CONN,AUDREY M.         Clinical Assoc Prof
    ## 636                    CONNER,CRAIG PATRICK           Adjunct Asst Prof
    ## 637                           CONNOR,NADINE                   Professor
    ## 638                             CONRAD,CLIF                   Professor
    ## 639                          CONROY,COLLEEN         Assistant Professor
    ## 640                            CONROY,TESSA         Assistant Professor
    ## 641                            CONTI,JOSEPH         Associate Professor
    ## 642                           CONWAY,KELLEY                   Professor
    ## 643                        CONWELL,JORDAN A         Assistant Professor
    ## 644                             COOK,DANE B                   Professor
    ## 645                            COOK,NIGEL B                   Professor
    ## 646                              COOK,SUSAN                   Professor
    ## 647                       COOK,THOMAS DAVID             Professor (Chs)
    ## 648                           COON,JOSHUA J                   Professor
    ## 649                              COON,KERRI         Assistant Professor
    ## 650                             COOPER,LISA                   Professor
    ## 651                            COPA,ANNETTE                    Lecturer
    ## 652                        COPELOVITCH,MARK                   Professor
    ## 653                    COPPAGE ARANDA,KEIVA                    Lecturer
    ## 654                       COPPERSMITH,SUSAN                   Professor
    ## 655                             CORBAE,DEAN                   Professor
    ## 656                              CORBY,KATE                   Professor
    ## 657                     COREY,DANIEL JOSEPH          Visiting Asst Prof
    ## 658                           CORFIS,IVY A.                   Professor
    ## 659                 CORNELIUS,DANIEL JOSEPH                    Lecturer
    ## 660                     COSTANZO,ERIN SUSAN             Professor (Chs)
    ## 661                     COTTER,MEGHAN MARIE                    Lecturer
    ## 662                            COUET,ADRIEN         Assistant Professor
    ## 663                 COURTIER,ANNA M. BISHOP         Assoc Faculty Assoc
    ## 664                       COVALESKI,MARK A.                   Professor
    ## 665             COVINGTON,ALEXANDER MICHAEL              Assoc Lecturer
    ## 666                   COVINGTON,ELIZABETH E           Faculty Associate
    ## 667                         COWAN,EILEEN A.        Asst Professor (Chs)
    ## 668                          COX,MICHAEL M.                   Professor
    ## 669                             COXHEAD,IAN                   Professor
    ## 670                             COYLE,SCOTT         Assistant Professor
    ## 671                             COYNE,SARAH          Adjunct Instructor
    ## 672                           CRABB,RICHARD                    Lecturer
    ## 673                        CRACIUN,GHEORGHE                   Professor
    ## 674                       CRAIG,ELIZABETH A                   Professor
    ## 675                      CRAIG,RACHEL DANAE          Clinical Asst Prof
    ## 676                             CRALL,JAMES         Assistant Professor
    ## 677                   CRAMER,KATHERINE JEAN                   Professor
    ## 678                           CRAMER,STEVEN                   Professor
    ## 679                           CRAVEN,MARK W                   Professor
    ## 680                     CRAWFORD,LATASHA K.         Assistant Professor
    ## 681                            CRENSHAW,TOM                   Professor
    ## 682                              CRIM,ELTON          Clinical Professor
    ## 683                             CRONE,WENDY                   Professor
    ## 684                          CRONON,WILLIAM       Honorary Assoc/Fellow
    ## 685                             CROOK,DAVID                   Professor
    ## 686                            CROSS,LORI J                    Lecturer
    ## 687                         CROWTHER,SHAUNA             Senior Lecturer
    ## 688                   CRUICKSHANKS,KAREN J.                   Professor
    ## 689                           CRYNS,VINCENT                   Professor
    ## 690                 CULBERSON,WESLEY STUART       Assoc Professor (Chs)
    ## 691                    CULLINANE,MICHAEL M.       Dis Faculty Associate
    ## 692                            CULP,LINDSEY         Clinical Instructor
    ## 693                         CULVER,KATHLEEN         Associate Professor
    ## 694                      CUNSOLO,ALESSANDRO              Assoc Lecturer
    ## 695                          CURRIE,CAMERON                   Professor
    ## 696                               CURRY,TOM           Faculty Associate
    ## 697                          CURTIN,JOHN J.                   Professor
    ## 698                      CURTIS,KATHERINE J                   Professor
    ## 699                       CUTSFORTH,TANYA M        Instructl Prg Mgr Ii
    ## 700                   CZAJKOWSKI,CYNTHIA M.                   Professor
    ## 701               CZUPRYNSKI,CHARLES JOSEPH                   Professor
    ## 702                               DAHL,GARY         Assoc Faculty Assoc
    ## 703                          DAHLKE,KATELYN          Asst Faculty Assoc
    ## 704                                 DAI,JUN         Assistant Professor
    ## 705                             DAKES,CHRIS           Faculty Associate
    ## 706                             DALE,THOMAS                   Professor
    ## 707                          DAMSCHEN,ELLEN                   Professor
    ## 708                           DANAHER,DAVID                   Professor
    ## 709                            DANKO,ISTVAN             Professor (Chs)
    ## 710                           DANTONI,LORIS         Assistant Professor
    ## 711                           DASU,SRIDHARA                   Professor
    ## 712                      DAVIDSON,RICHARD J                   Professor
    ## 713                   DAVIS,ABIGAIL NANETTE           Adjunct Professor
    ## 714                         DAVIS,DAWN BELT         Associate Professor
    ## 715                           DAVIS,ELISE C                    Lecturer
    ## 716                               DAVIS,JIM                   Professor
    ## 717                             DAVIS,SARAH          Clinical Professor
    ## 718                           DAVIS,THULANI         Assistant Professor
    ## 719                          DAVOODI,AZADEH                   Professor
    ## 720                            DAWSON,JULIE         Associate Professor
    ## 721                  DE FERRARI,GUILLERMINA                   Professor
    ## 722                        DE GASPERI,DIEGO         Clinical Instructor
    ## 723                   DE LEON GATTI,NATALIA                   Professor
    ## 724                    DE VILLIERS,MELGARDT             Professor (Chs)
    ## 725                    DE WERD,LARRY ALBERT                   Professor
    ## 726                          DE WITT,JOHN R             Senior Lecturer
    ## 727                               DEAN,DOUG         Assistant Professor
    ## 728                               DEAN,JAKE           Faculty Associate
    ## 729                      DEBAISIEUX,MARTINE                   Professor
    ## 730                        DEBOER,DOUGLAS J                   Professor
    ## 731                            DECI,DAVID M       Assoc Professor (Chs)
    ## 732                   DECICCO,MICHAEL PETER          Asst Faculty Assoc
    ## 733                            DECROIX,GREG                   Professor
    ## 734                              DEITZ,RITT           Faculty Associate
    ## 735                         DEL PIA,ALBERTO         Associate Professor
    ## 736                        DELANNAY,MARTINE       Sr Student Serv Coord
    ## 737                  DELGADILLO,THERESA ANN                   Professor
    ## 738                           DELLER,STEVEN                   Professor
    ## 739                     DELSANDRO,ELIZABETH         Clinical Assoc Prof
    ## 740                        DELUCA,HECTOR F.              Professor Emer
    ## 741                     DEMARCO,CHRISTOPHER              Professor Emer
    ## 742                            DEMETS,CHUCK                   Professor
    ## 743                         DEMETS,DAVID L.                   Professor
    ## 744                      DEMING,DUSTIN ALAN         Associate Professor
    ## 745                          DEMIRALP,ILHAN                    Lecturer
    ## 746                       DEMPSEY,ROBERT J.                   Professor
    ## 747                       DEMURI,GREGORY P.             Professor (Chs)
    ## 748                     DEN HARTOG,DANIEL J               Dis Scientist
    ## 749               DENECKERE,RAYMOND JACQUES                   Professor
    ## 750                           DENG,QUANLING          Visiting Asst Prof
    ## 751                           DENG,YONGHENG                   Professor
    ## 752                        DENISSOV,SERGUEI                   Professor
    ## 753                      DENNIS JR,SAMUEL F                   Professor
    ## 754                           DENNIS,JOSEPH         Associate Professor
    ## 755                            DENNIS,SHAWN                    Lecturer
    ## 756                         DENT,ERIK WOLFE                   Professor
    ## 757                             DENU,JOHN M                   Professor
    ## 758                          DEPPELER,DEBRA           Faculty Associate
    ## 759                           DESAI,ANKUR R                   Professor
    ## 760                              DESAI,ANUJ                   Professor
    ## 761                           DESAN,SUZANNE                   Professor
    ## 762                      DESHPANDE,ABBISHEK          Visiting Asst Prof
    ## 763                       DETCHEVERRY,CHARO                   Professor
    ## 764                        DETWYLER,ANATOLY         Assistant Professor
    ## 765                   DEVINE,PATRICIA GRACE                   Professor
    ## 766                       DEVOSS,AMANDA KAY         Clinical Instructor
    ## 767                             DEWANE,JUDY       Assoc Professor (Chs)
    ## 768                             DEWEY,COLIN                   Professor
    ## 769                               DEY,MAHUA         Assistant Professor
    ## 770                       DHARWADKER,APARNA                   Professor
    ## 771                        DHARWADKER,VINAY                   Professor
    ## 772                      DIAKONIKOLAS,ILIAS         Associate Professor
    ## 773                     DIAKONIKOLAS,JELENA         Assistant Professor
    ## 774                         DIAMOND,CAROL A       Assoc Professor (Chs)
    ## 775                          DIAMOND,JOHN B                   Professor
    ## 776                  DIAS MOREIRA,ANA SOFIA         Post Grad Trainee 5
    ## 777                         DICKMANN,LESLIE         Assoc Faculty Assoc
    ## 778                DIEM,STEPHANIE JOSEPHINE         Assistant Professor
    ## 779                         DIESTELMANN,MEG          Asst Faculty Assoc
    ## 780                      DIETZ,AMY TRENTHAM                   Professor
    ## 781                          DIFFEE,GARY M.                   Professor
    ## 782                          DIGMAN,MATTHEW         Assistant Professor
    ## 783                            DILL,CHARLES                   Professor
    ## 784                          DILLARD,JOSEPH                   Professor
    ## 785                    DILWORTH-BART,JANEAN                   Professor
    ## 786                               DIMA,VLAD                   Professor
    ## 787                               DINH,HONG           Faculty Associate
    ## 788                              DINH,HUY Q         Assistant Professor
    ## 789                            DIORIO,CHRIS                    Lecturer
    ## 790                      DIPRETE BROWN,LORI       Dis Faculty Associate
    ## 791                            DIRAN,INGRID         Assistant Professor
    ## 792                         DISANZA,ANTHONY                   Professor
    ## 793                               DOAN,AN H                   Professor
    ## 794                             DOBBS,TERYL                   Professor
    ## 795                   DODGE FRANCIS,CAROLEE                   Professor
    ## 796                            DOEBLEY,JOHN                   Professor
    ## 797                        DOESCHER,MICHAEL         Assoc Faculty Assoc
    ## 798                             DOING,JAMES                   Professor
    ## 799                  DOMINGUEZ,PETER JOSEPH                   Professor
    ## 800                         DOMINGUEZ,SUSAN             Senior Lecturer
    ## 801                            DONG,FENGXIA                    Lecturer
    ## 802                                DONG,WEI                   Professor
    ## 803                           DONGHIA,ELENA         Associate Professor
    ## 804                      DONNETT,URI BARUCH         Clinical Instructor
    ## 805                             DONOHUE,TIM                   Professor
    ## 806                           DOPFER,DOERTE         Associate Professor
    ## 807                               DOPP,JOHN       Assoc Professor (Chs)
    ## 808                            DOREN,BONNIE         Associate Professor
    ## 809                        DORO,CHRISTOPHER          Clinical Asst Prof
    ## 810                            DOSS,GRAYSON          Clinical Asst Prof
    ## 811                      DOUGLAS,JON CALVIN         Clinical Assoc Prof
    ## 812                              DOWER,PAUL         Assistant Professor
    ## 813                             DOWNEY,GREG                   Professor
    ## 814                  DOYLE JR.,JAMES EDWARD          Adjunct Assoc Prof
    ## 815                             DRAKE,DAVID                   Professor
    ## 816                          DRAKE,JENNIFER         Clinical Instructor
    ## 817                      DRESSER,LAURA JILL          Clinical Asst Prof
    ## 818                           DRESSLER,ALEX         Associate Professor
    ## 819                      DRESSLER,KRISTOFER                    Lecturer
    ## 820                         DREWAL,HENRY J.                   Professor
    ## 821                          DREWRY,JESSICA         Assoc Faculty Assoc
    ## 822            DRUSCHKE,CAROLINE GOTTSCHALK         Associate Professor
    ## 823                              DU,SHELDON         Associate Professor
    ## 824                           DUBOIS,THOMAS                   Professor
    ## 825                           DUELL,THERESA         Associate Professor
    ## 826                       DUERST,BARBARA L.           Faculty Associate
    ## 827                      DUFFY,SEAN MICHAEL        Asst Professor (Chs)
    ## 828                          DUGAN,HILARY A         Assistant Professor
    ## 829                           DUMESIC,JAMES              Professor Emer
    ## 830                           DUNCAN,IAN D.                   Professor
    ## 831                     DUNCAN,JEANNE MARIE           Faculty Associate
    ## 832                       DUNCAN,LARISSA G.         Associate Professor
    ## 833                        DUNHAM,RANDALL B              Professor Emer
    ## 834                            DUNN,JACOB T         Assoc Faculty Assoc
    ## 835                          DUNN,RACHEL M.                    Lecturer
    ## 836                            DUNNE,JOHN D                   Professor
    ## 837                  DURKIN,MAUREEN SUZANNE                   Professor
    ## 838               DURRANCE,CHRISTINE PIETTE         Associate Professor
    ## 839                     DUSICK,ALLISON FRAN         Clinical Instructor
    ## 840                           DUTTON,ANDREA                   Professor
    ## 841                      DWYER,DAVID EDWARD         Clinical Assoc Prof
    ## 842                    DYKEMA,JENNIFER LYNN         Visiting Assoc Prof
    ## 843                    DYKMAN,CHARLES PIPER          Adjunct Instructor
    ## 844                     DYMARZ,TULLIA MARIA         Associate Professor
    ## 845                             EADIE,LOREN         Assoc Faculty Assoc
    ## 846                           EASLAND,HOLLY                    Lecturer
    ## 847                              EASON,JOHN         Associate Professor
    ## 848                             EASWAR,VIJI         Assistant Professor
    ## 849                         EATON,CARRIE A.         Sr Academic Curator
    ## 850                       EATON,JOSHUA SETH          Clinical Asst Prof
    ## 851                      EBERT,STEVEN CAREY          Clinical Professor
    ## 852                            ECKHARDT,JON         Associate Professor
    ## 853                   ECKHARDT,LEE LOCHBAUM         Associate Professor
    ## 854                              EDGAR,MARK                    Lecturer
    ## 855                            EDGE,HEATHER                    Lecturer
    ## 856                          EDGERTON,LARRY           Faculty Associate
    ## 857                           EDIGER,MARK D                   Professor
    ## 858                      EDMONDS,BRITTNEY M         Assistant Professor
    ## 859                     EDORO,AINEHI EJIEME         Assistant Professor
    ## 860                           EDWARDS,COREY        Instrumentation Tech
    ## 861                         EDWARDS,DOROTHY                   Professor
    ## 862                            EDWARDS,GREG           Faculty Associate
    ## 863                           EDWARDS,LOGAN              Assoc Prof L/I
    ## 864                          EDWARDS,MORGAN         Assistant Professor
    ## 865                   EDWARDS,TIMOTHY DAVID          Adjunct Instructor
    ## 866                           EGAN,PATRICIA             Senior Lecturer
    ## 867                             EGEA,JUAN F                   Professor
    ## 868                              EGEDAL,JAN                   Professor
    ## 869                              EGGERT,TOM           Faculty Associate
    ## 870                     EHLENBACH,MARY LYNN       Assoc Professor (Chs)
    ## 871                     EHRENTHAL,DEBORAH B                   Professor
    ## 872                         EHRLICH,DAVID E         Assistant Professor
    ## 873                       EICHELMAN,BURR S.             Professor (Chs)
    ## 874                              EIDE,DAVID                   Professor
    ## 875                    EIRING,KRISTINE MARY                    Lecturer
    ## 876                         EISENSTEIN,RICK                   Professor
    ## 877                             EITH,ALYSON          Clinical Professor
    ## 878                           EITZER,ANDREW         Clinical Instructor
    ## 879                            EKLUND,KATIE         Associate Professor
    ## 880                       EL-NOSSERY,NEVINE         Associate Professor
    ## 881              ELDRIDGE,HANNAH VANDEGRIFT         Associate Professor
    ## 882                     ELDRIDGE,MARLOWE W.                   Professor
    ## 883                           ELDRIDGE,MARY              Assoc Lecturer
    ## 884                       ELFENBEIN,JOHANNA         Assistant Professor
    ## 885                  ELICEIRI,KEVIN WILLIAM         Associate Professor
    ## 886                        ELKHOULY,MOHAMED          Visiting Asst Prof
    ## 887                        ELLENBERG,JORDAN                   Professor
    ## 888                           ELLINGER,LISA              Assoc Lecturer
    ## 889                     ELLIS WEISMER,SUSAN                   Professor
    ## 890                              ELLIS,LISA             Senior Lecturer
    ## 891                          ELLISON,AUBREY          Asst Faculty Assoc
    ## 892                     ELLISON,PAUL ANDREW         Assistant Professor
    ## 893                     ELLISON,SHELBY LYNN         Assistant Professor
    ## 894                    ELSMO,ELIZABETH JANE          Clinical Asst Prof
    ## 895                            ELWERT,FELIX                   Professor
    ## 896                         EMBORG,MARINA E                   Professor
    ## 897                       EMIRBAYER,MUSTAFA                   Professor
    ## 898                          EMSHWILLER,EVE         Associate Professor
    ## 899                        ENDELMAN,JEFFREY         Associate Professor
    ## 900                          ENDERLE,GORDON           Faculty Associate
    ## 901                    ENDICOTT,SARAH ELISA          Clinical Professor
    ## 902                  ENDRES,MATTHEW CHARLES           Faculty Associate
    ## 903                           ENGEL,CHARLES                   Professor
    ## 904                      ENGELMAN,CORINNE D                   Professor
    ## 905                         ENGELMAN,MICHAL         Associate Professor
    ## 906                      ENGIN,FEYZA SONIYE         Assistant Professor
    ## 907                          ENGLAND,SAMUEL         Associate Professor
    ## 908                        ENGLE,JONATHAN W         Assistant Professor
    ## 909                               ENKE,FINN                   Professor
    ## 910                       ENRIGHT,ROBERT D.                   Professor
    ## 911                         ENRIQUEZ,FALINA         Assistant Professor
    ## 912                             ENSOR,SARAH         Assistant Professor
    ## 913                              ENSTAD,NAN                   Professor
    ## 914                          EOM,CHANG-BEOM                   Professor
    ## 915                               EPP,AMBER         Associate Professor
    ## 916                             EPP,RUSSELL             Senior Lecturer
    ## 917                            EPPLI,MARK J           Faculty Associate
    ## 918                            ERAKER,BJORN                   Professor
    ## 919                       ERBIL ERKAN,NALAN          Asst Faculty Assoc
    ## 920                      ERIKSSON,MARK ALAN                   Professor
    ## 921                            ERITEN,MELIH         Associate Professor
    ## 922                           ERKER,TEDWARD          Asst Faculty Assoc
    ## 923                         ERLANGER,HOWARD                   Professor
    ## 924                           ERMAKOFF,IVAN                   Professor
    ## 925                          ERMAN,DANIEL M         Associate Professor
    ## 926                              ERSIG,ANNE         Assistant Professor
    ## 927                    ESCHENFELDER,KRISTIN                   Professor
    ## 928                     ESCOTT-STUMP,SYLVIA         Assoc Faculty Assoc
    ## 929                            ESKOLA,LIANA          Clinical Asst Prof
    ## 930                     ESSELMAN,BRIAN JOHN           Faculty Associate
    ## 931                              ETZEL,MARK                   Professor
    ## 932                              EUDEY,GWEN             Senior Lecturer
    ## 933                        EVANS,DAVID TODD                   Professor
    ## 934                             EVANS,HEIDI           Faculty Associate
    ## 935                           EVANS,PAUL G.                   Professor
    ## 936                     EVANS-ROMAINE,KAREN                   Professor
    ## 937                   EVENSEN,ANN ELIZABETH             Professor (Chs)
    ## 938                          EVERETT,LISA L                   Professor
    ## 939                         FABRY,ZSUZSANNA                   Professor
    ## 940                            FAHL,WILLIAM                   Professor
    ## 941                      FAHY,JENNIFER LYNN                    Lecturer
    ## 942                     FAIN,SEAN BEDILLION                   Professor
    ## 943                      FALK,KATHLEEN MARY           Faculty Associate
    ## 944                     FALK,MICHAEL EDWARD           Adjunct Professor
    ## 945                       FAMAKIN,BOLANLE M         Assistant Professor
    ## 946                                FAN,JING         Assistant Professor
    ## 947                             FAN,SHUXING         Assistant Professor
    ## 948                            FANG,HANLONG          Visiting Asst Prof
    ## 949                                 FANG,KE         Assistant Professor
    ## 950                          FARHAT,WALID A             Professor (Chs)
    ## 951                          FAUST,JENNIFER                    Lecturer
    ## 952                            FAWAZ,KASSEM         Assistant Professor
    ## 953                             FAWAZ,RAMZI         Associate Professor
    ## 954                          FEDENIA,LAUREN                    Lecturer
    ## 955                         FEDENIA,MARK A.         Associate Professor
    ## 956                              FEIGL,KURT                   Professor
    ## 957                    FEINSTEIN,NOAH WEETH         Associate Professor
    ## 958                         FELDMAN,MIKHAIL                   Professor
    ## 959                    FELDSTEIN,DAVID ALAN             Professor (Chs)
    ## 960                        FELTON,ELIZABETH        Asst Professor (Chs)
    ## 961                              FENG,DAWEI         Assistant Professor
    ## 962                                FENG,IVY         Assistant Professor
    ## 963             FERGUSON,JEANNE MARIE BYRON                    Lecturer
    ## 964                      FERNANDES,EARLENCE         Assistant Professor
    ## 965                         FERNANDEZ,DONNA                   Professor
    ## 966                         FERRARETTO,LUIZ         Assistant Professor
    ## 967                        FERREE,MYRA MARX       Honorary Assoc/Fellow
    ## 968              FERREIRA,TATIANA HENRIQUES          Clinical Asst Prof
    ## 969                             FERRIER,KEN         Assistant Professor
    ## 970                          FERRIS,MICHAEL                   Professor
    ## 971              FIEGEL-NEWLON,JENNIFER ANN         Clinical Assoc Prof
    ## 972                             FIELD,AMBER              Assoc Lecturer
    ## 973                        FIELDER,BRIGITTE         Associate Professor
    ## 974                             FIELDS,BETH         Assistant Professor
    ## 975                            FIELDS,DAVID          Asst Faculty Assoc
    ## 976                           FINDLEY,KEITH                   Professor
    ## 977                   FINLEY,KATHRYN BELLIS          Clinical Asst Prof
    ## 978                            FINNEY,MISHA         Assoc Faculty Assoc
    ## 979                        FIORENZA,MARY E.           Faculty Associate
    ## 980                        FISCHER,COLLETTE                    Lecturer
    ## 981                           FISCHER,ISMOR             Senior Lecturer
    ## 982                          FISCHER,MARTHA                   Professor
    ## 983                            FISH,JEFFREY         Clinical Instructor
    ## 984                    FISHER,MADELINE MARY           Faculty Associate
    ## 985                         FISHLER,THERESA          Asst Faculty Assoc
    ## 986                 FITZPATRICK,MEGAN BURKE        Asst Professor (Chs)
    ## 987                        FITZSIMONS,SARAH         Assistant Professor
    ## 988                      FLANAGAN,CONSTANCE                   Professor
    ## 989                   FLANARY,PETER WILLIAM                    Lecturer
    ## 990                          FLETCHER,EMILY         Associate Professor
    ## 991                        FLETCHER,JASON M                   Professor
    ## 992                              FLUGA,ERIC           Adjunct Asst Prof
    ## 993                  FLYNN,MAXFIELD PATRICK        Asst Professor (Chs)
    ## 994                            FOLTZ,JEREMY                   Professor
    ## 995                      FONCK,RAYMOND JOHN              Professor Emer
    ## 996                   FONDOW,STEVEN RICHARD         Assoc Faculty Assoc
    ## 997                        FORD II,JAMES H.         Assistant Professor
    ## 998                             FOREST,CARY                   Professor
    ## 999                       FOREST,KATRINA T.                   Professor
    ## 1000                        FORREST,LISA J.                   Professor
    ## 1001                 FORSTER BENEDICT,STACY           Faculty Associate
    ## 1002                            FOST,NORMAN              Professor Emer
    ## 1003                       FOWLER,AMY MARIE         Assistant Professor
    ## 1004                         FOWLER,CYNTHIA                   Professor
    ## 1005                         FOX,ASHBY KENT              Assoc Lecturer
    ## 1006                           FOX,BRIAN G.                   Professor
    ## 1007                        FOX,CATHERINE A                   Professor
    ## 1008                            FOYS,MARTIN                   Professor
    ## 1009                   FRANCETIC LEPE,LINDA           Faculty Associate
    ## 1010                FRANCHINO,DAVID CHARLES           Adjunct Asst Prof
    ## 1011                   FRANCIS,DAVID OLIVER         Associate Professor
    ## 1012                       FRANCK,CHRISTIAN         Associate Professor
    ## 1013                        FRANCK,JENNIFER         Assistant Professor
    ## 1014                          FRANCOIS,MARY          Clinical Asst Prof
    ## 1015                        FRANK,CHRISTINA                    Lecturer
    ## 1016                            FRANK,HEIDI         Assoc Faculty Assoc
    ## 1017                         FRANK,VICTORIA              Assoc Lecturer
    ## 1018                             FRANTZ,EVA         Clinical Instructor
    ## 1019                           FRATTA,DANTE         Associate Professor
    ## 1020                        FREDETTE,STEVEN         Assoc Faculty Assoc
    ## 1021                   FREDRICKSON,DANIEL C                   Professor
    ## 1022                           FREEDMAN,ZAC         Assistant Professor
    ## 1023                      FREELAND,ROBERT F                   Professor
    ## 1024                          FREEMAN,KATIE          Asst Faculty Assoc
    ## 1025                          FREID,MATTHEW                    Lecturer
    ## 1026                            FRICKE,PAUL                   Professor
    ## 1027                        FRIEDLAND,LEWIS                   Professor
    ## 1028                    FRIEDMAN,JAMES ALAN          Adjunct Instructor
    ## 1029                    FRIEDMAN,MATTHEW L.              Assoc Lecturer
    ## 1030                         FRIEDMAN,SUSAN                   Professor
    ## 1031                       FRIEDRICH,THOMAS                   Professor
    ## 1032                   FRIEDRICHS,KRISTEN R         Clinical Assoc Prof
    ## 1033                      FRIESEN,PAUL DEAN                   Professor
    ## 1034                  FRITSCH,MICHAEL KEVIN             Professor (Chs)
    ## 1035                  FROST,NICKOLAS DELMAR         Assistant Professor
    ## 1036                                FU,CHAO                   Professor
    ## 1037                              FU,SHUBIN          Visiting Asst Prof
    ## 1038                      FUHREMANN,KRISTEN           Faculty Associate
    ## 1039                          FUJIMURA,JOAN                   Professor
    ## 1040                           FULMER,MIMMI                   Professor
    ## 1041                           FULTON,SCOTT           Adjunct Professor
    ## 1042                            FUNK,LUKE M         Associate Professor
    ## 1043                          FURLONG,SCOTT              Assoc Lecturer
    ## 1044                         FURUMOTO,DAVID                   Professor
    ## 1045                           GABAI,JOSHUA              Assoc Lecturer
    ## 1046                            GABER,ALICE              Assoc Lecturer
    ## 1047                        GADDIS,JENNIFER         Assistant Professor
    ## 1048                     GADE,ANNA MARGARET                   Professor
    ## 1049                         GAERTNER,FABIO         Associate Professor
    ## 1050                       GAJESKI,SHARON K           Faculty Associate
    ## 1051                       GALIPEAU,JACQUES                   Professor
    ## 1052                  GALLAGHER,CATHERINE L             Professor (Chs)
    ## 1053                        GALLIMORE,CASEY       Assoc Professor (Chs)
    ## 1054                     GALLIMORE,JONATHAN             Senior Lecturer
    ## 1055                        GALMOZZI,ANDREA         Assistant Professor
    ## 1056                         GALVAO,LOREN W           Faculty Associate
    ## 1057                             GAMM,DAVID                   Professor
    ## 1058                      GAMMIE,STEPHEN C.                   Professor
    ## 1059                           GANCO,MARTIN         Associate Professor
    ## 1060                    GANGL,AMY ELIZABETH         Assoc Faculty Assoc
    ## 1061                            GANGNON,RON                   Professor
    ## 1062                        GANZ,OLGA RADKO         Assoc Faculty Assoc
    ## 1063                               GAO,SONG         Assistant Professor
    ## 1064                         GARAND,ETIENNE         Associate Professor
    ## 1065                           GARBACZ,ANDY         Associate Professor
    ## 1066                 GARCIA TRILLOS,NICOLAS         Assistant Professor
    ## 1067                       GARCIA,ALEXANDRA              Assoc Lecturer
    ## 1068                           GARCIA,DENIA         Assistant Professor
    ## 1069                            GAROON,JOSH         Assistant Professor
    ## 1070                      GARTLAND,SHARON G          Clinical Professor
    ## 1071                        GARTNER,WILLIAM             Senior Lecturer
    ## 1072                        GASCH,AUDREY P.                   Professor
    ## 1073                           GASPER,DAVID          Clinical Asst Prof
    ## 1074               GATHMAN,CABELL HANKINSON                    Lecturer
    ## 1075                        GATTENBY,TIM G.       Dis Faculty Associate
    ## 1076                      GAUDREAU,JOSEPH B               Professor L/I
    ## 1077                           GAVINS,JAMES                    Lecturer
    ## 1078                                GE,YING                   Professor
    ## 1079                            GEBBIE,MATT         Assistant Professor
    ## 1080                        GEIGER,BENEDIKT         Assistant Professor
    ## 1081                      GELLMAN,SAMUEL H.                   Professor
    ## 1082                   GENNERMAN,REBECCA JO         Clinical Instructor
    ## 1083                            GENSKOW,KEN                   Professor
    ## 1084                             GEORGE,MAY                    Lecturer
    ## 1085                   GEORGIADES,ARISTOTLE                   Professor
    ## 1086                            GERA,PRERNA          Visiting Asst Prof
    ## 1087                GERARD,HEATHER STEPHANY           Adjunct Professor
    ## 1088                           GERASSI,LARA         Assistant Professor
    ## 1089                     GERBER,THEODORE P.                   Professor
    ## 1090                          GERHART,BARRY                   Professor
    ## 1091                          GERN,JAMES E.                   Professor
    ## 1092                 GERNSBACHER,MORTON ANN                   Professor
    ## 1093                     GEVENS,AMANDA JANE                   Professor
    ## 1094                            GEYER,NAOMI         Associate Professor
    ## 1095                           GHANDHI,JAAL                   Professor
    ## 1096                        GHOUSSEINI,HALA         Associate Professor
    ## 1097                    GIBBS,HOLLY KRISTEN         Associate Professor
    ## 1098                          GIBSON,MARTHA           Faculty Associate
    ## 1099                      GICQUELAIS,RACHEL         Assistant Professor
    ## 1100                            GIDAL,BARRY             Professor (Chs)
    ## 1101                        GILBERT,LEWIS E             Senior Lecturer
    ## 1102                           GILBERT,PUPA                   Professor
    ## 1103                    GILLETT,JOHN ROBERT             Senior Lecturer
    ## 1104                       GILLIAN,ANNELYNN           Faculty Associate
    ## 1105                           GILLIE,NAZAN                    Lecturer
    ## 1106                 GILLIS,COLIN RADCLIFFE                    Lecturer
    ## 1107                       GILMORE,JANET C.       Honorary Assoc/Fellow
    ## 1108                           GILROY,SIMON                   Professor
    ## 1109                   GINDER-VOGEL,MATTHEW         Associate Professor
    ## 1110                      GIOIA,CHRISTOPHER         Clinical Assoc Prof
    ## 1111           GIOVANNELLI CAPUTO,CHRISTINA              Assoc Lecturer
    ## 1112                        GIPSON,JENNIFER         Assistant Professor
    ## 1113                         GITTER,ANTHONY         Assistant Professor
    ## 1114                      GIVNISH,THOMAS J.                   Professor
    ## 1115                     GLADSTONE,BRUCE E.             Senior Lecturer
    ## 1116                          GLASPIE,JODIE          Asst Faculty Assoc
    ## 1117                     GLAWTSCHEW,REBECCA                    Lecturer
    ## 1118                         GLAZER,JEFFREY         Clinical Assoc Prof
    ## 1119                       GLEICHER,MICHAEL                   Professor
    ## 1120                         GLINBERG,LANNY          Clinical Asst Prof
    ## 1121                      GLINSMANN,BETHANY         Assoc Faculty Assoc
    ## 1122                      GLORIA,ALBERTA M.                   Professor
    ## 1123                          GLOTZER,PAIGE         Assistant Professor
    ## 1124                       GLOWACKI,GULNARA             Senior Lecturer
    ## 1125                         GLUKHOV,ALEXEY         Assistant Professor
    ## 1126                         GOCMEN,ASLIGUL         Associate Professor
    ## 1127                         GODFREY,BROOKE          Asst Faculty Assoc
    ## 1128               GOETZINGER,MATTHEW JAMES                    Lecturer
    ## 1129                             GOFF,PETER         Assistant Professor
    ## 1130                             GOH,JUN LE          Visiting Asst Prof
    ## 1131                            GOLAB,HANNA              Assoc Lecturer
    ## 1132                     GOLDBERG,CHAD ALAN                   Professor
    ## 1133                         GOLDBERG,SIMON         Assistant Professor
    ## 1134                          GOLDBERG,TONY                   Professor
    ## 1135                     GOLDBERGER,ZACHARY       Assoc Professor (Chs)
    ## 1136                        GOLDEN,JENNIFER         Assistant Professor
    ## 1137                GOLDGEL-CARBALLO,VICTOR         Associate Professor
    ## 1138                          GOLDMAN,IRWIN                   Professor
    ## 1139                         GOLDSMITH,HILL                   Professor
    ## 1140                    GOLDSMITH,RANDALL H         Associate Professor
    ## 1141               GOLDSTEIN,RUTH ELIZABETH         Assistant Professor
    ## 1142                      GOLOS,THADDEUS G.                   Professor
    ## 1143                      GOMEZ,MARY LOUISE                   Professor
    ## 1144                            GOMEZ,PABLO         Associate Professor
    ## 1145                        GOMEZ,TIMOTHY M                   Professor
    ## 1146                            GONDI,VINAI  Clinical Adjunct Asst Prof
    ## 1147                     GONG,SHAOQIN SARAH                   Professor
    ## 1148                         GONG,XIANGHONG                   Professor
    ## 1149                     GONZALEZ,ALEXANDER          Asst Faculty Assoc
    ## 1150                           GOOD,ANNALEE                    Lecturer
    ## 1151                    GOODING,DIANE CAROL                   Professor
    ## 1152                        GOODKIN,RICHARD                   Professor
    ## 1153                       GOODWIN,LAUREL B                   Professor
    ## 1154                          GOPALAN,PADMA                   Professor
    ## 1155                            GORIN,VADIM         Associate Professor
    ## 1156                       GOSBEE,ALYSSA L.                    Lecturer
    ## 1157                         GOTTLIEB,PAULA                   Professor
    ## 1158                 GOTTWALD,JENNIFER ROSE           Adjunct Professor
    ## 1159                         GOURSE,RICHARD                   Professor
    ## 1160                         GRABOIS,DANIEL         Associate Professor
    ## 1161                           GRAEFE,GOETZ       Honorary Assoc/Fellow
    ## 1162                           GRAHAM,LINDA                   Professor
    ## 1163                            GRAHAM,MIKE                   Professor
    ## 1164                       GRAHAM,STEPHANIE          Clinical Professor
    ## 1165                       GRAINGER,CORBETT         Associate Professor
    ## 1166                        GRALNICK,LISA B                   Professor
    ## 1167                  GRANDE,KATARINA MARIA                    Lecturer
    ## 1168                         GRANICK,MARTIN         Clinical Instructor
    ## 1169                             GRANT,CARL                   Professor
    ## 1170                         GRANT,MONICA J         Associate Professor
    ## 1171                             GRANT,PAUL                    Lecturer
    ## 1172                          GRANT,TIMOTHY         Assistant Professor
    ## 1173                        GRATTON,CLAUDIO                   Professor
    ## 1174                             GRAUE,BETH                   Professor
    ## 1175                           GRAVES,LUCAS         Associate Professor
    ## 1176                           GRAVES,SARAH                    Lecturer
    ## 1177                          GRAY,JONATHAN                   Professor
    ## 1178                              GRECO,JIM           Faculty Associate
    ## 1179                         GREEN,C. SHAWN         Associate Professor
    ## 1180                    GREEN,CHELSEY MARIE              Assoc Lecturer
    ## 1181                 GREEN,TIFFANY LORRAINE         Assistant Professor
    ## 1182                       GREENBERG,ANDREW       Dis Faculty Associate
    ## 1183                       GREENE,CHRISTINA                   Professor
    ## 1184                           GREENE,LINDA                   Professor
    ## 1185                GREENE,MADELYNE ZUEHLKE         Assistant Professor
    ## 1186                  GREENWALD,MERCY MAXAN          Asst Faculty Assoc
    ## 1187                       GREENWOOD,PHILIP             Senior Lecturer
    ## 1188                   GREGORY,JESSE MCCUNE         Associate Professor
    ## 1189                             GREIG,TONY             Senior Lecturer
    ## 1190                   GRIEP,ANNE ELIZABETH                   Professor
    ## 1191                         GRIFFITH,EMILY         Associate Professor
    ## 1192                          GRIFFITH,MATT                    Lecturer
    ## 1193                            GRIMM,GERIT         Associate Professor
    ## 1194                      GRINBLAT,YEVGENYA         Associate Professor
    ## 1195                        GRIZZARD,ROBERT           Faculty Associate
    ## 1196                            GROB,RACHEL          Clinical Professor
    ## 1197                         GROBLEWSKI,GUY                   Professor
    ## 1198                           GRODSKY,ERIC                   Professor
    ## 1199                          GROSS,DOMINIC         Assistant Professor
    ## 1200                     GROSS,JOHN PATRICK         Clinical Assoc Prof
    ## 1201                    GROSS,KELSEY NICOLE          Asst Faculty Assoc
    ## 1202                           GROSS,SABINE                   Professor
    ## 1203                    GROSSENBACHER,LAURA           Faculty Associate
    ## 1204                         GROVES,RUSSELL                   Professor
    ## 1205                            GRUBEN,KREG                   Professor
    ## 1206                        GRUNEWALD,RALPH         Assistant Professor
    ## 1207                         GUBNER,JOHN A.                   Professor
    ## 1208                      GUEDOT,CHRISTELLE         Associate Professor
    ## 1209                     GUILLIAMS,THOMAS G          Adjunct Assoc Prof
    ## 1210                    GULLICKSON,MICHELLE                    Lecturer
    ## 1211                          GUMPERZ,JENNY                   Professor
    ## 1212                   GUNASEKARAN,SUNDARAM                   Professor
    ## 1213                          GUNNESON,ERIK           Faculty Associate
    ## 1214                           GUO,SHAOMING         Assistant Professor
    ## 1215                                GUO,WEI         Assistant Professor
    ## 1216                            GUO,XIAOQIN          Visiting Asst Prof
    ## 1217                            GUPTA,MOHIT         Assistant Professor
    ## 1218                           GUPTE,SACHIN         Clinical Instructor
    ## 1219                       GUREVICH,SHAMGAR         Associate Professor
    ## 1220                          GURNEE,KENDRA              Assoc Lecturer
    ## 1221                GUSSICK,MEGAN ELIZABETH          Clinical Asst Prof
    ## 1222                             GUSTIN,LEA         Assoc Faculty Assoc
    ## 1223                 GUTIERREZ CHACON,LUCIA         Associate Professor
    ## 1224                             GUYER,SARA                   Professor
    ## 1225                       HA,MELISSA ELLEN         Clinical Instructor
    ## 1226                         HAAS,CHRISTINE                    Lecturer
    ## 1227                              HAAS,NATE              Assoc Lecturer
    ## 1228                              HAAS,RUSS           Faculty Associate
    ## 1229                      HABECK,KODY LOUIS        Asst Instrmt Inn/Ins
    ## 1230                       HABERKORN,TYRELL                   Professor
    ## 1231                      HADEN,CLARE ARENA                    Lecturer
    ## 1232                       HADLEY,DOUGLAS B             Senior Lecturer
    ## 1233                        HAFEZ,GHOLAM R.             Professor (Chs)
    ## 1234                    HAGER,DAVID RICHARD          Clinical Asst Prof
    ## 1235                  HAGERICH,KIMBERLY ANN             Senior Lecturer
    ## 1236                   HAGERMOSER,ELIZABETH          Clinical Asst Prof
    ## 1237                          HAGNESS,SUSAN                   Professor
    ## 1238                     HAHN,ERIN MARGARET          Adjunct Instructor
    ## 1239                              HAI,AVIAD         Assistant Professor
    ## 1240                   HAIRSTON,MARK STEVEN         Assistant Professor
    ## 1241                       HALBACH,THEODORE         Assoc Faculty Assoc
    ## 1242                           HALBERG,RICH         Associate Professor
    ## 1243                             HALL,APRIL           Adjunct Asst Prof
    ## 1244                          HALL,DEANNE J          Adjunct Instructor
    ## 1245                             HALL,EMILY       Dis Faculty Associate
    ## 1246                              HALL,JOHN         Associate Professor
    ## 1247                       HALL,TIMOTHY JON                   Professor
    ## 1248                 HALLISY,KRISTINE MARIE       Assoc Professor (Chs)
    ## 1249                          HALLORAN,MARY                   Professor
    ## 1250                             HALM,WENDY         Clinical Assoc Prof
    ## 1251                   HALPERN-MEEKIN,SARAH         Associate Professor
    ## 1252                    HALVERSON,ALAN DALE          Adjunct Assoc Prof
    ## 1253                        HALVERSON,ERICA                   Professor
    ## 1254                HALVERSON,RICHARD ROGER                   Professor
    ## 1255                      HALZEN,FRANCIS L.                   Professor
    ## 1256                     HAMERS,ROBERT JOHN                   Professor
    ## 1257                     HAMPTON,JESSE CLAY         Assistant Professor
    ## 1258                  HAMPTON,JOHN MITCHELL                  Researcher
    ## 1259                                 HAN,LU                   Professor
    ## 1260                    HANDELSMAN,JO EMILY                   Professor
    ## 1261                      HANHART,ALEXANDER         Assoc Faculty Assoc
    ## 1262                            HANNA,AMGAD             Professor (Chs)
    ## 1263                             HANNA,AWAD                   Professor
    ## 1264                   HANNON,JENNIFER ANNE          Adjunct Instructor
    ## 1265                            HANSEN,ANNE                   Professor
    ## 1266                        HANSEN,BRUCE E.                   Professor
    ## 1267                           HANSEN,DAVID                    Lecturer
    ## 1268                 HANSEN,KAREN ELIZABETH                   Professor
    ## 1269                       HANSEN,KORINNA K             Senior Lecturer
    ## 1270                  HANSON BRENNER,GAIL M           Faculty Associate
    ## 1271                          HANSON,KAEL D                   Professor
    ## 1272                          HANSON,LANE L              Assoc Lecturer
    ## 1273                     HANSON,PAUL CONRAD                    Lecturer
    ## 1274                         HANUKAI,MAKSIM         Assistant Professor
    ## 1275                    HARACKIEWICZ,JUDITH                   Professor
    ## 1276                       HARDIE,ROBERT J.          Clinical Professor
    ## 1277                            HARDIN,JEFF                   Professor
    ## 1278                        HARER,MATTHEW W        Asst Professor (Chs)
    ## 1279                              HARK,MARY                   Professor
    ## 1280                    HAROLDSON,AMBER RAE         Assoc Faculty Assoc
    ## 1281                      HARRILL,STEPHANIE                    Lecturer
    ## 1282                        HARRINGTON,GREG                   Professor
    ## 1283                   HARRINGTON,JOHN ALAN                   Professor
    ## 1284                          HARRIS,ANDREA         Associate Professor
    ## 1285                        HARRIS,MICHELLE       Dis Faculty Associate
    ## 1286                          HARRIS,RONALD       Dis Faculty Associate
    ## 1287                       HARRISON,MELISSA         Associate Professor
    ## 1288                             HART,SARAH         Assistant Professor
    ## 1289                      HARTEL,RICHARD W.                   Professor
    ## 1290                       HARTEMINK,ALFRED                   Professor
    ## 1291                       HARTENBACH,ELLEN                   Professor
    ## 1292                HARTER,JOSEPHINE MIRIAM       Assoc Professor (Chs)
    ## 1293                          HARTLEY,SIGAN         Associate Professor
    ## 1294                            HARTMAN,AMY          Clinical Professor
    ## 1295                           HARTMAN,JEFF        Asst Professor (Chs)
    ## 1296                   HARTMAN,SCOTT AUSTIN          Asst Faculty Assoc
    ## 1297                    HARTUP,BARRY KINNEY         Clinical Instructor
    ## 1298                        HARVEY,MELODY A         Assistant Professor
    ## 1299                          HASHIMOTO,AKI                   Professor
    ## 1300                        HASSETT,DAWNENE                   Professor
    ## 1301                             HASTI,BECK           Faculty Associate
    ## 1302                      HASTINGS,PATRICIA       Dis Faculty Associate
    ## 1303                   HATLAN-ATWELL,HANNAH       Student Services Cord
    ## 1304                         HATZEL,JEFFREY                    Lecturer
    ## 1305                             HAUSCH,DON                   Professor
    ## 1306                          HAVEY,MICHAEL       Honorary Assoc/Fellow
    ## 1307                       HAWKINS,MARGARET                   Professor
    ## 1308                         HAWKINS,SHAWNA         Clinical Instructor
    ## 1309                             HAWKS,JOHN                   Professor
    ## 1310                         HAWLEY,DONNA J           Faculty Associate
    ## 1311                           HAWLEY,HELEN                    Lecturer
    ## 1312                           HAYATI,FAZEL                    Lecturer
    ## 1313                         HAYES,MORGAN M              Assoc Lecturer
    ## 1314           HAYNES MANOGUE,JONANNE MARIE                    Lecturer
    ## 1315                           HAYNES,APRIL         Associate Professor
    ## 1316                            HAYNEY,MARY             Professor (Chs)
    ## 1317                   HAYS,REBECCA ELEANOR              Assoc Lecturer
    ## 1318                           HAZEN,ALICIA                    Lecturer
    ## 1319                               HE,CHENG         Assistant Professor
    ## 1320                       HEALLESS,LINDSAY         Clinical Instructor
    ## 1321                         HEATON,CAITLIN         Clinical Instructor
    ## 1322                         HEFFNER,THOMAS             Senior Lecturer
    ## 1323                            HEGNA,CHRIS                   Professor
    ## 1324                            HEIDE,JAN B                   Professor
    ## 1325                      HEIDE,MARIA PAPAS             Senior Lecturer
    ## 1326                        HEIDEMAN,BRENDA              Assoc Lecturer
    ## 1327                     HEIDERSCHEIT,BRYAN                   Professor
    ## 1328                        HEIMERL,FLORIAN          Asst Faculty Assoc
    ## 1329                          HEIMKE,JEREMY        Asst Prof Of Mil Sci
    ## 1330                 HEINER,ELIZABETH ALLEN          Adjunct Instructor
    ## 1331                          HEINTZ,CLAUDE           Faculty Associate
    ## 1332                        HEINZ,SEBASTIAN                   Professor
    ## 1333                     HELD,PATRICE KARYN       Assoc Professor (Chs)
    ## 1334                         HEMATTI,PEIMAN                   Professor
    ## 1335                          HENAK,CORINNE         Assistant Professor
    ## 1336                     HENDERSON,DOUGLASS                   Professor
    ## 1337                 HENDERSON,MEGHAN MARIE              Assoc Lecturer
    ## 1338                     HENDERSON,SHERYL L       Assoc Professor (Chs)
    ## 1339                  HENDERSON,STEPHANIE A         Assistant Professor
    ## 1340                    HENDERSON,TY THOMAS         Visiting Assoc Prof
    ## 1341                        HENDLEY,KATHRYN                   Professor
    ## 1342                      HENDRICKS,KENNETH                   Professor
    ## 1343                            HENKE,JAMIE       Dis Faculty Associate
    ## 1344                             HENKE,RYAN         Assistant Professor
    ## 1345                     HENNESSY,ELIZABETH         Associate Professor
    ## 1346            HENNING,REBECCA LYNN WARNER          Clinical Asst Prof
    ## 1347                      HENRICHS,RACHEL M           Faculty Associate
    ## 1348                         HENRIQUES,JEFF                Dis Lecturer
    ## 1349                         HENRY,TRAVIS J           Adjunct Asst Prof
    ## 1350                   HENZLER,KATHERINE A.         Associate Professor
    ## 1351                           HEPLER,BRIAN          Visiting Asst Prof
    ## 1352                                 HER,PA          Clinical Asst Prof
    ## 1353                           HERMANN,MATT         Assoc Faculty Assoc
    ## 1354                            HERMANS,IVE                   Professor
    ## 1355                      HERNANDEZ,ANTONIO         Assoc Faculty Assoc
    ## 1356                        HERNANDEZ,LAURA         Associate Professor
    ## 1357                        HERNANDEZ,PAOLA                   Professor
    ## 1358                      HERNANDEZ,REINIER         Assistant Professor
    ## 1359                         HERNANDO,DIEGO         Assistant Professor
    ## 1360                      HERNDON,MATTHEW F                   Professor
    ## 1361                      HERNKE,MICHAEL T.                    Lecturer
    ## 1362                    HERRERA,KYLE JORDAN                    Lecturer
    ## 1363                        HERRERA,YOSHIKO                   Professor
    ## 1364                          HERRINGA,RYAN         Associate Professor
    ## 1365                 HERSHBERGER,KAREN LYNN                    Lecturer
    ## 1366                        HERSHEY,DAVID M         Assistant Professor
    ## 1367                           HERZOG,EMILY         Clinical Instructor
    ## 1368                    HERZOG,MELANIE ANNE             Senior Lecturer
    ## 1369                             HESS,ERICA              Assoc Lecturer
    ## 1370                             HESS,JAMIE       Assoc Professor (Chs)
    ## 1371                           HETZLER,MARK                   Professor
    ## 1372                        HEYMANN,ELISA R             Senior Lecturer
    ## 1373                           HICKS,ANDREA         Assistant Professor
    ## 1374                          HIEBING,LAURA              Assoc Lecturer
    ## 1375                          HIGBY,GREGORY             Senior Lecturer
    ## 1376                       HILDNER,DAVID J.                   Professor
    ## 1377                             HILL,BETSI           Faculty Associate
    ## 1378                            HILL,JOEL R          Clinical Asst Prof
    ## 1379                        HILL,NICHOLAS J           Faculty Associate
    ## 1380                          HILL,PFANIQUE                    Lecturer
    ## 1381                       HILLMAN,NICHOLAS         Associate Professor
    ## 1382                  HILLS-MEYER,PATRICK R              Assoc Lecturer
    ## 1383                  HILTNER,AARON MICHAEL          Asst Faculty Assoc
    ## 1384                        HILYARD,STEPHEN                   Professor
    ## 1385                       HINKEL,NICHOLE L         Clinical Instructor
    ## 1386              HINRICHS,NILE CHRISTOPHER             Senior Lecturer
    ## 1387                        HIRSCH,FRANCINE                   Professor
    ## 1388                         HITCHCOCK,JOHN                   Professor
    ## 1389                    HITCHMAN,MATTHEW H.                   Professor
    ## 1390                     HITCHON,WILLIAM N.                   Professor
    ## 1391                           HITE,JESSICA         Assistant Professor
    ## 1392                   HITTINGER,CHRIS TODD         Associate Professor
    ## 1393                   HO,BENJAMIN MING-TAO          Clinical Asst Prof
    ## 1394                            HO,LI-CHING         Associate Professor
    ## 1395                                HO,LISA         Assoc Faculty Assoc
    ## 1396                             HOAG,KEVIN         Assoc Faculty Assoc
    ## 1397                          HOBAN,PAUL R.         Assistant Professor
    ## 1398                           HOCH,JOHN R.                   Professor
    ## 1399                         HOEFFERLE,MARY         Assoc Faculty Assoc
    ## 1400                        HOFACKER,EMILIE        Dir, Unspecified (8)
    ## 1401                     HOFF,LAURA HEATHER        Asst Professor (Chs)
    ## 1402                          HOFFELD,ERIKA         Clinical Instructor
    ## 1403                    HOFFMAN,ERIC JOSEPH         Assoc Faculty Assoc
    ## 1404             HOFFMEISTER,MICHAEL ROBERT          Asst Faculty Assoc
    ## 1405                       HOFSTETTER,HEIKE           Faculty Associate
    ## 1406                     HOFTYZER,MELANIE K             Senior Lecturer
    ## 1407                        HOLDEN,HAZEL M.                   Professor
    ## 1408                          HOLLAND,DUANE         Assistant Professor
    ## 1409                         HOLLAND,LESLIE         Assistant Professor
    ## 1410                        HOLLOWAY,TRACEY                   Professor
    ## 1411                           HOLMAN,SARAH         Clinical Instructor
    ## 1412                     HOLSCHBACH,CHELSEA         Clinical Instructor
    ## 1413             HOLSCHUH-HOUDEN,DEB HOUDEN          Adjunct Instructor
    ## 1414                HOLT III,JOSEPH PAYNTER         Clinical Assoc Prof
    ## 1415                          HONG,SEUNGPYO                   Professor
    ## 1416                        HONORE,FLORENCE         Assistant Professor
    ## 1417                              HOOD,SEAN              Assoc Lecturer
    ## 1418                          HOOKER,PAUL D             Senior Lecturer
    ## 1419                         HOON,MRINALINI         Assistant Professor
    ## 1420                  HOOPER-LANE,ELIZABETH             Senior Lecturer
    ## 1421                   HORA,MATTHEW TADASHI         Assistant Professor
    ## 1422                        HORNBERGER,TROY                   Professor
    ## 1423                    HORNER,VANESSA LYNN        Asst Professor (Chs)
    ## 1424                        HOROWITZ,LEAH S         Assistant Professor
    ## 1425                          HOSKINS,AARON         Associate Professor
    ## 1426                         HOTCHKISS,SARA                   Professor
    ## 1427                           HOUCK,JUDITH                   Professor
    ## 1428                    HOUDE,JEAN-FRANCOIS         Associate Professor
    ## 1429                        HOWARD,ROBERT G                   Professor
    ## 1430                              HOWE,MIKE              Assoc Lecturer
    ## 1431                          HOWE,MORGAN E              Assoc Lecturer
    ## 1432                     HOWELL,EVELYN ANNE                   Professor
    ## 1433                              HOYT,ERIC         Associate Professor
    ## 1434                           HOYT,WILLIAM                   Professor
    ## 1435                      HRYCKOWIAN,ANDREW         Assistant Professor
    ## 1436                HSIA,FLORENCE CHARLOTTE                   Professor
    ## 1437                              HSU,DAVID             Professor (Chs)
    ## 1438                             HSU,JUSTIN         Assistant Professor
    ## 1439                          HSUNG,RICHARD                   Professor
    ## 1440                             HU,JIAMIAN         Assistant Professor
    ## 1441                             HU,QUANYIN         Assistant Professor
    ## 1442                              HU,YU HEN                   Professor
    ## 1443                           HUANG,JINGYI         Assistant Professor
    ## 1444                         HUANG,KRISTINA         Assistant Professor
    ## 1445                          HUANG,QUNYING         Associate Professor
    ## 1446                          HUANG,SHAOSAI          Visiting Asst Prof
    ## 1447                              HUANG,XIN         Associate Professor
    ## 1448                             HUANG,ZHEN         Associate Professor
    ## 1449                       HUBANKS,TANYA A.                    Lecturer
    ## 1450                      HUBBARD,BREEANA N         Assoc Faculty Assoc
    ## 1451                         HUBBARD,EDWARD         Associate Professor
    ## 1452                           HUBER,GEORGE                   Professor
    ## 1453                          HUDNALL,KATIE         Assistant Professor
    ## 1454                         HUGHES,GWYNETH                    Lecturer
    ## 1455                   HULL,CHRISTINA MARIE                   Professor
    ## 1456                      HUNEEUS,ALEXANDRA                   Professor
    ## 1457                            HUNTER,PAUL       Assoc Professor (Chs)
    ## 1458                       HUNTINGTON,JOY W              Assoc Lecturer
    ## 1459                       HUNTINGTON,RANIA                   Professor
    ## 1460                           HURLEY,JAMES                   Professor
    ## 1461                           HUSTAD,KATIE                   Professor
    ## 1462                        HUTCHINS,B. IAN         Assistant Professor
    ## 1463                      HUTCHINSON,STEVEN                   Professor
    ## 1464                            HUTSON,PAUL             Professor (Chs)
    ## 1465                      HUTTENLOCHER,ANNA                   Professor
    ## 1466                          HUTTON,JEREMY                   Professor
    ## 1467                           HUYNH,JULIET         Assistant Professor
    ## 1468                           HUYNH,TU ANH         Assistant Professor
    ## 1469                             HYDE,JANET                   Professor
    ## 1470                             HYER,BRIAN                   Professor
    ## 1471                         IBARRA,ARMANDO         Associate Professor
    ## 1472                      IBELE,ERIK WARREN          Adjunct Instructor
    ## 1473                           IBER,PATRICK         Associate Professor
    ## 1474                          IFRIM,MIHAELA         Associate Professor
    ## 1475                          IKEDA,AKIHIRO                   Professor
    ## 1476                           IKEDA,SHINYA         Assistant Professor
    ## 1477                            IMHOFF,LISA              Assoc Lecturer
    ## 1478                         INEICHEN,JACOB              Assoc Lecturer
    ## 1479                      INGHAM,BARBARA H.                   Professor
    ## 1480                            INTHALY,SAM           Faculty Associate
    ## 1481                         IPSEN,PERNILLE         Associate Professor
    ## 1482                   IRIBE RAMIREZ,YVETTE              Assoc Lecturer
    ## 1483                      ISENBUEGEL,STELLA             Senior Lecturer
    ## 1484                       ISKANDAR,BERMANS                   Professor
    ## 1485                         IVANOV,MIKHAIL                    Lecturer
    ## 1486                        IVES,ANTHONY R.                   Professor
    ## 1487                             IYER,GOPAL         Assistant Professor
    ## 1488                       JABLONSKY,CLAIRE                    Lecturer
    ## 1489                     JACH,ELIZABETH ANN                    Lecturer
    ## 1490                        JACKA,ELIZABETH                    Lecturer
    ## 1491                          JACKLITZ,JILL         Clinical Instructor
    ## 1492                  JACKSON,JERLANDO F.L.                   Professor
    ## 1493                        JACKSON,MEYER B                   Professor
    ## 1494                          JACKSON,RANDY                   Professor
    ## 1495                          JACKSON,RANDY                    Lecturer
    ## 1496             JACKSON,SHERRELLE PRINCESS          Clinical Asst Prof
    ## 1497                      JACKSON,TARAKEE M         Assoc Faculty Assoc
    ## 1498                  JACOBS,CASANDRA MARIE         Clinical Instructor
    ## 1499                             JACOBS,LEA                   Professor
    ## 1500                         JACOBS,LINDSAY         Assistant Professor
    ## 1501                           JAHNS,THOMAS                   Professor
    ## 1502                       JARJOUR,NIZAR N.                   Professor
    ## 1503                       JARRARD,DAVID F.                   Professor
    ## 1504                         JASPER,CYNTHIA                   Professor
    ## 1505                             JEDD,SARAH           Faculty Associate
    ## 1506                      JEFCOATE,COLIN R.              Professor Emer
    ## 1507                        JEFFERSON,DIANE                    Lecturer
    ## 1508                           JENKINS,GINA                    Lecturer
    ## 1509                  JENNINGS,KARLENE NOEL          Instructional Spec
    ## 1510                       JENSEN,KATHERINE         Assistant Professor
    ## 1511                            JENSEN,OLAF         Associate Professor
    ## 1512                         JEONG,SEUNGGON         Assoc Faculty Assoc
    ## 1513                           JERAJ,ROBERT                   Professor
    ## 1514                             JEW,VICTOR             Senior Lecturer
    ## 1515                             JHA,SOMESH                   Professor
    ## 1516                          JIANG,HONGRUI                   Professor
    ## 1517                             JIANG,JACK                   Professor
    ## 1518                         JIANG,JIAOYANG         Associate Professor
    ## 1519                            JIANG,JIEPU         Assistant Professor
    ## 1520                  JIMENEZ,ROMMEL JAVIER       Student Services Cord
    ## 1521                               JIN,SONG                   Professor
    ## 1522                              JOG,VARUN         Assistant Professor
    ## 1523                           JOHANNES,JIM                   Professor
    ## 1524               JOHANNSEN,ERIC CHRISTIAN         Associate Professor
    ## 1525                     JOHNS,CHRISTY LYNN          Adjunct Instructor
    ## 1526                          JOHNSON,AMAUD                   Professor
    ## 1527                JOHNSON,ARLYNE HEDEMARK           Adjunct Professor
    ## 1528                          JOHNSON,BECKY          Clinical Professor
    ## 1529                    JOHNSON,CHRISTOPHER        Asst Prof Of Mil Sci
    ## 1530                        JOHNSON,DAVID W             Senior Lecturer
    ## 1531                          JOHNSON,DEREK                   Professor
    ## 1532                           JOHNSON,ERIC                   Professor
    ## 1533                        JOHNSON,JEFFREY                   Professor
    ## 1534                         JOHNSON,JENELL         Associate Professor
    ## 1535                        JOHNSON,JESSICA                   Professor
    ## 1536                  JOHNSON,KEVIN MICHAEL         Assistant Professor
    ## 1537                      JOHNSON,LEE HELEN         Assistant Professor
    ## 1538                    JOHNSON,LISA MARVEL         Assoc Faculty Assoc
    ## 1539                           JOHNSON,MARK                    Lecturer
    ## 1540                        JOHNSON,MICHAEL                    Lecturer
    ## 1541                       JOHNSON,MICHELLE           Faculty Associate
    ## 1542                JOHNSON,NATHAN BARRETTE         Assoc Faculty Assoc
    ## 1543                   JOHNSON,PAUL HERBERT                    Lecturer
    ## 1544                        JOHNSON,SHERI P       Assoc Professor (Chs)
    ## 1545                      JOHNSON,STEPHEN M         Associate Professor
    ## 1546                       JOHNSON,STERLING                   Professor
    ## 1547                      JOHNSON,SUSAN LEE                   Professor
    ## 1548                           JOHNSON,TANA         Associate Professor
    ## 1549                         JOHNSTON,SARAH         Assistant Professor
    ## 1550                         JONES,ANNIE M.                   Professor
    ## 1551                            JONES,DANNY                    Lecturer
    ## 1552                       JONES,HALLEY ANN              Assoc Lecturer
    ## 1553                            JONES,JAMAL         Assistant Professor
    ## 1554                   JONES,JANA ELIZABETH         Associate Professor
    ## 1555                         JONES,KELLI J.         Clinical Assoc Prof
    ## 1556                             JONES,MATT         Associate Professor
    ## 1557                           JONES,THOMAS                   Professor
    ## 1558                           JONES,TOMIKO         Assistant Professor
    ## 1559                           JORDAN,JERRY       Sr Student Serv Coord
    ## 1560                   JORDON-THADEN,INGRID         Assoc Faculty Assoc
    ## 1561                      JORENBY,DOUGLAS E             Professor (Chs)
    ## 1562                         JORGENSEN,JOAN         Associate Professor
    ## 1563                          JOUINI,NAJOUA                    Lecturer
    ## 1564                    JOVIC-HUMPHREY,ANJA                    Lecturer
    ## 1565                        JOYNT,ROBERT J.                   Professor
    ## 1566                          JOZWIK,SARA L         Clinical Assoc Prof
    ## 1567                              JUAREZ,AJ              Assoc Lecturer
    ## 1568                             JUDGE,MIKE           Faculty Associate
    ## 1569                          JULL,LAURA G.         Associate Professor
    ## 1570                           JUN,MYUNGHEE           Faculty Associate
    ## 1571                           JUNG,HEE SOO       Assoc Professor (Chs)
    ## 1572                         JUSZCZYK,LAURA                    Lecturer
    ## 1573                          KABBAGE,MEHDI         Associate Professor
    ## 1574                           KADAKIA,MAYA              Assoc Lecturer
    ## 1575                         KAEPPLER,HEIDI         Associate Professor
    ## 1576                         KAEPPLER,SHAWN                   Professor
    ## 1577                          KAIKSOW,FARAH        Asst Professor (Chs)
    ## 1578                          KAISER,ROBERT                   Professor
    ## 1579                          KAJI,EUGENE H       Assoc Professor (Chs)
    ## 1580                          KALAN,LINDSAY         Assistant Professor
    ## 1581                         KALEJTA,ROBERT                   Professor
    ## 1582                            KALETKA,SUE          Sr Admin Prgm Spec
    ## 1583                    KALIN,MARC LAWRENCE          Clinical Asst Prof
    ## 1584                           KALIN,NED H.                   Professor
    ## 1585                      KALLENBERGER,MIKE              Assoc Lecturer
    ## 1586                     KALLENBORN,CAROLYN                   Professor
    ## 1587                            KALRA,PRIYA                    Lecturer
    ## 1588                      KALSCHEUR,KATHRYN                    Lecturer
    ## 1589                              KAMAL,RAJ                    Lecturer
    ## 1590                               KAMP,TIM                   Professor
    ## 1591                       KANAREK,MARTY S.                   Professor
    ## 1592                         KANE,COLLEEN A           Faculty Associate
    ## 1593                         KANG,HYUNSEUNG         Assistant Professor
    ## 1594                             KANG,JUNSU         Assistant Professor
    ## 1595                         KANN,STEPHANIE       Sr Student Serv Coord
    ## 1596                     KANTROWITZ,STEPHEN                   Professor
    ## 1597                       KAPLAN,ALLISON G       Dis Faculty Associate
    ## 1598                           KAPLAN,DAVID                   Professor
    ## 1599                            KAPP,DANIEL          Adjunct Assoc Prof
    ## 1600                          KAPUST,DANIEL                   Professor
    ## 1601                         KARAJIC,ALMIRA                    Lecturer
    ## 1602                        KARASOV,WILLIAM                   Professor
    ## 1603                         KARLE,ALBRECHT                   Professor
    ## 1604                             KARP,PARRY                   Professor
    ## 1605                        KARPUKHIN,S. A.                    Lecturer
    ## 1606               KARTHIKEYAN,KRISHNAPURAM                   Professor
    ## 1607                             KASAB,JOHN                    Lecturer
    ## 1608                         KASDORF,THOMAS              Assoc Lecturer
    ## 1609                      KASIETA,ROBERT J.          Adjunct Instructor
    ## 1610                         KASPAR,CHARLES                   Professor
    ## 1611                KASTBERG,ERIN ELIZABETH          Adjunct Instructor
    ## 1612                     KASTNER,KATHLEEN A        Asst Professor (Chs)
    ## 1613                           KATANICK,RON              Assoc Lecturer
    ## 1614                           KATS,MIKHAIL         Associate Professor
    ## 1615                 KAUSHANSKAYA,MARGARITA                   Professor
    ## 1616                    KAUTZER,MEGHAN ROSE                    Lecturer
    ## 1617                      KAWAOKA,YOSHIHIRO                   Professor
    ## 1618                       KAWASAKI,JASON K         Assistant Professor
    ## 1619                         KEAN,RONALD P.           Faculty Associate
    ## 1620                             KEANE,MARK               Professor L/I
    ## 1621                        KEANE,MARTIN T.              Assoc Lecturer
    ## 1622                KECHELE,LEAH MCLAUGHLIN          Clinical Asst Prof
    ## 1623                           KECK,JAMES L                   Professor
    ## 1624                 KEDZIORA,JEREMY THOMAS              Assoc Lecturer
    ## 1625                      KEEFOVER-RING,KEN         Assistant Professor
    ## 1626                           KEELER,KASEY         Assistant Professor
    ## 1627                        KEENAN,THOMAS D        Asst Professor (Chs)
    ## 1628                         KEEPMAN,SAMUEL         Clinical Instructor
    ## 1629                    KEHE,JESSI CISEWSKI         Assistant Professor
    ## 1630                           KELES,SUNDUZ                   Professor
    ## 1631                       KELLEHER,J. PAUL         Associate Professor
    ## 1632                        KELLER,MORGAN J                    Lecturer
    ## 1633                           KELLER,NANCY                   Professor
    ## 1634                       KELLER,RICHARD C                   Professor
    ## 1635                         KELLEY,CAROLYN                   Professor
    ## 1636                    KELLEY,OLIVIA MARIE          Adjunct Instructor
    ## 1637                       KELLEY,THERESA M                   Professor
    ## 1638                         KELLIHAN,HEIDI         Clinical Assoc Prof
    ## 1639                KELLOGG,KATHRYN REBECCA         Clinical Assoc Prof
    ## 1640                            KELLY,BARON                   Professor
    ## 1641                             KELLY,CLAY                   Professor
    ## 1642                     KELLY,ELIZABETH S.           Faculty Associate
    ## 1643                            KELLY,KEVIN            Associate Dean/M
    ## 1644                           KELLY,KRISTY         Clinical Assoc Prof
    ## 1645                         KELLY,SHAWN T.       Dis Faculty Associate
    ## 1646                     KEMENY,MICHAEL L J         Assistant Professor
    ## 1647                       KENDALL,NANCY O.                   Professor
    ## 1648               KENDZIORSKI,CHRISTINA M.                   Professor
    ## 1649                            KENNAN,JOHN                   Professor
    ## 1650                          KENNEDY,DEVIN         Assistant Professor
    ## 1651                 KENNEY,CATHERINE CLARA           Faculty Associate
    ## 1652                         KENNEY,SHANNON                   Professor
    ## 1653                   KENNY,AMANDA DILLARD             Senior Lecturer
    ## 1654                  KENOYER,JONATHAN MARK                   Professor
    ## 1655                       KENT,AUTUMN EXUM                   Professor
    ## 1656                              KENT,PAUL          Adjunct Instructor
    ## 1657                        KERCHEVAL,JESSE                   Professor
    ## 1658                           KERN,ADAM L.                   Professor
    ## 1659                         KERR, MARGARET         Assistant Professor
    ## 1660                KEULER,NICHOLAS STEPHEN         Assoc Faculty Assoc
    ## 1661                         KEYSER,RICHARD             Senior Lecturer
    ## 1662                         KHAN,ASAD RAZA              Assoc Lecturer
    ## 1663                           KHANNA,VARUN                    Lecturer
    ## 1664                        KHASAWNEH,SAMER           Faculty Associate
    ## 1665                           KHATIB,HASAN                   Professor
    ## 1666                           KHEDUP,JAMPA             Senior Lecturer
    ## 1667                   KIDWELL,AMANDA LYNNE                    Lecturer
    ## 1668                           KIEFER,DAVID          Clinical Asst Prof
    ## 1669                            KIESER,MARA             Professor (Chs)
    ## 1670                          KIGEYA,DANIEL                    Lecturer
    ## 1671                  KIHSLINGER,JANE ELLEN         Assistant Professor
    ## 1672                            KILEN,SARAH          Clinical Asst Prof
    ## 1673                      KILEY,PATRICIA J.                   Professor
    ## 1674                         KILGUS,STEPHEN         Associate Professor
    ## 1675                            KIM,CHANWOO         Associate Professor
    ## 1676                            KIM,CHARLES         Associate Professor
    ## 1677                            KIM,HIEYOON         Assistant Professor
    ## 1678                           KIM,JEE-SEON                   Professor
    ## 1679                          KIM,KYUNG-SUN                   Professor
    ## 1680                          KIM,KYUNGMANN                   Professor
    ## 1681                             KIM,MONICA         Assistant Professor
    ## 1682                              KIM,NAM C         Associate Professor
    ## 1683                           KIM,SUNG SIN                   Professor
    ## 1684                           KIM,YEA-SEUL         Assistant Professor
    ## 1685                                 KIM,YJ         Assistant Professor
    ## 1686                          KIM,YOUNG MIE                   Professor
    ## 1687                          KIM,YOUNGHYUN         Assistant Professor
    ## 1688                          KIMBLE,JUDITH                   Professor
    ## 1689                            KIMMEL,PAUL             Senior Lecturer
    ## 1690                        KIMPLE,MICHELLE         Associate Professor
    ## 1691                           KIMPLE,RANDY         Associate Professor
    ## 1692                   KIND,AMY JO HAAVISTO         Associate Professor
    ## 1693                           KING,BARBARA         Associate Professor
    ## 1694                          KING,M. BRUCE           Faculty Associate
    ## 1695                             KING,STEVE          Adjunct Instructor
    ## 1696                         KINNEY,MELISSA         Assistant Professor
    ## 1697                     KINTNER,EILEEN KAE                   Professor
    ## 1698                           KINZLEY,JUDD         Associate Professor
    ## 1699                           KIRCH,JEREMY          Asst Faculty Assoc
    ## 1700           KIRCHDOERFER,ROBERT NICHOLAS         Assistant Professor
    ## 1701                      KIRCHGASLER,CHRIS         Assistant Professor
    ## 1702                      KIRCHGASLER,KATIE         Assistant Professor
    ## 1703                   KIRK,GWENDOLYN SARAH                    Lecturer
    ## 1704                      KIRKORIAN,HEATHER         Associate Professor
    ## 1705                KIRKPATRICK,BRIAN WAYNE                   Professor
    ## 1706                      KIRPALANI,RISHABH         Assistant Professor
    ## 1707                            KITA,ANGELA         Assoc Faculty Assoc
    ## 1708                             KLATT,JOHN          Assistant Dean/M-L
    ## 1709                        KLEEDEHN,MARK G        Asst Professor (Chs)
    ## 1710                    KLEHR,MARY RAIMONDA                    Lecturer
    ## 1711                         KLEIJWEGT,MARC                   Professor
    ## 1712                     KLEIN,BRUCE STEVEN                   Professor
    ## 1713                         KLIEWER,MARK A                   Professor
    ## 1714                        KLINGBEIL,DAVID         Assistant Professor
    ## 1715                       KLINGELE,CECELIA         Associate Professor
    ## 1716                        KLINGENBERG,DAN                   Professor
    ## 1717                           KLOCKE,SONJA         Associate Professor
    ## 1718                             KLUG,HEINZ                   Professor
    ## 1719                         KNEZEVIC,IRENA                   Professor
    ## 1720                          KNISHKA,SCOTT          Clinical Asst Prof
    ## 1721                   KNOCH,DANIEL WILLIAM             Professor (Chs)
    ## 1722                            KNOLL,LAURA                   Professor
    ## 1723                     KNOX,KJERSTI ELISE  Clinical Adjunct Asst Prof
    ## 1724                        KNUTSON,JASON J          Adjunct Instructor
    ## 1725                         KOBERNUSZ,JEFF         Clinical Instructor
    ## 1726                              KOCH,PAUL         Associate Professor
    ## 1727                            KODESH,NEIL                   Professor
    ## 1728                            KOENIG,JANE             Senior Lecturer
    ## 1729                           KOENIGS,MIKE                   Professor
    ## 1730                            KOH,LINDSAY           Faculty Associate
    ## 1731                           KOKJOHN,SAGE         Associate Professor
    ## 1732                             KOKO,MARIE              Assoc Lecturer
    ## 1733                       KOLKOWITZ,SHIMON         Assistant Professor
    ## 1734                       KOLOWRAT,KATIE M         Clinical Instructor
    ## 1735                      KOLTYN,KELLI FAYE                   Professor
    ## 1736                          KONG,JOOYOUNG         Assistant Professor
    ## 1737                           KONOPKA,ADAM         Assistant Professor
    ## 1738                            KONZ,ANDREA              Assoc Lecturer
    ## 1739                          KOPACEK,KAREN       Assoc Professor (Chs)
    ## 1740                 KORLAKAI VINAYAK,RAMYA         Assistant Professor
    ## 1741                          KORNBLUM,RENA             Senior Lecturer
    ## 1742                  KOROSEC,FRANK RICHARD             Professor (Chs)
    ## 1743                        KOSS,PHILLIP A.          Adjunct Instructor
    ## 1744                    KOTELNICKI,MARYRUTH       Assoc Student Sv Spec
    ## 1745                 KOTLOSKI,ROBERT JOSEPH         Assistant Professor
    ## 1746                         KOTULLA,RALF C              Assoc Lecturer
    ## 1747                              KOU,SINDO                   Professor
    ## 1748                          KOUTRIS,PARIS         Assistant Professor
    ## 1749                       KOWALKOWSKI,ANNA              Assoc Lecturer
    ## 1750                      KOWALSKI,ALYCIA A         Clinical Instructor
    ## 1751                             KOZA,JULIA                   Professor
    ## 1752                KRABBENHOFT,KAREN MARIE             Senior Lecturer
    ## 1753                         KRACHEY,JOSEPH           Faculty Associate
    ## 1754                       KRAHN,ELLEN JEAN         Clinical Instructor
    ## 1755                   KRANNER,PAUL WILLIAM       Assoc Professor (Chs)
    ## 1756          KRATTIGER-ZILTENER,NANCY JOAN         Assoc Faculty Assoc
    ## 1757                         KRAUSKOPF,SARA       Assoc Instructnl Spec
    ## 1758            KRAUTHAMER-MALONEY,AMY BETH              Assoc Lecturer
    ## 1759                            KREEGER,PAM         Associate Professor
    ## 1760                       KREITMAIR,KAROLA         Assistant Professor
    ## 1761                   KRISHNASWAMY,BHUVANA         Assistant Professor
    ## 1762                        KROLL,AMY KNOTT         Clinical Assoc Prof
    ## 1763                          KROUK,DEAN N.         Associate Professor
    ## 1764                          KRUEGER,KATIE                    Lecturer
    ## 1765                           KRUG,HEATHER         Clinical Assoc Prof
    ## 1766                            KRUGER,ERIC                   Professor
    ## 1767                    KRUMMEN-LEE,GAIL A.         Clinical Instructor
    ## 1768                          KRUPENKIN,TOM         Associate Professor
    ## 1769                       KRYSAN,PATRICK J                   Professor
    ## 1770                       KUBSCH,SYLVIA M.           Faculty Associate
    ## 1771                   KUCHARIK,CHRISTOPHER                   Professor
    ## 1772                             KUCHER,JAN           Adjunct Professor
    ## 1773                           KUCHNIA,ADAM         Assistant Professor
    ## 1774                           KUCIN,AMY V.                    Lecturer
    ## 1775                       KUEMMEL,ANDREW L         Assoc Faculty Assoc
    ## 1776                            KUHL,ASHLEY       Sr Clin Genetic Couns
    ## 1777                     KUHN,BRIANNA RENEE                    Lecturer
    ## 1778                         KUHRASCH,CINDY           Faculty Associate
    ## 1779                            KUKA,RONALD           Faculty Associate
    ## 1780                           KULIG,STEVEN              Assoc Lecturer
    ## 1781                          KUMAR,SATHISH         Associate Professor
    ## 1782                           KUO,WAN-CHIN                    Lecturer
    ## 1783                            KURTZ,ROBIN       Dis Faculty Associate
    ## 1784                           KURUTZ,MARIA          Asst Faculty Assoc
    ## 1785                         KUZUHARA,LOREN             Senior Lecturer
    ## 1786                             KWAN,JASON         Associate Professor
    ## 1787                        KWASNY,MICHELLE           Faculty Associate
    ## 1788                    KWEKKEBOOM,KRISTINE                   Professor
    ## 1789                KWIECINSKI,BROOKE RENEE         Clinical Assoc Prof
    ## 1790                            KWON,DOHYUN          Visiting Asst Prof
    ## 1791                              KWON,GLEN                   Professor
    ## 1792                           KWON,OH HOON         Assoc Faculty Assoc
    ## 1793                            KYDD,ANDREW                   Professor
    ## 1794                       LA ROWE,TARA LEA         Assoc Faculty Assoc
    ## 1795                                 LA,CHI           Adjunct Asst Prof
    ## 1796                        LABELLE,SUSAN M           Adjunct Professor
    ## 1797                         LABOSKI,CARRIE                   Professor
    ## 1798                          LACROSSE,TONY       Instructor Of Mil Sci
    ## 1799                           LAESEKE,PAUL         Assistant Professor
    ## 1800                         LAGALLY,MAX G.              Professor Emer
    ## 1801                          LAGMAN,EILEEN         Assistant Professor
    ## 1802                            LAGRO,JAMES                   Professor
    ## 1803                          LAHTI,JOHN L.           Adjunct Asst Prof
    ## 1804                         LAI,HUICHUAN J                   Professor
    ## 1805                           LAJCAK,RENEE             Senior Lecturer
    ## 1806                          LAKES,RODERIC                   Professor
    ## 1807                           LAMBERT,PAUL                   Professor
    ## 1808                       LAMMING,DUDLEY W         Associate Professor
    ## 1809                           LAMONT,LIANA           Faculty Associate
    ## 1810                     LANDESS,JACQUELINE  Clinical Adjunct Asst Prof
    ## 1811                  LANDGRAF,THOMAS ALLAN             Senior Lecturer
    ## 1812                         LANDICK,ROBERT                   Professor
    ## 1813                        LANDIS,CLARK R.                   Professor
    ## 1814                    LANG,JOSHUA MICHAEL         Associate Professor
    ## 1815                    LANG,LAURA MICHELLE         Assoc Faculty Assoc
    ## 1816                      LANGVA,GLORIANN F                    Lecturer
    ## 1817                    LANIUS,JESSICA BESS                    Lecturer
    ## 1818                         LANKAU,RICHARD         Associate Professor
    ## 1819                      LAPIN,JOSHUA ADAM         Assoc Faculty Assoc
    ## 1820                       LAPINA,ELIZABETH         Associate Professor
    ## 1821                        LAPLANTE,MARK J             Senior Lecturer
    ## 1822                        LAPLANTE,STACIE         Associate Professor
    ## 1823                          LAPOINT,PAIGE                    Lecturer
    ## 1824                         LAPORTA,JIMENA         Assistant Professor
    ## 1825                     LARGET,BRET ROBERT                   Professor
    ## 1826                       LARK,TYLER JAMES                    Lecturer
    ## 1827                          LAROCHE,CHRIS             Senior Lecturer
    ## 1828                   LARSEN-KLODD,KATHRYN         Assoc Faculty Assoc
    ## 1829                       LARSON,ELIZABETH         Associate Professor
    ## 1830                  LARSON,JENNIFER CISKE        Asst Professor (Chs)
    ## 1831                       LARSON,LAURIE J.            Senior Scientist
    ## 1832        LARSON-GUENETTE,JULIE CHRISTINE         Assoc Faculty Assoc
    ## 1833                         LASKEY,FRANCES                    Lecturer
    ## 1834                        LATIMER,TIMOTHY           Faculty Associate
    ## 1835                    LATTIS,JAMES MARION           Faculty Associate
    ## 1836                          LAUGHON,ALLEN              Professor Emer
    ## 1837                         LAUHON,CHARLES         Associate Professor
    ## 1838                         LAURENZ,JEAN M         Assistant Professor
    ## 1839                      LAUVER,DIANE RUTH                   Professor
    ## 1840                        LAVIN,KELLY ANN          Clinical Asst Prof
    ## 1841                    LAWLER,JAMES EDWARD                   Professor
    ## 1842                         LAYOUN,MARY N.                   Professor
    ## 1843                          LAZARIAN,ALEX                   Professor
    ## 1844                               LE,HAU D         Assistant Professor
    ## 1845                       LECLAIR, JESSICA         Clinical Instructor
    ## 1846                      LECUYER,TRISTAN S                   Professor
    ## 1847                    LEDERER,SUSAN MARIE                   Professor
    ## 1848                           LEDESMA,EDNA         Assistant Professor
    ## 1849                             LEE,ALICIA         Assistant Professor
    ## 1850                        LEE,CAROL EUNMI                   Professor
    ## 1851                              LEE,CHOUA                    Lecturer
    ## 1852                              LEE,GRACE         Assoc Faculty Assoc
    ## 1853                              LEE,HARRY          Visiting Asst Prof
    ## 1854                              LEE,HELEN         Associate Professor
    ## 1855                               LEE,JOHN                   Professor
    ## 1856                            LEE,JONAS J       Assoc Professor (Chs)
    ## 1857                           LEE,KANGWOOK         Assistant Professor
    ## 1858                              LEE,LAURA         Clinical Instructor
    ## 1859                             LEE,RACHEL          Clinical Asst Prof
    ## 1860                             LEE,STACEY                   Professor
    ## 1861                                LEE,TEV                    Lecturer
    ## 1862                          LEE,YOUNGSOOK         Associate Professor
    ## 1863                    LEES,THOMAS MICHAEL                    Lecturer
    ## 1864                         LEFF,PAUL ADAM                    Lecturer
    ## 1865                         LEGAULT,HOBBES         Assoc Faculty Assoc
    ## 1866                         LEGENZA,LAUREL         Assoc Faculty Assoc
    ## 1867                               LEI,REED         Assistant Professor
    ## 1868                     LEITH,ELIZABETH A.                    Lecturer
    ## 1869                           LEKO,MELINDA                   Professor
    ## 1870                   LEMASTER,TRACY WENDT                    Lecturer
    ## 1871                 LEMIRAND-POEPPING,DAWN           Faculty Associate
    ## 1872                          LEMPP,STEFFEN                   Professor
    ## 1873                           LENNIX,SHAWN         Clinical Instructor
    ## 1874                           LENTZ,RASMUS                   Professor
    ## 1875                      LEONARD,KATHERINE         Clinical Instructor
    ## 1876                          LEONE,VANESSA         Assistant Professor
    ## 1877                         LEPOWSKY,MARIA                   Professor
    ## 1878                            LERMAN,OMER         Clinical Instructor
    ## 1879                       LESIEUTRE,BERNIE                   Professor
    ## 1880                        LESLIE,TREVOR M          Visiting Asst Prof
    ## 1881                        LESSARD,LAURENT         Assistant Professor
    ## 1882                         LEVCHENKO,ALEX                   Professor
    ## 1883                       LEVCHENKO,POLINA          Asst Faculty Assoc
    ## 1884                  LEVENSON,BARRY MARTIN          Adjunct Instructor
    ## 1885                          LEVERTY,TYLER         Associate Professor
    ## 1886                         LEVIN,KEITH D.         Assistant Professor
    ## 1887                          LEVINE,OLIVER         Associate Professor
    ## 1888                     LEWIS,ALICE KELSEY              Assoc Lecturer
    ## 1889                   LEWIS,DAVID LAWRENCE           Adjunct Professor
    ## 1890                          LEWIS,PETER W         Associate Professor
    ## 1891                       LEWIS,SHANA RUTH          Adjunct Instructor
    ## 1892                   LEWIS-WILLIAMS,TRACY           Faculty Associate
    ## 1893                          LI,CHIAO-PING                   Professor
    ## 1894                               LI,JAMES         Assistant Professor
    ## 1895                            LI,JINGSHAN                   Professor
    ## 1896                                  LI,KE         Assistant Professor
    ## 1897                             LI,LINGJUN                   Professor
    ## 1898                                 LI,MIN             Senior Lecturer
    ## 1899                                 LI,NAN         Assistant Professor
    ## 1900                                 LI,QIN         Associate Professor
    ## 1901                              LI,SHARON         Assistant Professor
    ## 1902                              LI,WAN-JU         Associate Professor
    ## 1903                              LI,WEIJIA         Assistant Professor
    ## 1904                               LI,YAFEI                   Professor
    ## 1905                                 LI,YIN         Assistant Professor
    ## 1906                              LI,YUHANG         Associate Professor
    ## 1907                           LIANG,YINGYU         Assistant Professor
    ## 1908                              LIANG,YUN         Assistant Professor
    ## 1909                             LIDOR,ANNE             Professor (Chs)
    ## 1910                            LIEBE,ETHAN              Assoc Lecturer
    ## 1911                   LIGHT,MICHAEL THOMAS         Associate Professor
    ## 1912                          LIKOS,WILLIAM                   Professor
    ## 1913                          LIM,BYUNG-JIN         Associate Professor
    ## 1914                           LIM,CHAEYOON                   Professor
    ## 1915                              LIM,CI JI         Assistant Professor
    ## 1916                            LIM,SIN YIN        Asst Professor (Chs)
    ## 1917                   LIN,JASON CHIEH-SHEN             Senior Lecturer
    ## 1918                          LINDBERG,SARA        Asst Professor (Chs)
    ## 1919                         LINDEMANN,ABBY                    Lecturer
    ## 1920                      LINDEROTH,JEFFREY                   Professor
    ## 1921                            LINDLEY,BEN         Assistant Professor
    ## 1922                          LINDROTH,RICK                   Professor
    ## 1923                         LINDSAY,KEISHA         Associate Professor
    ## 1924                        LINDSEY,MELISSA           Faculty Associate
    ## 1925                LINDSTROM,TIMOTHY DAVID              Assoc Lecturer
    ## 1926                    LINSMEIER,THOMAS J.                   Professor
    ## 1927                            LINTNER,KIM         Clinical Instructor
    ## 1928                LINZMEIER,BENJAMIN JOHN              Assoc Lecturer
    ## 1929                          LIPASTI,MIKKO                   Professor
    ## 1930                    LIPINSKI,ROBERT JAN         Associate Professor
    ## 1931                           LISOWSKI,DAN         Associate Professor
    ## 1932                        LITOVSKY,RUTH Y                   Professor
    ## 1933                      LITZELMAN,KRISTIN         Assistant Professor
    ## 1934                                 LIU,BO                   Professor
    ## 1935                              LIU,GLENN                   Professor
    ## 1936                              LIU,KAIBO         Associate Professor
    ## 1937                               LIU,QING         Associate Professor
    ## 1938                                LIU,RAN         Assistant Professor
    ## 1939                    LIVANOS,CHRISTOPHER                   Professor
    ## 1940                        LIVORNI,ERNESTO                   Professor
    ## 1941                       LIWE,AMELIA JOAN           Faculty Associate
    ## 1942                            LLOYD,SARAH         Associate Scientist
    ## 1943                     LO SARDO,VALENTINA         Assistant Professor
    ## 1944                           LO,ADELINE Y         Assistant Professor
    ## 1945                         LOCONTE,NOELLE         Associate Professor
    ## 1946                               LOEB,DAN                   Professor
    ## 1947                        LOEBER,SAMANTHA          Clinical Asst Prof
    ## 1948                           LOEWEN,CARIN          Asst Faculty Assoc
    ## 1949                       LOFTON,LAUREN K.                    Lecturer
    ## 1950                            LOH,PO-LING         Associate Professor
    ## 1951                            LOH,WEI-YIN                   Professor
    ## 1952                 LOHEIDE II,STEVEN PAUL                   Professor
    ## 1953                        LOKUTA,ANDREW J           Faculty Associate
    ## 1954        LONDON-JOHNSON,ANTOINETTE MARIE              Assoc Lecturer
    ## 1955                      LONG,MICAH THOMAS        Asst Professor (Chs)
    ## 1956                              LONG,PETE         Assoc Faculty Assoc
    ## 1957                          LONG,XIAOYANG         Assistant Professor
    ## 1958                      LONGO,LANCE PETER Clinical Adjunct Assoc Prof
    ## 1959                             LOOK,KEVIN         Assistant Professor
    ## 1960                            LOPEZ,JASON         Assistant Professor
    ## 1961                             LOPEZ,LORI         Associate Professor
    ## 1962                LOPEZ-HERNANDEZ,ARNOLDO                    Lecturer
    ## 1963                            LOR,MAICHOU         Assistant Professor
    ## 1964                       LORD PLUMMER,KIM             Senior Lecturer
    ## 1965                       LOTHARY,BRITTA N         Clinical Instructor
    ## 1966                            LOTHE,KATIE         Clinical Assoc Prof
    ## 1967                      LOTLIKAR,SUSHMITA                    Lecturer
    ## 1968                          LOTTA,CORISSA           Faculty Associate
    ## 1969                            LOUDEN,MARK                   Professor
    ## 1970                         LOUIE,NICOLE L         Assistant Professor
    ## 1971                            LOVE,HAILEY         Assistant Professor
    ## 1972                 LOVELACE,DAVID MICHAEL         Assistant Scientist
    ## 1973                           LOWE,CHLORIS                    Lecturer
    ## 1974                           LOYD,JENNA M         Associate Professor
    ## 1975                            LU,QIONGSHI         Assistant Professor
    ## 1976                      LUBNER,SAM JOSEPH       Assoc Professor (Chs)
    ## 1977                         LUBSEN,JULIA R        Asst Professor (Chs)
    ## 1978                            LUBY,CLAIRE                    Lecturer
    ## 1979                          LUCEY,JOHN A.                   Professor
    ## 1980                        LUCEY,MICHAEL R                   Professor
    ## 1981                             LUCK,BRIAN         Assistant Professor
    ## 1982                    LUDOIS,DANIEL COLIN         Associate Professor
    ## 1983                 LUDVIK,GEOFFREY EDMOND              Assoc Lecturer
    ## 1984                       LUDWIG,KIP ALLAN         Associate Professor
    ## 1985                            LUEDTKE,JIM                   Professor
    ## 1986                        LUKSZYS,PETER B             Senior Lecturer
    ## 1987                       LUNASIN,EVELYN M         Visiting Assoc Prof
    ## 1988                        LUND,JANE RENEE          Clinical Asst Prof
    ## 1989                            LUPYAN,GARY                   Professor
    ## 1990                      LUTER,DAVID GAVIN              Assoc Lecturer
    ## 1991                      LUTZ,ROBERT SCOTT         Associate Professor
    ## 1992                   LUZZIO,CHRISTOPHER C       Assoc Professor (Chs)
    ## 1993                              LYNCH,DAN         Associate Professor
    ## 1994                          LYNN,DAVID M.                   Professor
    ## 1995                       LYONS,JOHN DAVID              Assoc Lecturer
    ## 1996                                 MA,CHU         Assistant Professor
    ## 1997                           MA,ZHENQIANG                   Professor
    ## 1998                   MACASAET,DAVID WEBER                    Lecturer
    ## 1999                        MACAULAY,MONICA                   Professor
    ## 2000                    MACDONALD,MARYELLEN                   Professor
    ## 2001                            MACE,DAKOTA                    Lecturer
    ## 2002                      MACGUIDWIN,ANN E.                   Professor
    ## 2003                          MACHADO,EMILY         Assistant Professor
    ## 2004                       MACHLEIDT,THOMAS           Adjunct Professor
    ## 2005                        MACHOIAN,RONALD             Senior Lecturer
    ## 2006                            MACKAY,JOHN         Associate Professor
    ## 2007                        MACOMBER,KELSEY              Assoc Lecturer
    ## 2008                         MADDEN,CAITLIN          Adjunct Instructor
    ## 2009                           MADDEN,HALEY         Outreach Specialist
    ## 2010                         MADUREIRA,LUIS                   Professor
    ## 2011                          MAEDA,HIROSHI         Associate Professor
    ## 2012                            MAES,MARINA        Asst Professor (Chs)
    ## 2013                         MAGANTI,RAMA K             Professor (Chs)
    ## 2014                       MAGNOLFI,LORENZO         Assistant Professor
    ## 2015                MAGNUSON,KATHERINE ANNE                   Professor
    ## 2016                        MAGUIRE,MICHAEL         Assoc Faculty Assoc
    ## 2017                        MAHER,JESSICA M                    Lecturer
    ## 2018                        MAHMOUD,AHMED I         Assistant Professor
    ## 2019                   MAIER,JOSEPH MICHAEL          Adjunct Instructor
    ## 2020                     MAJUMDER,ERICA L-W         Assistant Professor
    ## 2021                        MAJUMDER,KINJAL         Assistant Professor
    ## 2022                         MAKI,DENNIS G.              Professor Emer
    ## 2023                        MAKI,LYNN MARIE              Assoc Lecturer
    ## 2024                        MALECKI,KRISTEN         Associate Professor
    ## 2025                       MALITSKY,EUGENIA                    Lecturer
    ## 2026                         MALLOY,MATTHEW           Adjunct Asst Prof
    ## 2027               MALONE,KRISTA-LEE MEGHAN           Faculty Associate
    ## 2028                    MALONE,MARY KATHRYN           Faculty Associate
    ## 2029                MALSON-HUDDLE,ELIZABETH             Senior Lecturer
    ## 2030                            MANDEL,MARK         Associate Professor
    ## 2031                         MANI,B. VENKAT                   Professor
    ## 2032                       MANKOWSKI,JOEL E             Senior Lecturer
    ## 2033                     MANN,TERRY MICHAEL             Senior Lecturer
    ## 2034                         MANS,CHRISTOPH         Clinical Assoc Prof
    ## 2035                                 MAO,LU         Assistant Professor
    ## 2036                           MARA,KATHRYN              Assoc Lecturer
    ## 2037                    MARAVELIAS,CHRISTOS                   Professor
    ## 2038                       MARCHE,JORDAN D.             Senior Lecturer
    ## 2039                   MARCOTT,SHAUN ANDREW         Associate Professor
    ## 2040                      MARCOUILLER,DAVID                   Professor
    ## 2041                     MARES,MARIE-LOUISE                   Professor
    ## 2042               MARES-PERLMAN,JULIE ANNE                   Professor
    ## 2043                        MARGOLIS,AMANDA        Asst Professor (Chs)
    ## 2044                      MARI-BEFFA,GLORIA                   Professor
    ## 2045                    MARIN-SPIOTTA,ERIKA                   Professor
    ## 2046                 MARINEZ LORA,ANE MARIA                    Lecturer
    ## 2047                         MARKEL,MARK D.                   Professor
    ## 2048                            MARKER,PAUL                   Professor
    ## 2049                       MARLER,CATHERINE                   Professor
    ## 2050                       MAROON,ELIZABETH         Assistant Professor
    ## 2051                MARQUES,FERNANDO JAVIER         Clinical Assoc Prof
    ## 2052                       MARQUEZ,BENJAMIN                   Professor
    ## 2053                      MARSH FINCO,JAMIE         Assoc Faculty Assoc
    ## 2054                              MARSH,ANN              Assoc Lecturer
    ## 2055                         MARSHALL,NANCY                   Professor
    ## 2056                 MARSHALL,NOWELL ANDREW             Senior Lecturer
    ## 2057                 MARSHALL,SIMON LINDSAY         Associate Professor
    ## 2058                      MARTELL,JEFFREY D         Assistant Professor
    ## 2059                       MARTIN,ANN SMART                   Professor
    ## 2060                            MARTIN,BETH             Professor (Chs)
    ## 2061                          MARTIN,DARREN       Student Services Cord
    ## 2062                         MARTIN,JESSICA           Adjunct Professor
    ## 2063                            MARTIN,JOHN              Assoc Lecturer
    ## 2064                 MARTIN,JONATHAN EDWARD                   Professor
    ## 2065                           MARTIN,KERRY           Faculty Associate
    ## 2066                            MARTIN,LISA                   Professor
    ## 2067                      MARTIN,THOMAS F J                   Professor
    ## 2068                        MARTINEZ,MARCOS              Assoc Lecturer
    ## 2069                             MARTINS,JP         Assistant Professor
    ## 2070                            MARTY,SARAH           Faculty Associate
    ## 2071                  MARULASIDDAPPA,SURESH                   Professor
    ## 2072                         MASON,ANDREA H                   Professor
    ## 2073                           MASON,JOSEPH                   Professor
    ## 2074                          MASROUR,FARID         Associate Professor
    ## 2075                    MASSOGLIA,MICHAEL A                   Professor
    ## 2076                         MASSON,PATRICK                   Professor
    ## 2077                        MASTERS,KRISTYN                   Professor
    ## 2078                            MATHEWS,JIM                    Lecturer
    ## 2079                      MATHIEU,ROBERT D.                   Professor
    ## 2080                     MATSUMURA,ELLA MAE                   Professor
    ## 2081                    MATTHEWS,PERCIVAL G         Associate Professor
    ## 2082                         MATTHIES,ROBIN              Assoc Lecturer
    ## 2083                           MATTILA,DANE                    Lecturer
    ## 2084                        MATTIS,KRISTINE          Asst Faculty Assoc
    ## 2085                   MATULIONIS,GAUDRIMAS        Asst Prof Of Mil Sci
    ## 2086                           MAUK,MATTHEW                    Lecturer
    ## 2087                       MAVRIKAKIS,MANOS                   Professor
    ## 2088                             MAWST,LUKE                   Professor
    ## 2089                        MAXIM,LAURENTIU                   Professor
    ## 2090                          MAYER,KENNETH                   Professor
    ## 2091                        MAYERS,JOSHUA B           Adjunct Asst Prof
    ## 2092                         MAYHEW,BRIAN W                   Professor
    ## 2093                     MAYNARD,DOUGLAS W.                   Professor
    ## 2094             MC ANULTY,JONATHAN FRANCIS                   Professor
    ## 2095                          MC CAMMON,DAN                   Professor
    ## 2096                           MC CLAIN,ROB           Faculty Associate
    ## 2097                        MC DANIEL,SARAH                    Lecturer
    ## 2098                        MC LEOD,DOUGLAS                   Professor
    ## 2099             MC SHANE-HELLENBRAND,KAREN           Faculty Associate
    ## 2100                        MCANDREWS,CAREY         Associate Professor
    ## 2101                 MCAULIFFE,NOREEN MARIE              Assoc Lecturer
    ## 2102                        MCBRIDE,ERIN K.         Clinical Assoc Prof
    ## 2103                   MCCALLUM,JAMES SCOTT          Adjunct Assoc Prof
    ## 2104                           MCCARTHY,LIZ                  Sr Advisor
    ## 2105                         MCCARY,LINDSAY  Clinical Adjunct Asst Prof
    ## 2106                          MCCLEAN,MEGAN         Assistant Professor
    ## 2107                            MCCLURG,TIM             Senior Lecturer
    ## 2108                   MCCORD,ALEIA INGULLI         Assoc Faculty Assoc
    ## 2109                   MCCOY,ALFRED WILLIAM                   Professor
    ## 2110                                MCCOY,M           Faculty Associate
    ## 2111                             MCCOY,SARA        Asst Professor (Chs)
    ## 2112                   MCCULLEY,DAVID JAMES         Assistant Professor
    ## 2113                          MCCULLOH,KATE         Associate Professor
    ## 2114                      MCCULLOUGH,CHAD J              Assoc Lecturer
    ## 2115                       MCCURDY,MARTHA L                    Lecturer
    ## 2116                        MCDERMOTT,MEGAN                    Lecturer
    ## 2117                     MCDERMOTT,ROBERT F                   Professor
    ## 2118                MCDONALD,DAVID MACLAREN                   Professor
    ## 2119                        MCDONALD,JOSEPH              Assoc Lecturer
    ## 2120                 MCDONALD,PETER DOUGLAS         Assistant Professor
    ## 2121                       MCDONNELL,TERESA           Adjunct Professor
    ## 2122                     MCDOWELL,COLLEEN M         Assistant Professor
    ## 2123                      MCFARLAND,RICHARD         Associate Professor
    ## 2124                         MCGARR,KATHRYN         Assistant Professor
    ## 2125                       MCGLAMERY,THOMAS           Faculty Associate
    ## 2126                      MCGRANAHAN,PAMELA         Clinical Assoc Prof
    ## 2127                        MCINNES,BRIAN D         Associate Professor
    ## 2128                   MCKELVEY,CHRISTOPHER                    Lecturer
    ## 2129                          MCKEOWN,JAMES                   Professor
    ## 2130             MCKINNEY DE ROYSTON,MAXINE         Assistant Professor
    ## 2131                          MCKINNON,SARA         Associate Professor
    ## 2132                        MCKOWN,KEVIN M.          Clinical Asst Prof
    ## 2133                       MCLELLAN,GILLIAN         Associate Professor
    ## 2134                   MCLEOD,ZACHARY DAVID          Admin Program Spec
    ## 2135                      MCMAHON,KATHERINE                   Professor
    ## 2136                      MCMAHON,ROBERT J.                   Professor
    ## 2137                         MCMASTER,JAMES         Assistant Professor
    ## 2138                    MCMILLAN,ALAN BLAIR       Assoc Professor (Chs)
    ## 2139                         MCMILLAN,DAWNA          Clinical Asst Prof
    ## 2140                 MCNAMARA,NICHOLAS JOEL          Adjunct Instructor
    ## 2141                  MCNEEL,DOUGLAS GORDON                   Professor
    ## 2142               MCQUILLAN,MOLLIE THERESE         Assistant Professor
    ## 2143                           MEAD,JULIE F                   Professor
    ## 2144                     MEAD,SCOTT MICHAEL         Clinical Assoc Prof
    ## 2145                         MECOZZI,SANDRO                   Professor
    ## 2146                           MEDINA,RUBEN                   Professor
    ## 2147                           MEDNICK,ADAM                    Lecturer
    ## 2148                      MEDOW,JOSHUA ERIC         Associate Professor
    ## 2149                           MEHLE,ANDREW         Associate Professor
    ## 2150                           MEIER,ALISON              Assoc Lecturer
    ## 2151                          MEILLER,LARRY              Professor Emer
    ## 2152                   MEKEEL,WILLIAM JAMES             Senior Lecturer
    ## 2153                  MELLO,ANTONIO SAMPAIO                   Professor
    ## 2154                           MELLOR,SCOTT       Dis Faculty Associate
    ## 2155                      MENDONCA,ENEIDA A       Honorary Assoc/Fellow
    ## 2156                   MENDOZA RIVERA,HENRY             Senior Lecturer
    ## 2157                      MENECHELLA,GRAZIA         Associate Professor
    ## 2158                           MENZEL,ANNIE         Assistant Professor
    ## 2159                        MERCADO,SARLI E             Senior Lecturer
    ## 2160                       MERMELSTEIN,OMER          Visiting Asst Prof
    ## 2161                  MERRINS,MATTHEW JAMES         Assistant Professor
    ## 2162                            MERTZ,JANET                   Professor
    ## 2163                          MESSINA,JAMES         Associate Professor
    ## 2164                   METCALF,CARISSA ROSE              Assoc Lecturer
    ## 2165                            MEURIS,JIRS         Assistant Professor
    ## 2166                           MEYER,DANIEL                   Professor
    ## 2167                      MEYER,GABRIELE E.           Faculty Associate
    ## 2168                         MEYER,LAUREN N                    Lecturer
    ## 2169                    MEYER,MARK BENJAMIN              Assoc Lecturer
    ## 2170                          MEYERAND,BETH                   Professor
    ## 2171                        MEYERS,JENNIFER                    Lecturer
    ## 2172                          MEYERS,ROSS O         Assoc Faculty Assoc
    ## 2173                       MEYERS,STEPHEN R                   Professor
    ## 2174                               MEYN,ION         Assistant Professor
    ## 2175                         MIALIK,HEATHER        Instructl Prg Mgr Ii
    ## 2176                     MICHAUD,MARY DAVIS           Faculty Associate
    ## 2177                           MICHELS,TONY                   Professor
    ## 2178                          MICHINI,CARLA         Assistant Professor
    ## 2179                  MICKELSON,JAMIE IRENE                    Lecturer
    ## 2180                       MIDDLECAMP,CATHY                   Professor
    ## 2181                     MIER-CRUZ,BENJAMIN         Assistant Professor
    ## 2182                         MIERNOWSKA,EWA             Senior Lecturer
    ## 2183                         MIERNOWSKI,JAN                   Professor
    ## 2184                       MIKKELSON,ANDREW         Assoc Faculty Assoc
    ## 2185                     MILENKOVIC,PAUL H.         Associate Professor
    ## 2186                         MILES,KELSEY C              Assoc Lecturer
    ## 2187                         MILICIC,SRDJAN         Assoc Faculty Assoc
    ## 2188                       MILKOWSKI,ANDREW           Adjunct Professor
    ## 2189                       MILLER,BARTON P.                   Professor
    ## 2190                          MILLER,DENNIS                   Professor
    ## 2191                            MILLER,ERIC                    Lecturer
    ## 2192                        MILLER,FRANKLIN         Associate Professor
    ## 2193                           MILLER,JAMES           Faculty Associate
    ## 2194                           MILLER,JANEL                    Lecturer
    ## 2195                        MILLER,JOSEPH S                   Professor
    ## 2196                         MILLER,MICHAEL       Honorary Assoc/Fellow
    ## 2197                         MILLER,PAUL E.          Clinical Professor
    ## 2198                         MILLER,PETER M                   Professor
    ## 2199                             MILLS,NEIL         Assistant Professor
    ## 2200                            MILTON,ROSS         Assistant Professor
    ## 2201                            MIN,SANGKEE         Assistant Professor
    ## 2202                 MINI,DARSHANA SREEDHAR         Assistant Professor
    ## 2203             MINICHIELLO,VINCENT JOSEPH        Asst Professor (Chs)
    ## 2204                          MINTZ,YONATAN         Assistant Professor
    ## 2205                       MIRANDA,ALMITA A         Assistant Professor
    ## 2206                MIRSHARIFI,FATEMEHSADAT                    Lecturer
    ## 2207                         MISEY,ROBERT J          Adjunct Instructor
    ## 2208                   MISSION,PAIGE LAUREN                    Lecturer
    ## 2209                                MITCH,-          Clinical Professor
    ## 2210                     MITCHELL,CAROL K C       Assoc Professor (Chs)
    ## 2211                     MITCHELL,EVERETT D          Adjunct Instructor
    ## 2212                           MITCHELL,MEG         Associate Professor
    ## 2213                          MITCHELL,PAUL                   Professor
    ## 2214                         MITCHELL,SUSAN              Assoc Lecturer
    ## 2215                           MITMAN,GREGG                   Professor
    ## 2216                       MIYAMOTO,SHIGEKI                   Professor
    ## 2217                     MIYASAKI,JAN KEIKO             Senior Lecturer
    ## 2218                        MLADENOFF,DAVID              Professor Emer
    ## 2219                           MOBLEY,SCOTT         Assoc Faculty Assoc
    ## 2220                     MOEDERSHEIM,SABINE         Associate Professor
    ## 2221                        MOELLER,KATHRYN         Assistant Professor
    ## 2222                         MOHAMED,MAHA A       Assoc Professor (Chs)
    ## 2223                     MOHAMMADI,ABDOLLAH          Asst Faculty Assoc
    ## 2224                              MOHR,EMMA         Assistant Professor
    ## 2225                            MOK,LUCILLE                    Lecturer
    ## 2226                 MOLFENTER,NANCY FARNON                    Lecturer
    ## 2227                     MOMMAERTS,CORINA D         Assistant Professor
    ## 2228                    MOMONT,HARRY WALTER         Clinical Assoc Prof
    ## 2229                        MONAHAN,LAURA A                    Lecturer
    ## 2230                        MONETTE,RICHARD                   Professor
    ## 2231                     MONIZ,DANTIEL WYNN          Asst Faculty Assoc
    ## 2232                          MONSON,MORGAN              Assoc Lecturer
    ## 2233                       MONTGOMERY,KITTY         Assistant Professor
    ## 2234                     MOONEY,MARGARET E.              Assoc Lecturer
    ## 2235                           MOORE,DARCIE         Assistant Professor
    ## 2236                            MOORE,LUCAS              Assoc Lecturer
    ## 2237                          MOORE,SARAH A         Associate Professor
    ## 2238                        MORALES,ALFONSO                   Professor
    ## 2239                            MOREAU,PAGE                   Professor
    ## 2240                       MORELLO,SAMANTHA         Clinical Assoc Prof
    ## 2241                           MORENO,MARIA           Faculty Associate
    ## 2242                   MORENO,MEGAN ANDREAS                   Professor
    ## 2243                      MORGAN,COURTNEY E        Asst Professor (Chs)
    ## 2244                            MORGAN,DANE                   Professor
    ## 2245                      MORGAN,MICHAEL C.                   Professor
    ## 2246                             MORI,JUNKO                   Professor
    ## 2247                       MORITZ,DEBORAH C             Senior Lecturer
    ## 2248                          MORRIS,JEREMY         Associate Professor
    ## 2249                           MORRIS,MARIO                    Lecturer
    ## 2250                         MORRIS,ZACHARY         Assistant Professor
    ## 2251                  MORRISON,MOSI ADESINA         Assistant Professor
    ## 2252                       MORROW,KATHERINE         Associate Professor
    ## 2253                           MOSER,AMY R.         Associate Professor
    ## 2254                            MOSES,TALLY         Associate Professor
    ## 2255                        MOSHER,DEANE F.                   Professor
    ## 2256                       MOSKOWITZ,MARINA                   Professor
    ## 2257                             MOTT,DAVID                   Professor
    ## 2258   MOUGOUE,JACQUELINE-BETHEL KEUTCHEMEN         Assistant Professor
    ## 2259                     MOUNTAIN,ALEXANDRA              Assoc Lecturer
    ## 2260                            MOWAT,FREYA         Assistant Professor
    ## 2261                 MUEHRER,REBECCA JEANNE         Assistant Professor
    ## 2262                       MUELLER,CARLYN O         Assistant Professor
    ## 2263                MUELLER,KIMBERLY DIGGLE         Assistant Professor
    ## 2264                             MUIR,PETER                   Professor
    ## 2265                        MUKHERJEE,ANITA         Assistant Professor
    ## 2266                        MUKHERJEE,PRIYA         Assistant Professor
    ## 2267                          MUKHIN,DMITRY         Assistant Professor
    ## 2268                           MULLAHY,JOHN                   Professor
    ## 2269                    MULLEN,JESS MATTHEW           Faculty Associate
    ## 2270                    MULLEN,KEVIN GEORGE         Assistant Professor
    ## 2271                       MULVIHILL,JOHN F             Senior Lecturer
    ## 2272                      MUNCHMEYER,MORITZ         Assistant Professor
    ## 2273                    MUNIAGURRIA,MARIA E           Faculty Associate
    ## 2274                    MUNSTERMAN,AMELIA S          Clinical Asst Prof
    ## 2275              MURCHISON,MELANIE JANELLE                    Lecturer
    ## 2276                             MURPHY,JEN                    Lecturer
    ## 2277                            MURPHY,JOHN           Faculty Associate
    ## 2278                    MURPHY,PATRICK ALAN                    Lecturer
    ## 2279                          MURPHY,REGINA                   Professor
    ## 2280                       MURPHY,WILLIAM L                   Professor
    ## 2281                  MURRAY,MICHELLE RENEE              Assoc Lecturer
    ## 2282                          MURRAY,MURRAY           Faculty Associate
    ## 2283                           MURTHY,VIREN         Associate Professor
    ## 2284                        MUSTAFA,MUSTAFA           Faculty Associate
    ## 2285                            MUTLU,BILGE         Associate Professor
    ## 2286                       MUYOLEMA,ARMANDO                    Lecturer
    ## 2287                   MYERS,MARY ELIZABETH             Senior Lecturer
    ## 2288                        MYERSON,REBECCA         Assistant Professor
    ## 2289                    MYRZABEKOVA,RAUSHAN             Senior Lecturer
    ## 2290                  NACEWICZ,BRENDON MARK         Assistant Professor
    ## 2291                             NACK,JAMIE            Sr Outreach Spec
    ## 2292      NACKERS,KIRSTIN ANDREA MUEHLBAUER        Asst Professor (Chs)
    ## 2293                          NADLER,STEVEN                   Professor
    ## 2294                      NAGEL,NICHOLAS J.                    Lecturer
    ## 2295                      NAKADA,STEPHEN Y.                   Professor
    ## 2296                        NAKAKUBO,TAKAKO         Assoc Faculty Assoc
    ## 2297                      NAPARSTEK,MICHAEL                    Lecturer
    ## 2298                  NAPIERALSKI,STEPHANIE              Assoc Lecturer
    ## 2299                         NARDI,HENRIQUE                    Lecturer
    ## 2300                        NATHAN,MITCHELL                   Professor
    ## 2301                   NATHANSON,GILBERT M.                   Professor
    ## 2302                          NAUGHTON,LISA                   Professor
    ## 2303                        NAVSARIA,DIPESH       Assoc Professor (Chs)
    ## 2304                      NAWYN,KIMBERLEE H                    Lecturer
    ## 2305                       NAZAROVA,GULNISA             Senior Lecturer
    ## 2306                        NECKAR,AMANDA L          Asst Faculty Assoc
    ## 2307                             NEGRUT,DAN                   Professor
    ## 2308                 NELLIS,GREGORY FRANCIS                   Professor
    ## 2309                      NELLIS,MARGARET J       Sr Student Serv Coord
    ## 2310                       NELSESTUEN,GRANT         Associate Professor
    ## 2311                            NELSON,ADAM                   Professor
    ## 2312                            NELSON,ADAM                    Lecturer
    ## 2313                         NELSON,CONOR R         Assistant Professor
    ## 2314                           NELSON,DAVID                    Lecturer
    ## 2315                     NELSON,EVAN OTHMER        Asst Professor (Chs)
    ## 2316                    NELSON,GUNTHER PAUL                    Lecturer
    ## 2317                            NELSON,JEFF          Asst Faculty Assoc
    ## 2318                        NELSON,JENNIFER         Assistant Professor
    ## 2319                            NELSON,JOHN           Adjunct Professor
    ## 2320                       NELSON,NICOLE C.         Associate Professor
    ## 2321                           NELSON,SUSAN       Sr Student Serv Coord
    ## 2322                           NELSON,TRACY          Adjunct Instructor
    ## 2323                          NEMET,GREGORY                   Professor
    ## 2324                           NESPER,LARRY                   Professor
    ## 2325                       NESTERCHOUK,ANYA             Senior Lecturer
    ## 2326                      NETT,JENIEL EMILY         Associate Professor
    ## 2327                  NEUHAUSER,HEIDI MARIE         Clinical Instructor
    ## 2328                       NEUMANN,DONNA M.         Associate Professor
    ## 2329                     NEUMAYER,KRISTIN M         Assoc Faculty Assoc
    ## 2330                        NEVILLE,LEONORA                   Professor
    ## 2331                             NEVIN,JACK              Professor Emer
    ## 2332                NEWBURY,SANDRA PATRICIA         Clinical Assoc Prof
    ## 2333                       NEWMAN,TODD PAUL         Assistant Professor
    ## 2334                      NEWMARK,PHILLIP A                   Professor
    ## 2335                        NEWTON,LAURIE A         Clinical Assoc Prof
    ## 2336                      NEWTON,MICHAEL A.                   Professor
    ## 2337                             NEY,DENISE                   Professor
    ## 2338                        NEYRAT,FREDERIC         Associate Professor
    ## 2339                      NGOLA,AMANDA JEAN          Clinical Asst Prof
    ## 2340                    NGUYEN THI,MINHHIEN              Assoc Prof L/I
    ## 2341                            NGUYEN,BETH                   Professor
    ## 2342                             NI,CHAOQUN         Assistant Professor
    ## 2343               NICHELASON,AMY ELIZABETH          Clinical Asst Prof
    ## 2344                       NICHOLS,KATHLEEN         Assoc Faculty Assoc
    ## 2345                     NICKELLS,ROBERT W.                   Professor
    ## 2346                          NICKOLAI,ANNA                    Lecturer
    ## 2347                       NIEDENTHAL,PAULA                   Professor
    ## 2348                         NIENHUIS,JAMES                   Professor
    ## 2349                             NILI,YARON         Assistant Professor
    ## 2350              NIMITYONGSKUL,SONNY AARON         Assoc Faculty Assoc
    ## 2351                          NIMUNKAR,AMIT           Faculty Associate
    ## 2352                           NIWOT,MELODY         Assoc Faculty Assoc
    ## 2353                             NIX,ROBERT         Associate Professor
    ## 2354                        NIZIOLEK,CARRIE         Assistant Professor
    ## 2355                 NOBLES,JENNA ELIZABETH                   Professor
    ## 2356                         NOGUERA,DANIEL                   Professor
    ## 2357                 NORDER-BRANDLI,CHANDRA         Clinical Assoc Prof
    ## 2358                          NORMAN,CORRIE           Faculty Associate
    ## 2359                   NOSEK,JOSEPH MICHAEL           Faculty Associate
    ## 2360                           NOTARO,KELLI          Clinical Asst Prof
    ## 2361                          NOTBOHM,JACOB         Assistant Professor
    ## 2362                     NOWAK,ROBERT DAVID                   Professor
    ## 2363                            NOYCE,DAVID                   Professor
    ## 2364                           NTAMBI,JAMES                   Professor
    ## 2365                         NUCKOLLS,TERRY             Senior Lecturer
    ## 2366                            NYHART,LYNN                   Professor
    ## 2367                          O BRIEN,JERRY           Faculty Associate
    ## 2368                             OAKES,GALE           Faculty Associate
    ## 2369                           OAKLEY,JASON                    Lecturer
    ## 2370                    OAKLEY,LINDA DENISE                   Professor
    ## 2371                         OBERSTAR,ERICK         Assoc Faculty Assoc
    ## 2372                             OBRIEN,ANN                Dis Lecturer
    ## 2373                          OBRIEN,DANA R         Clinical Assoc Prof
    ## 2374                OCALLAGHAN,ELIZABETH M.                    Lecturer
    ## 2375                      OCONNELL,DANIEL M        Asst Professor (Chs)
    ## 2376                         OCONNOR,ANNE M       Assoc Professor (Chs)
    ## 2377                       OCONNOR,DAVID H.                   Professor
    ## 2378                    OCONNOR,SHELBY LYNN         Associate Professor
    ## 2379                          ODEGARD,LYDIA        Assoc Stu Serv Coord
    ## 2380                             ODELL,LUKE              Assoc Lecturer
    ## 2381                         ODORICO,JON S.                   Professor
    ## 2382                        OESTE,ANDREAS A           Adjunct Asst Prof
    ## 2383                            OETZEL,GARY                   Professor
    ## 2384                       OGRAS,UMIT YUSUF         Associate Professor
    ## 2385                        OGUINN,THOMAS C                   Professor
    ## 2386                             OH,EUN SIL         Assistant Professor
    ## 2387                            OH,JUNG SUN             Senior Lecturer
    ## 2388                              OHM,BRIAN                   Professor
    ## 2389                         OHNESORGE,JOHN                   Professor
    ## 2390                         OKONKWO,OZIOMA         Associate Professor
    ## 2391                          OLANIYAN,MOJI            Assistant Dean/M
    ## 2392                      OLDS,KRISTOPHER N                   Professor
    ## 2393                          OLEARY,RENAGH          Clinical Asst Prof
    ## 2394                    OLEINIK,MARK GEORGE           Adjunct Professor
    ## 2395                            OLIVE,PEGGY            Sr Outreach Spec
    ## 2396                       OLIVER,PAMELA E.                   Professor
    ## 2397                        OLIVER,THOMAS R                   Professor
    ## 2398                    OLLIVETT,TERRI LYNN         Assistant Professor
    ## 2399                    OLSEN,CHRISTOPHER W              Professor Emer
    ## 2400                          OLSON,CHRISTA         Associate Professor
    ## 2401                          OLSON,JOHN L.  Clinical Adjunct Professor
    ## 2402                         OLSON,LEAH JOY              Assoc Prof L/I
    ## 2403                             OLSON,MARK           Faculty Associate
    ## 2404                            OLSON,TRENT                    Lecturer
    ## 2405                          OLSZEWSKI,DAN           Faculty Associate
    ## 2406                      ONELLION,MARSHALL                   Professor
    ## 2407                      ONG,IRENE MAY LIN         Assistant Professor
    ## 2408                      OOSTERWYK,JOHANNA           Faculty Associate
    ## 2409                           ORLOV,DMITRY         Assistant Professor
    ## 2410                          OROURKE,ANN P       Assoc Professor (Chs)
    ## 2411                   OROURKE,BERNADETT M.            Sr Outreach Spec
    ## 2412                              ORR,SARAH          Clinical Professor
    ## 2413                          ORROCK,JOHN L                   Professor
    ## 2414                     ORTIZ-ROBLES,MARIO                   Professor
    ## 2415                      OSBORNE,CHARLES A          Clinical Asst Prof
    ## 2416                    OSORIO,JORGE EMILIO                   Professor
    ## 2417                         OSPOVAT,KIRILL         Assistant Professor
    ## 2418                   OSSORIO,PILAR NICOLE                   Professor
    ## 2419                            OSSWALD,TIM                   Professor
    ## 2420                          OTEGUI,MARISA                   Professor
    ## 2421                      OTEPKA,CARRIE ANN          Clinical Asst Prof
    ## 2422                          OTTMANN,SUSAN           Faculty Associate
    ## 2423                             OTTO,MARIO         Associate Professor
    ## 2424                           OTTO,STACY B         Clinical Instructor
    ## 2425                   OUAYOGODE,MARIETOU H         Assistant Professor
    ## 2426                           OW,TERENCE T         Visiting Assoc Prof
    ## 2427                  OWENBY,THOMAS CLINTON           Faculty Associate
    ## 2428                             OWENS,RYAN                   Professor
    ## 2429              OWUSU-YEBOA,LATISH CHERIE                    Lecturer
    ## 2430                          OZDOGAN,MUTLU         Associate Professor
    ## 2431                            PAC,GREGORY             Senior Lecturer
    ## 2432                            PAC,JESSICA         Assistant Professor
    ## 2433                        PACHECO,MARIANA         Associate Professor
    ## 2434                          PADILLA,DARCY         Associate Professor
    ## 2435                       PAGE JR.,C DAVID                   Professor
    ## 2436                        PAGEL,HOLLY RAE         Assoc Faculty Assoc
    ## 2437                        PAGLIARINI,DAVE         Assistant Professor
    ## 2438                        PAKER,BULENT S.          Clinical Professor
    ## 2439                    PAKES AHLMAN,ANGELA                  Researcher
    ## 2440                           PALECEK,SEAN                   Professor
    ## 2441                  PALLADINO,KIMBERLY J.         Assistant Professor
    ## 2442                   PALMENBERG,ANN CAROL                   Professor
    ## 2443                 PALMER,KASSANDRA BOEHM                    Lecturer
    ## 2444                         PALMER,LINDSAY         Associate Professor
    ## 2445                   PALMER,MARISA MACKEY             Senior Lecturer
    ## 2446                       PALMQUIST,RUTH A             Senior Lecturer
    ## 2447                            PALTA,JIWAN                   Professor
    ## 2448                            PAN,WENXIAO         Assistant Professor
    ## 2449                               PAN,XUAN         Associate Professor
    ## 2450                             PAN,XUEJUN                   Professor
    ## 2451                              PAN,YIBIN         Associate Professor
    ## 2452                          PAN,ZHONGDANG                   Professor
    ## 2453                         PANDEY,NANDINI         Associate Professor
    ## 2454                  PANKOW,BENJAMIN JACOB        Asst Prof Of Mil Sci
    ## 2455                        PANZER,SARAH E.         Assistant Professor
    ## 2456                PAPAILIOPOULOS,DIMITRIS         Assistant Professor
    ## 2457                            PAPE,LOUISE            Senior Scientist
    ## 2458                            PAPP,LAUREN                   Professor
    ## 2459                        PARETSKAYA,ANNA                    Lecturer
    ## 2460                             PARINS,AMY          Clinical Asst Prof
    ## 2461                        PARISI,GIUSTINA                    Lecturer
    ## 2462                               PARK,JIM                   Professor
    ## 2463                         PARKER,DOMINIC         Associate Professor
    ## 2464                            PARKER,JEFF         Assistant Professor
    ## 2465                         PARKIN,KIRK L.              Professor Emer
    ## 2466                            PARKS,BRIAN         Assistant Professor
    ## 2467               PARRA-MONTESINOS,GUSTAVO                   Professor
    ## 2468                            PARRELL,BEN         Assistant Professor
    ## 2469                        PARRISH,JOHN J.                   Professor
    ## 2470                        PASKEWITZ,SUSAN                   Professor
    ## 2471                      PATANKAR,MANISH S                   Professor
    ## 2472                             PATEL,GINA          Adjunct Assoc Prof
    ## 2473                 PATEL,JIGNESH MANUBHAI                   Professor
    ## 2474                            PATEL,VIVAK         Assistant Professor
    ## 2475                        PATENAUDE,LOUKA                    Lecturer
    ## 2476                      PATTNAIK,BIKASH R         Assistant Professor
    ## 2477                            PATZ,JEAN A                    Lecturer
    ## 2478                          PATZ,JONATHAN                   Professor
    ## 2479                            PAUL,SEAN T                   Professor
    ## 2480                          PAULEY,GWYN C              Assoc Lecturer
    ## 2481                           PAULI,DENNIS                    Lecturer
    ## 2482                         PAULI,JONATHAN         Associate Professor
    ## 2483                           PAULSEN,KURT                   Professor
    ## 2484                       PAUSTIAN,TIMOTHY       Dis Faculty Associate
    ## 2485                           PAVEK, KATIE         Clinical Instructor
    ## 2486                    PAWLAK,ROBERTA PAGE          Clinical Professor
    ## 2487                           PAYSEUR,BRET                   Professor
    ## 2488                            PAZICNI,SAM         Assistant Professor
    ## 2489                    PEARCE,ROBERT ALLEN                   Professor
    ## 2490                          PEARSON,ALICE         Clinical Assoc Prof
    ## 2491                        PECANAC,KRISTEN         Assistant Professor
    ## 2492                        PECARINA,JOHN M        Professor Of Mil Sci
    ## 2493                             PECK,JOANN         Associate Professor
    ## 2494                        PEDERSEN,JOEL A                   Professor
    ## 2495              PEDRIANA,NICHOLAS ANTHONY             Senior Lecturer
    ## 2496                        PEEBLES,PATRICK          Clinical Asst Prof
    ## 2497                            PEEK,AUDREY                    Lecturer
    ## 2498                          PEEK,SIMON F.          Clinical Professor
    ## 2499                                PEERY,M                   Professor
    ## 2500                        PEHAR,MARIANA A         Assistant Professor
    ## 2501                    PELEGRI,FRANCISCO J                   Professor
    ## 2502                     PELLEGRINI,MARCELO         Associate Professor
    ## 2503                        PELLETIER,DAVID                    Lecturer
    ## 2504                 PELLIN,MACKENZIE ARLAH          Clinical Asst Prof
    ## 2505                 PENAGARICANO,FRANCISCO         Assistant Professor
    ## 2506                                PENG,XU                    Lecturer
    ## 2507                              PENG,ZHAO              Assoc Lecturer
    ## 2508                         PENNELLA,MARIO         Assoc Faculty Assoc
    ## 2509                        PEPPARD,PAUL E.                   Professor
    ## 2510                    PEPPERELL,CAITLIN S         Associate Professor
    ## 2511                         PEREPEZKO,JOHN                   Professor
    ## 2512                         PERGAMENT,ADAM             Senior Lecturer
    ## 2513                        PERNA,NICOLE T.                   Professor
    ## 2514                            PERRY,DAVID                   Professor
    ## 2515                      PERSIKE,CONSTANCE         Clinical Assoc Prof
    ## 2516                      PESAVENTO,THERESA                    Lecturer
    ## 2517                           PETER,KIRK A           Faculty Associate
    ## 2518                        PETERS,DONNA M.                   Professor
    ## 2519                         PETERS,JASON M         Assistant Professor
    ## 2520                        PETERS,SHANAN E                   Professor
    ## 2521               PETERSON,AMY LYNN HERING       Assoc Professor (Chs)
    ## 2522                           PETERSON,KIM             Senior Lecturer
    ## 2523                       PETERSON,MICHAEL                   Professor
    ## 2524                       PETERSON,SANDY K              Assoc Lecturer
    ## 2525                       PETTERSEN,CLAIRE              Assoc Lecturer
    ## 2526                  PETTY,ELIZABETH MARIE                   Professor
    ## 2527                          PETTY,GRANT W                   Professor
    ## 2528                          PEVEHOUSE,JON                   Professor
    ## 2529                 PEYER,SUZANNE MICHELLE              Assoc Lecturer
    ## 2530                      PFEFFERKORN,FRANK                   Professor
    ## 2531                          PFLEGER,BRIAN                   Professor
    ## 2532                         PFLUM,MADELINE              Assoc Lecturer
    ## 2533                       PFOTENHAUER,JOHN                   Professor
    ## 2534                         PHANEUF,DANIEL                   Professor
    ## 2535                          PHELPS,ALYSSA                    Lecturer
    ## 2536                  PHELPS,KATHERINE ANNE                    Lecturer
    ## 2537                  PHILLIPPI,ERIC THOMAS  Clinical Adjunct Asst Prof
    ## 2538                          PHILLIPS,GENE                   Professor
    ## 2539                     PHILLIPS,MEGAN ANN          Adjunct Instructor
    ## 2540                 PHILLIPS-COURT,KRISTIN         Associate Professor
    ## 2541                 PICASSO RISSO,VALENTIN         Assistant Professor
    ## 2542               PICCIONE,MICHELLE LAUREN         Clinical Instructor
    ## 2543                 PICKERING,TRAVIS RAYNE                   Professor
    ## 2544                            PICKETT,DAN             Senior Lecturer
    ## 2545                 PICKETT,KRISTEN ALEXIS         Assistant Professor
    ## 2546                           PIDGEON,ANNA                   Professor
    ## 2547                           PIERCE,DEBRA           Faculty Associate
    ## 2548                  PIERCE,ROBERT BRADLEY                   Professor
    ## 2549                    PIERCE,TIMOTHY JOHN          Adjunct Instructor
    ## 2550                          PIKE,J WESLEY                   Professor
    ## 2551                    PILIAVIN,JANE ALLYN              Professor Emer
    ## 2552                     PILLAI,PARVATHY T.        Asst Professor (Chs)
    ## 2553                PIMENTEL ALARCON,DANIEL         Assistant Professor
    ## 2554                             PINC,GUZZO                    Lecturer
    ## 2555                       PINCHEIRA,JOSE A         Associate Professor
    ## 2556                   PINEKENSTEIN,BARBARA          Clinical Professor
    ## 2557                      PINKERTON,MARIE E         Clinical Assoc Prof
    ## 2558                     PIRE,TIMOTHY JAMES                    Lecturer
    ## 2559                       PITT,MECHELE LEE                    Lecturer
    ## 2560                       PITTERLE,MICHAEL       Assoc Professor (Chs)
    ## 2561                    PLANTE,DAVID THOMAS         Assistant Professor
    ## 2562                       PLANTE,SEBASTIEN         Assistant Professor
    ## 2563                        PLANTS,JENNIFER           Faculty Associate
    ## 2564                         PLUMMER,BRENDA                   Professor
    ## 2565                            POE,CYNTHIA         Assoc Faculty Assoc
    ## 2566                     POE-GAVLINSKI,RYAN         Clinical Instructor
    ## 2567                   POEHLMANN,JULIE ANNE                   Professor
    ## 2568                          POINTON,LUCAS                    Lecturer
    ## 2569                   POLFUSS,MICHELE LYNN           Faculty Associate
    ## 2570                            POLLAK,SETH                   Professor
    ## 2571                            POLMAN,EVAN         Associate Professor
    ## 2572                     POLTORATSKI,ALEXEI                   Professor
    ## 2573                           POMPEY,COREY         Assoc Faculty Assoc
    ## 2574                    PONIK,SUZANNE MARIE         Assistant Professor
    ## 2575                            PONTO,KEVIN         Associate Professor
    ## 2576                            POOL,JOHN E         Associate Professor
    ## 2577                         POORE,SAMUEL O         Associate Professor
    ## 2578                       POPKEWITZ,THOMAS                   Professor
    ## 2579                        POPULIN,LUIS C.                   Professor
    ## 2580                          PORTER,ANDREA       Assoc Professor (Chs)
    ## 2581                      PORTER,JACK R. II                   Professor
    ## 2582                      PORTILLO,EDWARD C        Asst Professor (Chs)
    ## 2583                           POSEN,HART E                   Professor
    ## 2584                      POSEY-MADDOX,LINN         Associate Professor
    ## 2585                            POSTLE,BRAD                   Professor
    ## 2586                     POTTER,HEATHER A D       Assoc Professor (Chs)
    ## 2587                         POTTER,KENNETH                   Professor
    ## 2588                          POULOS,ANDREA           Faculty Associate
    ## 2589                   POULSEN,KEITH PAPPAS         Clinical Assoc Prof
    ## 2590                         POWELL,ELEANOR         Associate Professor
    ## 2591                         POWELL,LINDSEY          Adjunct Instructor
    ## 2592                          POWERS,ALEXIS         Clinical Instructor
    ## 2593                       PRABHAKAR,PAVANA         Assistant Professor
    ## 2594                      PRABHAKARAN,VIVEK         Associate Professor
    ## 2595                         PRASCH,ALLISON         Assistant Professor
    ## 2596                             PREM,KATHY         Assoc Faculty Assoc
    ## 2597                         PRESTON,DANIEL         Assistant Professor
    ## 2598                            PRICE,BRIAN           Adjunct Asst Prof
    ## 2599                         PRIMM,STEFANIE          Asst Faculty Assoc
    ## 2600                           PRIMUS,ROY J           Adjunct Asst Prof
    ## 2601                           PRINGLE,ANNE                   Professor
    ## 2602                      PRITCHARD,JESSICA          Clinical Asst Prof
    ## 2603                   PROLLA,TOMAS ALBERTO                   Professor
    ## 2604                            PROST,LYNNE           Faculty Associate
    ## 2605                        PROVENCHER,BILL                   Professor
    ## 2606                        PRUITT,JENNIFER         Associate Professor
    ## 2607                             PRYDE,EMMA                    Lecturer
    ## 2608                   PUCCINELLI,JOHN PAUL           Faculty Associate
    ## 2609                  PUCCINELLI,TRACY JANE         Assoc Faculty Assoc
    ## 2610                        PUGLIELLI,LUIGI                   Professor
    ## 2611                          PUJARA,NIMISH         Assistant Professor
    ## 2612                              PUJOL,EVE           Faculty Associate
    ## 2613                  PULIA,MICHAEL SANTINO         Assistant Professor
    ## 2614                           PULIA,NICOLE         Assistant Professor
    ## 2615                  PULTORAK,JOSHUA DAVID           Faculty Associate
    ## 2616                         PULTORAK,SARAH           Faculty Associate
    ## 2617                    PUNTAMBEKAR,SADHANA                   Professor
    ## 2618                          PURDUE,EUGENE           Faculty Associate
    ## 2619                            PURNELL,TOM                   Professor
    ## 2620                   PUSTEJOVSKY,JAMES E.         Associate Professor
    ## 2621                       PUTNAM,WILLIAM C          Visiting Professor
    ## 2622                          QIAN,XIAOPING                   Professor
    ## 2623                              QIN,MOHAN         Assistant Professor
    ## 2624                      QUAGLIANA,CHARLES           Adjunct Professor
    ## 2625                        QUANBECK,ANDREW         Assistant Professor
    ## 2626                        QUARLES,BRANDON              Assoc Lecturer
    ## 2627                      QUILLEN,CAITLIN M                    Lecturer
    ## 2628                      QUINN,DAVEN PATEL              Assoc Lecturer
    ## 2629                         QUINN,MICHELLE          Clinical Professor
    ## 2630                              QUINT,DAN         Associate Professor
    ## 2631                         QUINTANA,STEVE                   Professor
    ## 2632                          QUINTIN,ERWAN                   Professor
    ## 2633                  QURAISHI-LANDES,ASIFA                   Professor
    ## 2634                       QURESHI,ARIF ALI             Senior Lecturer
    ## 2635                          RACETTE,MOLLY          Clinical Asst Prof
    ## 2636          RACINE GILLES,CAROLINE NICOLE         Assoc Faculty Assoc
    ## 2637                        RADELOFF,VOLKER                   Professor
    ## 2638                          RADWIN,ROBERT                   Professor
    ## 2639                              RAE,JULIE          Admin Program Spec
    ## 2640                     RAHOI,DANE MICHAEL         Clinical Instructor
    ## 2641                       RAIFE,THOMAS JAY             Professor (Chs)
    ## 2642                     RAIMBEKOVA,LOLAGUL                    Lecturer
    ## 2643                             RAIMY,ERIC                   Professor
    ## 2644                         RAISON,CHARLES                   Professor
    ## 2645                 RAKOTONDRAFARA,AURELIE         Associate Professor
    ## 2646                     RALPHE,JOHN CARTER         Associate Professor
    ## 2647                           RAMAN,VATSAN         Assistant Professor
    ## 2648                     RAMANATHAN,PARMESH                   Professor
    ## 2649                RAMBERG,ERICA ELIZABETH         Assoc Faculty Assoc
    ## 2650           RAMIREZ TAHUADO,MARLA ANDREA         Assistant Professor
    ## 2651                       RAMIREZ,ALYSSA M          Clinical Asst Prof
    ## 2652                           RAMLY,EDMOND         Assistant Professor
    ## 2653                         RAMOS,MICHELLE              Assoc Lecturer
    ## 2654                                RAN,BIN                   Professor
    ## 2655                          RANADE,MILIND             Senior Lecturer
    ## 2656                   RANALLO,FRANK NUNZIO             Professor (Chs)
    ## 2657                           RANHEIM,ERIK             Professor (Chs)
    ## 2658                             RANK,DAVID          Adjunct Assoc Prof
    ## 2659                         RANKIN,SCOTT A                   Professor
    ## 2660                            RAO,LUDMILA             Senior Lecturer
    ## 2661                            RAO,RAJIV G         Associate Professor
    ## 2662                      RASCHKA,SEBASTIAN         Assistant Professor
    ## 2663                       RASKUTTI,GARVESH         Associate Professor
    ## 2664                        RATLIFF,CAMERON         Clinical Instructor
    ## 2665                        RATNER,JENNIFER                   Professor
    ## 2666                 RATTERMAN,DENISE MARIE           Faculty Associate
    ## 2667                            RAU,MARTINA         Associate Professor
    ## 2668                            RAVAL,AMISH         Associate Professor
    ## 2669                           RAYMENT,IVAN                   Professor
    ## 2670                 REARDON,CLAUDIA LOUISE       Assoc Professor (Chs)
    ## 2671                            REARDON,JIM           Faculty Associate
    ## 2672                            REBEL,BRIAN         Associate Professor
    ## 2673                    REBOUCAS DOREA,JOAO         Assistant Professor
    ## 2674                              RECK,TODD                    Lecturer
    ## 2675                    RECORD JR.,M THOMAS                   Professor
    ## 2676               RED EAGLE,LAURA CANDIDIA              Assoc Lecturer
    ## 2677                REDFIELD III,ROBERT RAY       Honorary Assoc/Fellow
    ## 2678                          REED,JENNIFER                   Professor
    ## 2679                           REED,JESS D.                   Professor
    ## 2680                         REEDER,SCOTT B                   Professor
    ## 2681                          REESE,WILLIAM                   Professor
    ## 2682                      REILLY,MEGAN MARY         Assistant Professor
    ## 2683                         REINDL,DOUGLAS                   Professor
    ## 2684                         REINEMANN,DOUG                   Professor
    ## 2685                    REINFELDT,DIANE LOU         Clinical Assoc Prof
    ## 2686                       REINHOLTZ,RHONDA             Senior Lecturer
    ## 2687                       REISER,CATHERINE             Professor (Chs)
    ## 2688                   REKATSINAS,THEODOROS         Assistant Professor
    ## 2689                          REMALIA,MAREE              Assoc Lecturer
    ## 2690             REMINGTON,PATRICK LHEUREUX              Professor Emer
    ## 2691                 REMOND-TIEDREZ,ANTOINE          Visiting Asst Prof
    ## 2692                        REMUCAL,CHRISTY         Associate Professor
    ## 2693                           RENAULT,MARC          Asst Faculty Assoc
    ## 2694                       RENSHON,JONATHAN         Associate Professor
    ## 2695                              RENZ,MARK                   Professor
    ## 2696                            REPS,THOMAS                   Professor
    ## 2697                       RESNICK,DANIEL K                   Professor
    ## 2698                           REY,FEDERICO         Associate Professor
    ## 2699                          REYES,LETICIA         Assistant Professor
    ## 2700                        REYNOLDS,ANDREW         Associate Professor
    ## 2701                    REYNOLDS,MATTHEW R.         Assistant Professor
    ## 2702                                RHA,EUN              Assoc Lecturer
    ## 2703                        RHODES,DANIEL A         Assistant Professor
    ## 2704                        RICE,GREGORY M.       Assoc Professor (Chs)
    ## 2705                            RICE,JOHN P       Assoc Professor (Chs)
    ## 2706                      RICH,WALTER HENRY           Faculty Associate
    ## 2707                          RICHARDS,CATE                    Lecturer
    ## 2708                        RICHARDS,MARK P                   Professor
    ## 2709                      RICHARDSON,ANGELA         Assoc Faculty Assoc
    ## 2710                          RICHERT,LUCAS         Associate Professor
    ## 2711                      RICHMAN,MICHAEL P          Adjunct Instructor
    ## 2712                    RICK,STEVEN WILLIAM             Senior Lecturer
    ## 2713                        RICKE,STEVEN C.                   Professor
    ## 2714                             RICKE,WILL                   Professor
    ## 2715                        RICKENBACH,MARK                   Professor
    ## 2716                      RIDDIOUGH,TIMOTHY                   Professor
    ## 2717                           RIDDLE,KARYN                   Professor
    ## 2718                            RIDER,ROBIN             Senior Lecturer
    ## 2719                          RIDGELY,STEVE         Associate Professor
    ## 2720                       RIDGELY,SUSAN B.                   Professor
    ## 2721                        RIENSTRA,CHAD M                   Professor
    ## 2722                         RIGBY,BRITTNEY         Clinical Instructor
    ## 2723                   RILEY,CARRIE JACKSON           Faculty Associate
    ## 2724                    RINDFLEISCH,JAMES A       Honorary Assoc/Fellow
    ## 2725                             RINGE,NILS                   Professor
    ## 2726                  RINGLER,TAMSIE LOUISE                    Lecturer
    ## 2727                   RINGLER,THOR STEPHEN  Clinical Adjunct Asst Prof
    ## 2728                           RIOS,SARAH M         Assistant Professor
    ## 2729                    RIOUX,RENEE ARIELLE         Assistant Professor
    ## 2730                          RISSMAN,ADENA                   Professor
    ## 2731                          RITERS,LAUREN                   Professor
    ## 2732                           ROALD,LINE A         Assistant Professor
    ## 2733                        ROBATTO,ROBERTO         Assistant Professor
    ## 2734                        ROBB,CLIFFORD A         Associate Professor
    ## 2735                           ROBBINS,PAUL                   Professor
    ## 2736                       ROBERT,STEPHANIE                   Professor
    ## 2737                      ROBERTS,ELIZABETH         Clinical Instructor
    ## 2738                    ROBERTS,MARY LOUISE                   Professor
    ## 2739                          ROBERTS,TONYA         Assistant Professor
    ## 2740                  ROBERTSON SMITH,AMBER         Assoc Faculty Assoc
    ## 2741                      ROBERTSON,GAIL A.                   Professor
    ## 2742                       ROBERTSON,MORGAN                   Professor
    ## 2743               ROBINSON,STEPHEN MICHAEL              Professor Emer
    ## 2744                         ROBINSON,SUSAN                   Professor
    ## 2745                         ROCH,SEBASTIEN                   Professor
    ## 2746                          ROCK,AARON W.         Assistant Professor
    ## 2747                    ROCK,MICHAEL JOSEPH             Professor (Chs)
    ## 2748                       ROCK-SINGER,CARA         Assistant Professor
    ## 2749                             RODEN,ERIC                   Professor
    ## 2750                       RODGERS,LENNON P                    Lecturer
    ## 2751                  RODRIGUEZ GOMEZ,DIANA         Assistant Professor
    ## 2752                  RODRIGUEZ,JOSE ISRAEL         Assistant Professor
    ## 2753               RODRIGUEZ-GURIDI,BARBARA         Assoc Faculty Assoc
    ## 2754                          ROESSLER,JEFF             Senior Lecturer
    ## 2755                          ROGERS,JEREMY         Assistant Professor
    ## 2756                            ROGERS,JOEL                   Professor
    ## 2757                 ROGERS,KAYCEE DANIELLE           Faculty Associate
    ## 2758                       ROGERS,TIMOTHY T                   Professor
    ## 2759                              ROHE,KARL         Associate Professor
    ## 2760                         ROJAS,HERNANDO                   Professor
    ## 2761                       ROLDAN,ALEJANDRO         Assistant Professor
    ## 2762                               ROLL,JON           Faculty Associate
    ## 2763                          ROMAN,DIEGO X         Assistant Professor
    ## 2764                         ROMBACH,NICOLE                    Lecturer
    ## 2765                  ROMERO ARVELO,EDUARDO          Asst Faculty Assoc
    ## 2766                          ROMERO,PHILIP         Assistant Professor
    ## 2767                 ROMMELFAENGER,MARIJO A         Dis Professor (Chs)
    ## 2768                               RON,AMOS                   Professor
    ## 2769                        RONDON,MICHELLE           Faculty Associate
    ## 2770                            RONIS,DAVID         Assistant Professor
    ## 2771                       RONK,ERIC THOMAS          Asst Faculty Assoc
    ## 2772           RONNEKLEIV-KELLY,SEAN MARTIN         Assistant Professor
    ## 2773                       ROONEY,FRANCIS J         Assoc Faculty Assoc
    ## 2774                         ROOPRA,AVTAR S         Associate Professor
    ## 2775                          ROOS,LIINA-LY         Assistant Professor
    ## 2776                          ROOT,THATCHER                   Professor
    ## 2777                      ROS,ALEJANDRA ROS         Assistant Professor
    ## 2778          ROSA,GUILHERME J DE MAGALHAES                   Professor
    ## 2779                           ROSA,KATHY S                    Lecturer
    ## 2780              ROSADO-MENDEZ,IVAN MIGUEL         Assistant Professor
    ## 2781                            ROSE,WARREN         Associate Professor
    ## 2782                         ROSE,WILLIAM N       Assoc Professor (Chs)
    ## 2783                        ROSEN,ELIZABETH         Assoc Faculty Assoc
    ## 2784                          ROSENBERG,ARI         Assistant Professor
    ## 2785                      ROSENBERG,DOUGLAS                   Professor
    ## 2786                       ROSENBERG,MARGIE                   Professor
    ## 2787                       ROSENBLUM,JORDAN                   Professor
    ## 2788                      ROSENHAGEN,ULRICH           Faculty Associate
    ## 2789                ROSENKRANZ,MELISSA ANNE         Assistant Professor
    ## 2790                        ROSENTHAL,DAVID                   Professor
    ## 2791                           ROSIN,COOPER              Assoc Lecturer
    ## 2792                              ROSS,JEFF              Professor Emer
    ## 2793                       ROSTEK,MARZENA J                   Professor
    ## 2794                     ROTH,JOSHUA DANIEL         Assistant Professor
    ## 2795                     ROTH,ROBERT EMMETT         Associate Professor
    ## 2796                         ROTHAMER,DAVID                   Professor
    ## 2797                        ROTTMAYER,JULIA           Faculty Associate
    ## 2798                        ROTZENBERG,KATE         Assoc Faculty Assoc
    ## 2799                          ROUSE,DOUGLAS                   Professor
    ## 2800                            ROWE,ANGELA         Assistant Professor
    ## 2801                              ROWE,PAUL                   Professor
    ## 2802                ROWELL,TAWANDRA LASHONE         Assistant Professor
    ## 2803                           ROY,SUSHMITA         Associate Professor
    ## 2804                    ROYSTON,REGINOLD A.         Assistant Professor
    ## 2805                          RUARK,MATTHEW                   Professor
    ## 2806                             RUBEL,ALAN         Associate Professor
    ## 2807                         RUBIN,ANDREW M                    Lecturer
    ## 2808                         RUBIN,JENNIFER                    Lecturer
    ## 2809                           RUDOLPH,JOHN                   Professor
    ## 2810                        RUDRARAJU,SHIVA         Assistant Professor
    ## 2811                         RUDYKH,STEPHAN         Assistant Professor
    ## 2812                               RUE,ANNA          Asst Faculty Assoc
    ## 2813                               RUHL,KIM         Associate Professor
    ## 2814                              RUI,LIXIN         Associate Professor
    ## 2815                         RUMBLE,PATRICK                   Professor
    ## 2816                             RUNGE,TROY                   Professor
    ## 2817                          RUPPAR,ANDREA         Associate Professor
    ## 2818                          RUSS,ROSEMARY         Associate Professor
    ## 2819                     RUSSELL,JEFFREY S.                   Professor
    ## 2820                  RUSSELL,TIMOTHY JAMES              Assoc Lecturer
    ## 2821                         RUTECKI,TERESA                    Lecturer
    ## 2822                      RUTHERFORD,THOMAS                   Professor
    ## 2823                             RYFF,CAROL                   Professor
    ## 2824                        RYLANDER,HELENA         Clinical Assoc Prof
    ## 2825                         RZCHOWSKI,MARK                   Professor
    ## 2826                       SAALMANN,YURI B.         Associate Professor
    ## 2827                          SAATCHI,AHMAD           Faculty Associate
    ## 2828 SABAAALAZAB,MARIAM MOHAMED ALY NASHAAT                    Lecturer
    ## 2829                           SAFDAR,NASIA                   Professor
    ## 2830                           SAFFMAN,MARK                   Professor
    ## 2831                          SAFFRAN,JENNY                   Professor
    ## 2832                          SAGE,ADRIANNA          Clinical Asst Prof
    ## 2833                           SAGER,LESLEY         Assoc Faculty Assoc
    ## 2834                          SAHA,KRISHANU         Associate Professor
    ## 2835                              SALA,FRED         Assistant Professor
    ## 2836                        SALADAR,TRACY E         Clinical Assoc Prof
    ## 2837                       SALAMAT,SHAHRIAR             Professor (Chs)
    ## 2838                  SALGADO PABON,WILMARA         Assistant Professor
    ## 2839                            SALMONS,JOE                   Professor
    ## 2840                          SALO,DOROTHEA       Dis Faculty Associate
    ## 2841                     SALZMAN,TINA MARIE          Clinical Professor
    ## 2842                       SAMANTA,JAYSHREE         Assistant Professor
    ## 2843                       SAMPENE,EMMANUEL                    Lecturer
    ## 2844                        SAMPLE,SUSANNAH         Assistant Professor
    ## 2845               SANCHEZ,KATHRYN MARGARET                   Professor
    ## 2846                          SANDBO,NATHAN         Associate Professor
    ## 2847                          SANDERS,SCOTT                   Professor
    ## 2848                     SANDGREN,ERIC PAUL                   Professor
    ## 2849                     SANDLER,RICKY CHAD                    Lecturer
    ## 2850                          SANDOCK,SARAH           Adjunct Asst Prof
    ## 2851                          SANDOR,MATYAS                   Professor
    ## 2852                          SANFORD,GREGG             Senior Lecturer
    ## 2853                     SANKARALINGAM,KARU                   Professor
    ## 2854                        SANKARAN,KRIS R         Assistant Professor
    ## 2855                       SANMIGUEL,JOSHUA         Assistant Professor
    ## 2856                             SANS,ORIOL         Assistant Professor
    ## 2857                      SANTIAGO,KELVIN R         Assoc Faculty Assoc
    ## 2858                        SAPEGA,ELLEN W.                   Professor
    ## 2859                               SARADA,-         Assistant Professor
    ## 2860                             SARFF,JOHN                   Professor
    ## 2861                       SARLIOGLU,BULENT         Associate Professor
    ## 2862                          SARMADI,MAJID                   Professor
    ## 2863                     SARMIENTO,CAROLINA         Assistant Professor
    ## 2864                          SAUER,HEATHER                    Lecturer
    ## 2865                               SAUER,JD         Associate Professor
    ## 2866                        SAVER,ALEXANDER         Clinical Instructor
    ## 2867                       SCHACHTER,PARTHY             Senior Lecturer
    ## 2868                SCHAEFER,DANIEL MEILAHN                   Professor
    ## 2869                         SCHAEFER,SUSAN         Clinical Assoc Prof
    ## 2870                            SCHALK,SAMI         Associate Professor
    ## 2871                     SCHARDT,DANA ELYSE         Clinical Assoc Prof
    ## 2872                      SCHARRER,JONATHAN          Clinical Asst Prof
    ## 2873                         SCHATZKE,KYOKO         Clinical Instructor
    ## 2874                      SCHAUB,ANNA MARIE         Clinical Instructor
    ## 2875                          SCHAUER,JAMES                   Professor
    ## 2876         SCHAUMBERG,KATHERINE ELIZABETH        Asst Professor (Chs)
    ## 2877                        SCHECHTER,LAURA                   Professor
    ## 2878                        SCHECHTMAN,ANAT         Associate Professor
    ## 2879                          SCHEELE,CHRIS                    Lecturer
    ## 2880                          SCHEER,ELAINE                   Professor
    ## 2881                     SCHEND,VALERIE ANN         Clinical Instructor
    ## 2882                      SCHEUFELE,DIETRAM                   Professor
    ## 2883                       SCHIEKE,STEFAN M        Asst Professor (Chs)
    ## 2884                          SCHIFERL,RICH           Adjunct Asst Prof
    ## 2885                          SCHLOSS,KAREN         Assistant Professor
    ## 2886                  SCHMIDT,CALICO ESTHER         Clinical Instructor
    ## 2887                           SCHMIDT,J.R.                   Professor
    ## 2888                 SCHMIDT,JEFFREY ROBERT           Faculty Associate
    ## 2889                      SCHMIDT,JESSICA N        Asst Professor (Chs)
    ## 2890                           SCHMIDT,NETE           Faculty Associate
    ## 2891                          SCHMIDT,SILKE              Assoc Lecturer
    ## 2892                 SCHMIEDICKE,DAVID PAUL          Adjunct Assoc Prof
    ## 2893                            SCHMIT,JOAN                   Professor
    ## 2894                            SCHMITZ,AMY              Assoc Lecturer
    ## 2895                       SCHMITZ,LAUREN L         Assistant Professor
    ## 2896                SCHMITZ,NATALIE SUZANNE        Asst Professor (Chs)
    ## 2897                         SCHMITZ,OLIVER                   Professor
    ## 2898               SCHMITZ-SIEBERTZ,VANESSA              Assoc Lecturer
    ## 2899                    SCHNEIDER,ANNEMARIE         Associate Professor
    ## 2900                      SCHNEIDER,DAVID F         Assistant Professor
    ## 2901                            SCHNELL,LIZ         Clinical Assoc Prof
    ## 2902                       SCHNUR,ROBERT A.          Adjunct Instructor
    ## 2903                   SCHOMAKER,JENNIFER M                   Professor
    ## 2904              SCHONBERG,CHRISTINA CAROL                    Lecturer
    ## 2905                          SCHOOHS,SHARI                    Lecturer
    ## 2906                         SCHOVILLE,SEAN         Associate Professor
    ## 2907                   SCHRAGE,WILLIAM GREG                   Professor
    ## 2908                        SCHREIER,MARCEL         Assistant Professor
    ## 2909                       SCHRODI,STEVEN J         Assistant Professor
    ## 2910                   SCHROEDER,CARRIE ANN          Clinical Asst Prof
    ## 2911                         SCHROEDER,GREG             Senior Lecturer
    ## 2912                       SCHROEDER,SISSEL                   Professor
    ## 2913                       SCHROEPFER,TRACY                   Professor
    ## 2914                           SCHUBERT,AMY           Faculty Associate
    ## 2915                  SCHUCHARDT,ERIC JAMES         Assoc Faculty Assoc
    ## 2916                     SCHUCHARDT,MAKAYLA         Assoc Faculty Assoc
    ## 2917                         SCHUELKE,SHANE        Asst Prof Of Mil Sci
    ## 2918                       SCHUELLER,JEANNE           Faculty Associate
    ## 2919                       SCHULDIES,JAKE M              Assoc Lecturer
    ## 2920                        SCHULFER,NATHAN           Faculty Associate
    ## 2921                            SCHULTZ,AMY              Assoc Lecturer
    ## 2922                 SCHULTZ,KELLY KATHLEEN         Clinical Instructor
    ## 2923                       SCHUMACHER,ERICA         Clinical Instructor
    ## 2924                      SCHUSTER,JONATHAN          Adjunct Instructor
    ## 2925               SCHWARTZ,CHRISTINE RENEE                   Professor
    ## 2926                         SCHWARTZ,DAVID                   Professor
    ## 2927                      SCHWARTZ,DAVID C.                   Professor
    ## 2928                  SCHWARTZ,PAUL --SON--         Clinical Instructor
    ## 2929                      SCHWARZ,ALLISON M              Assoc Lecturer
    ## 2930                         SCHWARZ,ROBERT                    Lecturer
    ## 2931                      SCHWARZE,GRETCHEN         Associate Professor
    ## 2932                      SCHWARZE,MICHELLE         Assistant Professor
    ## 2933                        SCHWEBACH,MOLLY                    Lecturer
    ## 2934                        SCHWEBER,HOWARD                   Professor
    ## 2935                      SCHWEBER,SIMONE A                   Professor
    ## 2936                     SCHWENDINGER,LAURA                   Professor
    ## 2937                         SCHWOCH,ROBERT                    Lecturer
    ## 2938                   SCOTT,JESSICA ALYSIA       Assoc Professor (Chs)
    ## 2939                SEABORG,ANDREW THOMPSON          Adjunct Instructor
    ## 2940                         SEEGER,ANDREAS                   Professor
    ## 2941                          SEELY,WILLIAM             Senior Lecturer
    ## 2942                      SEFFROOD,BENJAMIN           Adjunct Professor
    ## 2943                           SEIBEL,KATIE                    Lecturer
    ## 2944                   SEIBERT,CHRISTINE S.             Professor (Chs)
    ## 2945                   SEIDEL,COURTNEY LANE         Clinical Assoc Prof
    ## 2946                      SEIDENBERG,MARK S                   Professor
    ## 2947                         SEIDMAN,GAY W.                   Professor
    ## 2948                         SEIFTER,MIRIAM         Associate Professor
    ## 2949                   SEILER SCHULTZ,TRACY          Clinical Asst Prof
    ## 2950                       SELL,KATHERINE A           Faculty Associate
    ## 2951                           SEMANIK,MIKE        Asst Professor (Chs)
    ## 2952            SEMRAD-DOOLITTLE,PAMELA SUE       Dis Faculty Associate
    ## 2953                      SENCHYNE,JONATHAN         Associate Professor
    ## 2954                    SENECAL,PETER KELLY           Adjunct Asst Prof
    ## 2955                       SENES,ALESSANDRO                   Professor
    ## 2956                         SEO,SANG BYUNG         Assistant Professor
    ## 2957                       SEPPALAINEN,TIMO                   Professor
    ## 2958                             SERAG,SARA                    Lecturer
    ## 2959                        SESHADRI,ANANTH                   Professor
    ## 2960                            SESIL,JAMES             Senior Lecturer
    ## 2961                             SESTO,MARY         Associate Professor
    ## 2962                 SETALURI,VIJAYASARADHI                   Professor
    ## 2963                          SETHARES,BILL                   Professor
    ## 2964                           SETHI,AJAY K         Associate Professor
    ## 2965                        SEVERSON,ERIC L         Assistant Professor
    ## 2966                               SEXE,LIZ                    Lecturer
    ## 2967                      SEYS,TRISHA MARIE          Clinical Asst Prof
    ## 2968                     SHAFER-LANDAU,RUSS                   Professor
    ## 2969               SHAFFER,DAVID WILLIAMSON                   Professor
    ## 2970                            SHAH,DHAVAN                   Professor
    ## 2971                            SHAH,HEMANT                   Professor
    ## 2972                            SHAH,MANISH                   Professor
    ## 2973                          SHALABY,MARWA         Assistant Professor
    ## 2974                     SHALIASTOVICH,IVAN         Associate Professor
    ## 2975                         SHANKAR,ANANTH         Assistant Professor
    ## 2976                  SHANMUGANAYAGAM,DHANU         Assistant Professor
    ## 2977                       SHANNON,BENJAMIN              Assoc Lecturer
    ## 2978                               SHAO,JUN                   Professor
    ## 2979                          SHAPIRO,DEBRA       Dis Faculty Associate
    ## 2980                          SHAPIRO,LARRY                   Professor
    ## 2981                        SHAPIRO,MIKE A.          Asst Faculty Assoc
    ## 2982                          SHAPIRO,VADIM                   Professor
    ## 2983                          SHARAFI,MITRA                   Professor
    ## 2984                            SHARMA,DIYA       Honorary Assoc/Fellow
    ## 2985                        SHARMA,PRASHANT         Assistant Professor
    ## 2986                        SHARP,NATHANIEL         Assistant Professor
    ## 2987                      SHASHKO,ALEXANDER                    Lecturer
    ## 2988                      SHAW,BRET RANDALL         Associate Professor
    ## 2989                    SHAW,GILLIAN CURTIS         Clinical Instructor
    ## 2990                             SHAW,KELLY         Clinical Instructor
    ## 2991                     SHCHERBYNA,TATIANA         Assistant Professor
    ## 2992                         SHEAR,LESLIE D          Clinical Professor
    ## 2993                     SHEEDY,MELISSA ANN                    Lecturer
    ## 2994                     SHEEHAN JR.,JOHN P                   Professor
    ## 2995                           SHEEHAN,NORA         Clinical Instructor
    ## 2996                  SHEETS,MICHAEL DENNIS                   Professor
    ## 2997                         SHEIBANI,NADER                   Professor
    ## 2998                        SHELEF,MIRIAM A         Associate Professor
    ## 2999                           SHELEF,NADAV                   Professor
    ## 3000                 SHELTON-MORRIS,YOLANDA              Assoc Lecturer
    ## 3001                               SHEN,HAO         Assistant Professor
    ## 3002                          SHENKER,YORAM       Honorary Assoc/Fellow
    ## 3003                         SHENOI,HEMANTH           Adjunct Professor
    ## 3004                         SHEREOS,JENINE              Assoc Lecturer
    ## 3005                          SHERER,NATHAN         Associate Professor
    ## 3006                       SHERRARD,CHERENE                   Professor
    ## 3007                       SHEVELENKO,IRINA                   Professor
    ## 3008                           SHI,GUANMING                   Professor
    ## 3009                             SHI,LEYUAN                   Professor
    ## 3010                               SHI,PENG         Associate Professor
    ## 3011                            SHI,XIAOXIA                   Professor
    ## 3012                       SHIELDS,MORGAN R           Faculty Associate
    ## 3013                        SHIELDS,REBECCA                    Lecturer
    ## 3014                             SHIN,JIHAE         Assistant Professor
    ## 3015                          SHIN,JUNG-HYE         Associate Professor
    ## 3016                         SHINNERS,KEVIN                   Professor
    ## 3017                     SHISHEGAR,NASTARAN         Assistant Professor
    ## 3018                              SHIU,GARY                   Professor
    ## 3019                    SHIYANBOLA,OLAYINKA         Associate Professor
    ## 3020                         SHOEMAKER,KARL                   Professor
    ## 3021                         SHOHET,J. LEON                   Professor
    ## 3022                     SHORT,SARAH JESSIE         Assistant Professor
    ## 3023                          SHREVE,PORTER                   Professor
    ## 3024                         SHUBERT,AMANDA              Assoc Lecturer
    ## 3025                            SHULL,JAMES                   Professor
    ## 3026                      SHUMOW,JOSEPH DEY                    Lecturer
    ## 3027                            SHUSTA,ERIC                   Professor
    ## 3028                           SHUTSKE,JOHN                   Professor
    ## 3029                         SHUTTS,KRISTIN                   Professor
    ## 3030                        SIBERT,EDWIN L.                   Professor
    ## 3031                             SIDEL,MARK                   Professor
    ## 3032                           SIDELLE,ALAN                   Professor
    ## 3033                           SIEMSEN,ENNO                   Professor
    ## 3034                      SIFAKIS,EFTYCHIOS         Associate Professor
    ## 3035                    SIGLER,PATRICIA ANN         Assoc Faculty Assoc
    ## 3036                          SILBER,HANNAH                    Lecturer
    ## 3037                      SILBERNAGEL,JANET                   Professor
    ## 3038                            SILET,KARIN                    Lecturer
    ## 3039                             SILVA,ERIN         Associate Professor
    ## 3040                        SIMCOX,JUDITH A         Assistant Professor
    ## 3041                        SIMMONS,ERICA S         Associate Professor
    ## 3042                          SIMON,PHILIPP                   Professor
    ## 3043                           SIMPSON,GAIL                   Professor
    ## 3044                             SIMS,REVEL         Assistant Professor
    ## 3045                          SINCLAIR,MATT         Assistant Professor
    ## 3046                        SINCOULAR,RANDY              Assoc Lecturer
    ## 3047                     SINDELAR,JEFFREY J                   Professor
    ## 3048                             SINGER,BEN         Associate Professor
    ## 3049                      SINGER,BRADLEY S.                   Professor
    ## 3050                           SINGH,ANNE M         Associate Professor
    ## 3051                            SINGH,VIKAS                   Professor
    ## 3052                           SINHA,RAUNAK         Assistant Professor
    ## 3053                          SKALA,MELISSA                   Professor
    ## 3054                        SKARZYNSKI,BART         Assoc Faculty Assoc
    ## 3055                           SKOG,MARLENE         Assistant Professor
    ## 3056                              SKOP,AHNA                   Professor
    ## 3057                 SKRENTNY,JAMES DOUGLAS           Faculty Associate
    ## 3058                          SLACK,KRISTEN                   Professor
    ## 3059                            SLADKY,KURT          Clinical Professor
    ## 3060                         SLUKVIN,IGOR I                   Professor
    ## 3061                         SMEDEMA,ADAM R                    Lecturer
    ## 3062                   SMEDEMA,SUSAN MILLER                   Professor
    ## 3063               SMEEDING,TIMOTHY MICHAEL                   Professor
    ## 3064                       SMITH III,LESLIE         Associate Professor
    ## 3065                         SMITH,AMANDA G          Asst Faculty Assoc
    ## 3066                     SMITH,AMANDA MARIE                    Lecturer
    ## 3067                             SMITH,ANNE         Clinical Assoc Prof
    ## 3068                 SMITH,CATHERINE ARNOTT                   Professor
    ## 3069                      SMITH,CHRISTINE E         Clinical Instructor
    ## 3070                            SMITH,DAMON         Associate Professor
    ## 3071                             SMITH,DOUG                    Lecturer
    ## 3072                            SMITH,ELLEN         Clinical Assoc Prof
    ## 3073                     SMITH,HEATHER DAWN          Asst Faculty Assoc
    ## 3074              SMITH,JEANNINA ANTOINETTE       Assoc Professor (Chs)
    ## 3075                             SMITH,JEFF                   Professor
    ## 3076                        SMITH,JEFFREY A                   Professor
    ## 3077                    SMITH,JENNIFER ROSE         Assistant Professor
    ## 3078                         SMITH,JUDITH A         Associate Professor
    ## 3079                        SMITH,LESLEY J.          Clinical Professor
    ## 3080                        SMITH,LESLIE M.                   Professor
    ## 3081                          SMITH,LLOYD M                   Professor
    ## 3082                            SMITH,LONES                   Professor
    ## 3083                         SMITH,MARGARET                    Lecturer
    ## 3084                     SMITH,MICHELE ANNE         Clinical Instructor
    ## 3085                         SMITH,NICHOLAS         Assoc Outreach Spec
    ## 3086                            SMITH,SCOTT          Visiting Asst Prof
    ## 3087                  SMITH,TESSA KATHERINE         Clinical Instructor
    ## 3088                          SNEDDEN,TRACI         Assistant Professor
    ## 3089                     SNELL,JEFFREY TODD           Faculty Associate
    ## 3090                    SNYDER,ASHLEY MARIE              Assoc Lecturer
    ## 3091                     SNYDER,CHRISTOPHER         Clinical Assoc Prof
    ## 3092                           SNYDER,KEVIN         Clinical Instructor
    ## 3093                          SNYDER,MAGGIE                    Lecturer
    ## 3094                     SNYDER,VIRGINIA L.       Assoc Professor (Chs)
    ## 3095                       SOBER,ELLIOTT R.                   Professor
    ## 3096            SOBIESKA,ALEKSANDRA CECYLIA          Visiting Asst Prof
    ## 3097                       SOELVSTEN,MIKKEL         Assistant Professor
    ## 3098                              SOHI,GURI                   Professor
    ## 3099                            SOLDAT,DOUG                   Professor
    ## 3100                          SOLHEIM,KAREN          Clinical Professor
    ## 3101                    SOLIS LEMUS,CLAUDIA         Assistant Professor
    ## 3102                 SOMERS,KATERINA IDETTE         Assistant Professor
    ## 3103                         SONDEL,PAUL M.                   Professor
    ## 3104                            SONE,HIROKI         Assistant Professor
    ## 3105                            SONE,JUDITH                    Lecturer
    ## 3106                        SORENSEN,ALAN T                   Professor
    ## 3107                SORKNESS,CHRISTINE ANNE         Dis Professor (Chs)
    ## 3108                         SOSKOVA,MARIYA         Associate Professor
    ## 3109                           SOUKUP,JASON         Clinical Assoc Prof
    ## 3110                SOUNNY-SLITINE,M. ANWAR         Assoc Faculty Assoc
    ## 3111                        SOUTHGATE,HENRY                    Lecturer
    ## 3112                           SOVINEC,CARL                   Professor
    ## 3113                      SPAGNOLIE,SAVERIO         Associate Professor
    ## 3114                         SPALDING,EDGAR                   Professor
    ## 3115                       SPAULDING,DANIEL         Assistant Professor
    ## 3116                         SPEECE,BEVERLY           Faculty Associate
    ## 3117                        SPEIDEL,MICHAEL         Associate Professor
    ## 3118                        SPERLING,CARRIE          Clinical Professor
    ## 3119                  SPIKE,BENJAMIN THOMAS         Assoc Faculty Assoc
    ## 3120                      SPURGERS,RACHEL L                    Lecturer
    ## 3121                            SRACIC,MIKE         Assoc Faculty Assoc
    ## 3122                      SRAMEK,BARBARA JO          Clinical Professor
    ## 3123                        SRIDHARAN,KUMAR                   Professor
    ## 3124                         SRIDHARAN,RUPA         Associate Professor
    ## 3125                   ST JAMES,MARIKO LUCY         Clinical Instructor
    ## 3126                   STAFFORD,CATHERINE A         Associate Professor
    ## 3127                       STAHL,SHANNON S.                   Professor
    ## 3128                 STAJKOVIC,ALEXANDER D.         Associate Professor
    ## 3129                      STALEY,ROBIN ANNE                    Lecturer
    ## 3130                           STAMBACH,AMY                   Professor
    ## 3131                            STAMM,JULIE          Clinical Asst Prof
    ## 3132                    STANIC-KOSTIC,ALEKS         Assistant Professor
    ## 3133                   STANIMIROVIC,SNEZANA                   Professor
    ## 3134                         STANLEY,DONALD           Faculty Associate
    ## 3135                          STANLEY,EMILY                   Professor
    ## 3136                      STANTON,MEGAN ANN                    Lecturer
    ## 3137                        STATKIEWICZ,MAX         Associate Professor
    ## 3138                      STATMAN,ALEXANDER              Assoc Lecturer
    ## 3139                           STAUFFER,JIM         Assoc Faculty Assoc
    ## 3140                          STECHMANN,SAM                   Professor
    ## 3141                          STEEGE,LINSEY         Associate Professor
    ## 3142                          STEFFAN,SHAWN         Associate Professor
    ## 3143                        STEINBERG,JESSE           Faculty Associate
    ## 3144                       STEINER,JAMES D.             Senior Lecturer
    ## 3145                     STEINKAMP,LISA ANN        Asst Professor (Chs)
    ## 3146                     STEPHENSON,JASON W       Assoc Professor (Chs)
    ## 3147                        STEPIEN,REBECCA          Clinical Professor
    ## 3148               STERLING VON GLAHN,AUDRA         Associate Professor
    ## 3149                             STERN,ADAM         Assistant Professor
    ## 3150                         STERN,WALTER C         Assistant Professor
    ## 3151                          STEUDEL,HARRY              Professor Emer
    ## 3152                 STEVENS,ANDREW WILLIAM         Assistant Professor
    ## 3153                         STEVENSON,ADAM          Clinical Professor
    ## 3154                       STEWART,COLLETTE           Faculty Associate
    ## 3155                         STEWART,KATE L                    Lecturer
    ## 3156                    STEWART,KATHARINA S             Professor (Chs)
    ## 3157                          STIEGERT,KYLE                   Professor
    ## 3158                   STIETZ,KIMBERLY KEIL         Assistant Professor
    ## 3159                           STILL,THOMAS             Senior Lecturer
    ## 3160                          STITES,ALISON              Assoc Lecturer
    ## 3161                   STODDARD,JEREMY DOUD                   Professor
    ## 3162                      STOECKER,RANDY R.                   Professor
    ## 3163                          STOLL,LINDY K                    Lecturer
    ## 3164                      STOLTENBERG,DAVID                   Professor
    ## 3165                         STOLZ,DANIEL A         Assistant Professor
    ## 3166                        STONE,DONALD S.                   Professor
    ## 3167                 STONEHOUSE,FREDERICK A                   Professor
    ## 3168                            STORY,KAYLA                    Lecturer
    ## 3169                          STOVALL,BETSY         Associate Professor
    ## 3170                             STOWE,JOHN                   Professor
    ## 3171                             STOWE,RYAN         Assistant Professor
    ## 3172                        STOWE,ZACHARY N                   Professor
    ## 3173                            STOY,PAUL C         Associate Professor
    ## 3174                        STOYCHUK,OKSANA              Assoc Lecturer
    ## 3175                            STRAMPP,PIA              Assoc Lecturer
    ## 3176                    STRANG,KEVIN THOMAS       Dis Faculty Associate
    ## 3177                           STRAUS,SCOTT                   Professor
    ## 3178                    STREET,BRIAN THOMAS                   Professor
    ## 3179                          STREIFFER,ROB                   Professor
    ## 3180                         STRIER,KAREN B                   Professor
    ## 3181                         STRIKER,ROBERT         Associate Professor
    ## 3182               STROHL,NICHOLAS MCINTOSH                    Lecturer
    ## 3183                        STROJNY,SHELLEY           Faculty Associate
    ## 3184                           STRONG,LAURA           Adjunct Professor
    ## 3185                        STRZELEC,ANDREA          Asst Faculty Assoc
    ## 3186                   STUDER,LYNETTE MARIE          Clinical Asst Prof
    ## 3187                      SU,RUTHIE REBECCA        Asst Professor (Chs)
    ## 3188                     SUAREZ,SASHA MARIA         Assistant Professor
    ## 3189                SUAREZ-GONZALEZ,DARILIS          Asst Faculty Assoc
    ## 3190                            SUEN,GARRET         Associate Professor
    ## 3191                         SUGDEN,WILLIAM                   Professor
    ## 3192                       SUKIENNIK,JUSTIN         Assoc Faculty Assoc
    ## 3193              SULLIVAN,CHRISTOPHER JOHN         Assistant Professor
    ## 3194                         SUMINSKI,AARON         Assoc Faculty Assoc
    ## 3195                            SUNDE,ROGER                   Professor
    ## 3196                    SUNDLING,KAITLIN E.        Asst Professor (Chs)
    ## 3197                       SURASIN,JANPANIT             Senior Lecturer
    ## 3198                      SURDYK,JOHN SCOTT           Faculty Associate
    ## 3199                        SURESH,KRISHNAN                   Professor
    ## 3200                            SURI,DEVIKA          Asst Faculty Assoc
    ## 3201                          SUROVI,LAUREN                    Lecturer
    ## 3202                 SURYANARAYANAN,SAINATH              Assoc Lecturer
    ## 3203                     SUSSMAN,MICHAEL R.                   Professor
    ## 3204                    SUTULA,THOMAS PETER       Honorary Assoc/Fellow
    ## 3205                          SUZUKI,AUSSIE         Assistant Professor
    ## 3206                       SUZUKI,MASATOSHI         Associate Professor
    ## 3207                            SVAREN,JOHN                   Professor
    ## 3208                   SVENSON,JAMES ERNEST       Assoc Professor (Chs)
    ## 3209                           SWACK,JEANNE                   Professor
    ## 3210                           SWAN,HEATHER             Senior Lecturer
    ## 3211                            SWANEY,ROSS         Associate Professor
    ## 3212                           SWANKE,JAMES                    Lecturer
    ## 3213                         SWARTZ,ALEISHA         Clinical Instructor
    ## 3214              SWARTZENTRUBER,ELAINE KAY             Senior Lecturer
    ## 3215                      SWATKOWSKI,PAMELA           Adjunct Professor
    ## 3216                            SWEET,JAMES                   Professor
    ## 3217                          SWIFT,MICHAEL                   Professor
    ## 3218                        SYAMKUMAR,MEENA          Asst Faculty Assoc
    ## 3219                       SYDNOR,JUSTIN R.                   Professor
    ## 3220                          SYFOX,CHONTEL         Assistant Professor
    ## 3221                         SYTSMA,KENNETH                   Professor
    ## 3222                     SZLUFARSKA,IZABELA                   Professor
    ## 3223                            TABER,CHRIS                   Professor
    ## 3224                              TAHK,ALEX         Associate Professor
    ## 3225                          TAHK,SUSANNAH         Associate Professor
    ## 3226                              TAI,STEPH                   Professor
    ## 3227                         TAKADA,MARILIA         Clinical Instructor
    ## 3228                        TAKAHASHI,NAOMI          Asst Faculty Assoc
    ## 3229                    TALAAT,ADEL MOHAMED                   Professor
    ## 3230                         TALARCZYK,ALAN                Dis Lecturer
    ## 3231                     TAMPLIN,OWEN JAMES         Assistant Professor
    ## 3232                           TANG,WEIPING                   Professor
    ## 3233                        TANG,ZHENGZHENG         Assistant Professor
    ## 3234                     TANNENBAUM,MATTHEW              Assoc Lecturer
    ## 3235                           TANNER,ROBIN         Associate Professor
    ## 3236                   TANNU,SWAMIT SANDEEP         Assistant Professor
    ## 3237                TANSEY,TIMOTHY NICHOLAS                   Professor
    ## 3238                    TANUMIHARDJO,SHERRY                   Professor
    ## 3239                           TARVER,BECKY             Senior Lecturer
    ## 3240                              TAS,SINAN               Asst Prof L/I
    ## 3241                           TAYLOR,BRIAN              Assoc Lecturer
    ## 3242                     TAYLOR,CHRISTOPHER                   Professor
    ## 3243                        TAYLOR,HOWARD W          Adjunct Instructor
    ## 3244               TAYLOR,JOLANDA VANDERWAL                   Professor
    ## 3245                         TAYLOR,MATTHEW                    Lecturer
    ## 3246                         TAYLOR,MICHAEL         Assistant Professor
    ## 3247                 TAYLOR-MARSHALL,SANDRA                    Lecturer
    ## 3248                     TEBBE,ELLIOT AARON         Assistant Professor
    ## 3249                           TEEPLE,SCOTT                   Professor
    ## 3250                       TEIXEIRA,LEANDRO         Assistant Professor
    ## 3251                TEJEDO-HERRERO,FERNANDO         Associate Professor
    ## 3252                            TEMPLE,JACK         Clinical Instructor
    ## 3253                    TEMTE,JONATHAN LANE             Professor (Chs)
    ## 3254                     TEODORESCU,MIHAELA                   Professor
    ## 3255                    TERASAWA-GRILLEY,EI                   Professor
    ## 3256                            TERLAAK,ANN         Associate Professor
    ## 3257                          TERRY,PAUL W.                   Professor
    ## 3258                    TERWILLIGER,PAUL M.                   Professor
    ## 3259                     TESLAA,JESSICA JOY          Asst Faculty Assoc
    ## 3260                             THAL,SARAH                   Professor
    ## 3261                   THATCHER,GRAHAM PAUL          Clinical Asst Prof
    ## 3262                 THEBAULT-SPIEKER,JACOB         Assistant Professor
    ## 3263                             THEIN,JILL       Assoc Professor (Chs)
    ## 3264                    THEIS,MONICA LOUISE                Dis Lecturer
    ## 3265                           THEISEN,CARA          Asst Faculty Assoc
    ## 3266                          THELEN,DARRYL                   Professor
    ## 3267                   THEOBALD,ANNE LOUISE           Faculty Associate
    ## 3268                          THERTUS,KETTY          Clinical Asst Prof
    ## 3269                  THEVAMARAN,RAMATHASAN         Assistant Professor
    ## 3270                        THIBEAULT,SUSAN                   Professor
    ## 3271                          THIEL,ABIGAIL              Assoc Lecturer
    ## 3272                    THIFFEAULT,JEAN-LUC                   Professor
    ## 3273                         THIMMIG,LESLIE                   Professor
    ## 3274                              THOMA,DAN                   Professor
    ## 3275                         THOMA,SHARON L           Faculty Associate
    ## 3276                           THOMAS,ALVIN         Assistant Professor
    ## 3277                         THOMAS,MICHAEL                   Professor
    ## 3278                        THOMAS,TYLER F.         Assistant Professor
    ## 3279                             THOMAS,ZEB              Assoc Lecturer
    ## 3280                         THOMPSON,ANITA                   Professor
    ## 3281                         THOMPSON,CRAIG                   Professor
    ## 3282           THOMPSON,DAKOTAH RITTENHOUSE         Assistant Professor
    ## 3283                        THOMPSON,DEAN A                    Lecturer
    ## 3284                       THOMPSON,KATRINA                   Professor
    ## 3285                         THOMPSON,MINDI                   Professor
    ## 3286                        THOMPSON,RYAN J        Asst Professor (Chs)
    ## 3287                       THOMSON,JAMES A.                   Professor
    ## 3288                THORLEIFSDOTTIR,KRISTIN         Assistant Professor
    ## 3289                       THURBER,CLIFFORD                   Professor
    ## 3290                           THURBER,MARY         Clinical Instructor
    ## 3291                          THURLOW,JULIE           Faculty Associate
    ## 3292                   THURS,DANIEL PATRICK          Asst Faculty Assoc
    ## 3293                   TIBBETTS,RANDAL SCOT                   Professor
    ## 3294                    TIBORIS,MICHAEL GUS             Senior Lecturer
    ## 3295                       TIDWELL,TAWNI L.              Assoc Lecturer
    ## 3296                           TIKOFF,BASIL                   Professor
    ## 3297                       TILLER,HEATHER S         Assoc Faculty Assoc
    ## 3298                    TILMANN,CHRISTOPHER           Faculty Associate
    ## 3299                        TIMBIE,PETER T.                   Professor
    ## 3300                           TIMLER,TESSA              Assoc Lecturer
    ## 3301                    TIMM,DANIEL JEFFREY           Faculty Associate
    ## 3302                            TIMM,STEVEN           Faculty Associate
    ## 3303                          TINGLUM,TRINA                    Lecturer
    ## 3304                           TINJUM,JAMES         Associate Professor
    ## 3305                TISCHAUSER,JEFF GARNETT                    Lecturer
    ## 3306                  TISHLER,JENNIFER RYAN           Faculty Associate
    ## 3307                      TITELBAUM,MICHAEL                   Professor
    ## 3308                      TJOSTHEIM,SONJA S          Clinical Asst Prof
    ## 3309                          TOBIN,MICHAEL          Adjunct Instructor
    ## 3310                      TOCHON,FRANCOIS V                   Professor
    ## 3311                       TODOROVIC,JELENA         Associate Professor
    ## 3312                       TOLLIVER,SARA E.         Clinical Instructor
    ## 3313                TOLSON,YOLANDA MICHELLE          Clinical Professor
    ## 3314                          TOMA,CATALINA         Associate Professor
    ## 3315                         TOMLINSON,KATY       Student Services Cord
    ## 3316                     TOMPKINS,WILLIS J.              Professor Emer
    ## 3317                            TONG,JORDAN         Associate Professor
    ## 3318                          TONGDAENG,EVE                    Lecturer
    ## 3319                          TONONI,GIULIO                   Professor
    ## 3320                         TOWNSEND,EMILY              Assoc Lecturer
    ## 3321                        TOWNSEND,PHILIP                   Professor
    ## 3322                     TOWNSEND,RICHARD H                   Professor
    ## 3323                          TRACY,WILLIAM                   Professor
    ## 3324                         TRAN,HUNG VINH         Associate Professor
    ## 3325                     TRAVERS,BRITTANY G         Associate Professor
    ## 3326                TRAYNOR,SARAH ELIZABETH              Assoc Lecturer
    ## 3327                              TREJO,SAM         Assistant Professor
    ## 3328                       TREMONTI,CHRISTY         Associate Professor
    ## 3329                       TREPANIER,LAUREN                   Professor
    ## 3330                            TREST,MARIE         Assoc Faculty Assoc
    ## 3331                          TREVES,ADRIAN                   Professor
    ## 3332                  TREVINO-MURPHY,ALICIA              Assoc Lecturer
    ## 3333                         TREVOR,CHARLIE                   Professor
    ## 3334                    TREZEK,BEVERLY JANE         Associate Professor
    ## 3335                           TRIANA,MARIA         Associate Professor
    ## 3336                     TRIGSTED,STEPHANIE          Asst Faculty Assoc
    ## 3337                    TRIMBELL,KOHL MARIE                    Lecturer
    ## 3338                     TRIPOLI,GREGORY J.                   Professor
    ## 3339                             TRIPP,AILI                   Professor
    ## 3340                           TROTTER,MARY         Associate Professor
    ## 3341                         TROWBRIDGE,AMY         Assistant Professor
    ## 3342                     TRUE,JAMES MICHAEL          Adjunct Instructor
    ## 3343                         TRUJILLO,MARIO         Associate Professor
    ## 3344                        TRYON,ELIZABETH            Sr Outreach Spec
    ## 3345                        TUCKER,PATRICIA                    Lecturer
    ## 3346                   TUERKHEIMER,FRANK M.              Professor Emer
    ## 3347                            TULI,SACHIN           Faculty Associate
    ## 3348                          TUMARKIN,ANNA           Faculty Associate
    ## 3349                       TUN,SAN SAN HNIN           Faculty Associate
    ## 3350                         TUREK,MICHELLE         Clinical Assoc Prof
    ## 3351                          TURNER,ANDREW                    Lecturer
    ## 3352                    TURNER,ANDREW JASON                    Lecturer
    ## 3353                           TURNER,ERICA         Associate Professor
    ## 3354                      TURNER,KRISTOPHER              Assoc Lecturer
    ## 3355                         TURNER,MATTHEW                   Professor
    ## 3356                       TURNER,MONICA G.                   Professor
    ## 3357                        TURNG,LIH-SHENG                   Professor
    ## 3358                         TYLER,MITCHELL       Honorary Assoc/Fellow
    ## 3359                        TZAMOS,CHRISTOS         Assistant Professor
    ## 3360                    UDVARI-SOLNER,ALICE           Faculty Associate
    ## 3361                            UHLRICH,DAN                   Professor
    ## 3362                      ULLAND,TYLER KENT         Assistant Professor
    ## 3363                        UNDERWOOD,JULIE                   Professor
    ## 3364                     UPAH,BARTHOLOMEW G                    Lecturer
    ## 3365                    URNESS,CHARLES TODD                    Lecturer
    ## 3366                         URRUTIA,MATTIE           Faculty Associate
    ## 3367                         USECHE,ALLISON         Assistant Professor
    ## 3368                       USSISHKIN,DANIEL         Associate Professor
    ## 3369                            VAID,UCHITA         Assistant Professor
    ## 3370                             VAIL,DAVID                   Professor
    ## 3371               VALENCIA,SARAH ELIZABETH              Assoc Lecturer
    ## 3372                       VALEO COOKE,NINA           Faculty Associate
    ## 3373                          VALKO,BENEDEK                   Professor
    ## 3374                         VALLEY,JOHN W.                   Professor
    ## 3375                            VALLON,MARC                   Professor
    ## 3376                    VAN HALLGREN,CARRIE             Senior Lecturer
    ## 3377                VAN ASSELT,NATHANIEL C.          Clinical Asst Prof
    ## 3378                  VAN DAN,REBECCA SUSAN              Assoc Lecturer
    ## 3379                     VAN DE WATER,MANON                   Professor
    ## 3380                     VAN DEELEN,TIMOTHY                   Professor
    ## 3381                   VAN DER WEIDE,DANIEL                   Professor
    ## 3382              VAN DYKE JR.,KENNETH JOHN       Assoc Professor (Chs)
    ## 3383                      VAN KAN,PETER L E         Associate Professor
    ## 3384                        VAN LEHN,REID C         Assistant Professor
    ## 3385                   VAN MALE,THERESE ANN           Faculty Associate
    ## 3386                   VAN MELKEBEEK,DIETER                   Professor
    ## 3387                        VAN OS,JENNIFER         Assistant Professor
    ## 3388                 VAN PIJKEREN,JAN PETER         Associate Professor
    ## 3389                        VAN RIJN,JORDAN                    Lecturer
    ## 3390               VAN RYBROEK,GREGORY JOHN           Adjunct Asst Prof
    ## 3391               VAN SICKLEN,BARRET VILAS          Adjunct Instructor
    ## 3392                           VAN SWOL,LYN                   Professor
    ## 3393                      VANCAMP,ELIJAH B.          Adjunct Instructor
    ## 3394                     VANDEN HEUVEL,MIKE                   Professor
    ## 3395                   VANDENBROUCKE,JUSTIN         Associate Professor
    ## 3396                     VANDER ZANDEN,JAKE                   Professor
    ## 3397                      VANDERBURG,ANDREW         Assistant Professor
    ## 3398                 VANDERWALL,CASSANDRA M           Adjunct Asst Prof
    ## 3399                          VANVEEN,BARRY                   Professor
    ## 3400                              VARDI,URI                   Professor
    ## 3401                          VARESCHI,MARK         Associate Professor
    ## 3402                       VARGAS,MARCELO R         Assistant Professor
    ## 3403                VARGAS-PRIETO,ALBERTO M           Faculty Associate
    ## 3404                          VARGHESE,TOMY                   Professor
    ## 3405                           VARSAVA,NINA         Assistant Professor
    ## 3406                         VATAN,FLORENCE                   Professor
    ## 3407                   VAUGHAN,BRIAN DWIGHT                    Lecturer
    ## 3408                        VAVILOV,MAXIM G                   Professor
    ## 3409                          VEERAMANI,RAJ                   Professor
    ## 3410                            VEITH,TONYA          Clinical Asst Prof
    ## 3411              VELLIQUETTE,MICHAEL JAMES           Faculty Associate
    ## 3412                     VELTEN,ANDREAS UDO         Assistant Professor
    ## 3413                        VEMUGANTI,RAGHU                   Professor
    ## 3414                  VENKATARAMAN,SHIVARAM         Assistant Professor
    ## 3415                    VENKATARAMANAN,GIRI                   Professor
    ## 3416                          VENTURA,STEVE                   Professor
    ## 3417                     VENTURELLI,OPHELIA         Assistant Professor
    ## 3418                     VENTURINI,MICHELLE           Adjunct Professor
    ## 3419                        VERBRUGGE,MARIA         Clinical Instructor
    ## 3420                   VERMILLION,KATIE LEE         Assoc Faculty Assoc
    ## 3421                     VESTLING,MARTHA M.            Senior Scientist
    ## 3422                         VEZINA,CHAD M.                   Professor
    ## 3423                         VICKROY,CHERYL           Adjunct Professor
    ## 3424                       VIEIRA,CATHERINE                   Professor
    ## 3425                              VILA,ANNE                   Professor
    ## 3426                       VILLAGRAN,JOSE G              Assoc Lecturer
    ## 3427                          VIMONT,DANIEL                   Professor
    ## 3428                         VINEY,GRETCHEN           Dis Clinical Prof
    ## 3429                     VITCENDA,ANGELA K.          Clinical Asst Prof
    ## 3430                             VIVIAN,EVA             Professor (Chs)
    ## 3431                   VIVIANO,KATRINA ROSE         Clinical Assoc Prof
    ## 3432                            VLACH,HALEY         Associate Professor
    ## 3433                            VOGE,CASSIE         Clinical Assoc Prof
    ## 3434                        VOILS,CORRINE I                   Professor
    ## 3435                     VON SIMSON,CHARLES         Clinical Assoc Prof
    ## 3436                      VOPAL,EDWARD JOHN          Adjunct Instructor
    ## 3437                            VOYLES,PAUL                   Professor
    ## 3438                     VRANAS,PETER B. M.                   Professor
    ## 3439                            VUE,GOODSON                    Lecturer
    ## 3440                      WACKER,LEEANN SOO               Professor L/I
    ## 3441                          WAGGONER,JESS         Assistant Professor
    ## 3442                           WAGH,SIDDESH          Visiting Asst Prof
    ## 3443                         WAGNER,AMY LEE                    Lecturer
    ## 3444                            WAGNER,BRIT              Assoc Lecturer
    ## 3445                         WAGNER,MICHAEL                   Professor
    ## 3446                            WAGNER,MIKE         Assistant Professor
    ## 3447                             WAGNER,ROB         Assoc Faculty Assoc
    ## 3448                      WAGNER,TERA HOLTZ           Faculty Associate
    ## 3449                           WAGNER,TIAHA         Clinical Instructor
    ## 3450                       WAGNER,TIMOTHY J                    Lecturer
    ## 3451                            WAHEED,SANA        Asst Professor (Chs)
    ## 3452                        WAKAI,RONALD T.                   Professor
    ## 3453                        WAKKER,BASTIAAN              Assoc Lecturer
    ## 3454                           WALASZEK,ART             Professor (Chs)
    ## 3455             WALBRANDT PIGARELLI,DENISE       Assoc Professor (Chs)
    ## 3456               WALDEN,JUSTINE ANGELIQUE                    Lecturer
    ## 3457                           WALDRON,ALEX         Assistant Professor
    ## 3458                         WALEFFE,FABIAN                   Professor
    ## 3459                   WALKER,CHRISTOPHER A                   Professor
    ## 3460                         WALKER,JAMES R                   Professor
    ## 3461                         WALKER,JULIE M         Clinical Assoc Prof
    ## 3462                          WALKER,THAD G                   Professor
    ## 3463                    WALLACE,GEOFFREY L.         Associate Professor
    ## 3464                   WALLACE,SUZANNE BETH          Clinical Asst Prof
    ## 3465                             WALLER,KEN         Clinical Assoc Prof
    ## 3466                          WALLER,SHELLY                    Lecturer
    ## 3467                      WALLMANN,JOHANNES         Associate Professor
    ## 3468                         WALSH,JENNIFER                    Lecturer
    ## 3469                      WALSH,JOHN EDWARD             Senior Lecturer
    ## 3470                         WALSH,JOSEPH G           Faculty Associate
    ## 3471                             WALSH,KATE         Associate Professor
    ## 3472               WALSH,MATTHEW CUNNINGHAM                    Lecturer
    ## 3473                           WALSH,TOVA B         Assistant Professor
    ## 3474                       WALTER,ALEXANDRA                    Lecturer
    ## 3475                      WANDEL,LEE PALMER                   Professor
    ## 3476                            WANG,BOTONG         Assistant Professor
    ## 3477                                WANG,BU         Assistant Professor
    ## 3478                           WANG,DAIFENG         Assistant Professor
    ## 3479                               WANG,HAN         Assistant Professor
    ## 3480              WANG,JENNIFER LYNN HYLAND                    Lecturer
    ## 3481                               WANG,JUE                   Professor
    ## 3482                              WANG,MARY           Faculty Associate
    ## 3483                           WANG,MIAOYAN         Assistant Professor
    ## 3484                              WANG,TINA         Assistant Professor
    ## 3485                               WANG,XIN         Assistant Professor
    ## 3486                            WANG,XUDONG                   Professor
    ## 3487                             WANG,XUELI                   Professor
    ## 3488                              WANG,YANG         Associate Professor
    ## 3489                            WANG,YAZHEN                   Professor
    ## 3490                                WANG,YI         Assistant Professor
    ## 3491                              WANG,YING         Assistant Professor
    ## 3492                       WANGERIN, JOANNA             Senior Lecturer
    ## 3493                           WANGERIN,DAN         Associate Professor
    ## 3494                            WANNER,ANJA                   Professor
    ## 3495                       WARD,DAVID ALLEN             Senior Lecturer
    ## 3496                           WARD,EARLISE                   Professor
    ## 3497                           WARD,EMILY J         Assistant Professor
    ## 3498                   WARDRIP,PETER THOMAS         Assistant Professor
    ## 3499                       WARFIELD,TERRY D                   Professor
    ## 3500                WARGOWSKI,DAVID STEPHAN             Professor (Chs)
    ## 3501                       WARNER,H WILLIAM              Assoc Lecturer
    ## 3502                WARREN ANDERSEN,SHANEDA         Assistant Professor
    ## 3503                        WASSARMAN,DAVID                   Professor
    ## 3504                        WASSARMAN,KAREN                   Professor
    ## 3505                          WATSON,ANDREW         Assistant Professor
    ## 3506                          WATTERS,JYOTI                   Professor
    ## 3507                        WATTIAUX,MICHEL                   Professor
    ## 3508                           WATTS,STEVEN                    Lecturer
    ## 3509                      WAX,AUDREY LAUREN                    Lecturer
    ## 3510                          WEAVER,BETH A         Associate Professor
    ## 3511                          WEAVER,JEREMY           Faculty Associate
    ## 3512                            WEBER,JESSE         Assistant Professor
    ## 3513                            WEBERT,KYLE          Asst Faculty Assoc
    ## 3514                              WEEKS,AMY         Assistant Professor
    ## 3515                          WEEKS,JESSICA                   Professor
    ## 3516                             WEI,HAORAN         Assistant Professor
    ## 3517                      WEICHERT,JAMEY P.                   Professor
    ## 3518                            WEIGEL,KENT                   Professor
    ## 3519                         WEIGOLD,URSULA          Clinical Professor
    ## 3520                            WEIMER,DAVE                   Professor
    ## 3521                             WEISS,LIAD         Assistant Professor
    ## 3522                     WEISSHAAR,JAMES C.                   Professor
    ## 3523                       WEIX,DANIEL JOHN                   Professor
    ## 3524                           WELCH,RODNEY                   Professor
    ## 3525                          WELHAM,NATHAN         Associate Professor
    ## 3526                    WELLIK,DENEEN MARIE                   Professor
    ## 3527                            WELLS,SARAH         Associate Professor
    ## 3528                   WELTON,ANJALE DEVAWN                   Professor
    ## 3529                        WEMMERLOV,URBAN                   Professor
    ## 3530                  WENDLAND,CLAIRE LEONE                   Professor
    ## 3531                              WENDT,AMY                   Professor
    ## 3532                        WENDT,MARK ALAN           Faculty Associate
    ## 3533                             WENG,YIQUN                   Professor
    ## 3534                             WENKER,SUE        Asst Professor (Chs)
    ## 3535                     WENTHUR,CODY JAMES         Assistant Professor
    ## 3536                          WERETKA,MAREK         Associate Professor
    ## 3537                          WERLE,RODRIGO         Assistant Professor
    ## 3538                          WERLING,DONNA         Assistant Professor
    ## 3539                           WERNER,CRAIG              Professor Emer
    ## 3540                          WERNER,NICOLE         Assistant Professor
    ## 3541                   WEST,CHARLES RAYMOND             Senior Lecturer
    ## 3542                           WEST,CYNTHIA                    Lecturer
    ## 3543                        WEST,KENNETH D.                   Professor
    ## 3544               WESTERGAARD,RYAN PATRICK         Associate Professor
    ## 3545                     WESTLER,WILLIAM M.               Dis Scientist
    ## 3546                     WESTMARK,CARA JEAN         Assistant Professor
    ## 3547                        WHEELER,DERIC L         Associate Professor
    ## 3548                       WHELAN,CHRISTINE         Assoc Faculty Assoc
    ## 3549                          WHITE,HEATHER         Associate Professor
    ## 3550                        WHITE,MONICA M.         Associate Professor
    ## 3551                            WHITE,SARAH         Clinical Instructor
    ## 3552                 WHITING,GLORIA MCCAHON         Assistant Professor
    ## 3553                           WHITMAN,THEA         Assistant Professor
    ## 3554                      WHITMIRE,ETHELENE                   Professor
    ## 3555                           WHITMORE,KIM         Assistant Professor
    ## 3556                          WHITTLE,BRUNO         Assistant Professor
    ## 3557                         WICKENS,ZACH K         Assistant Professor
    ## 3558                 WIDICUS WEAVER,SUSANNA                   Professor
    ## 3559                       WIDMAYER,CHRISSY                    Lecturer
    ## 3560                          WIEBEN,OLIVER                   Professor
    ## 3561                        WIEDENHOEFT,BOB                    Lecturer
    ## 3562                     WIEGMANN,DOUGLAS A         Associate Professor
    ## 3563                       WIEGMANN,SUSAN M         Assoc Faculty Assoc
    ## 3564                      WIENHOLTS,JOHANNA                    Lecturer
    ## 3565                      WIERCIOCH,GREGORY         Clinical Assoc Prof
    ## 3566                      WIESSINGER,NICOLE         Assoc Faculty Assoc
    ## 3567                           WILCOTS,ERIC                   Professor
    ## 3568                       WILD,PROF JOHN J                   Professor
    ## 3569                      WILDONGER,JILL C.         Associate Professor
    ## 3570                     WILES,BRADLEY JOHN              Assoc Lecturer
    ## 3571                     WILKERSON,KIMBER L                   Professor
    ## 3572                        WILKINSON,GRACE         Assistant Professor
    ## 3573                      WILKINSON,KRISTIN                    Lecturer
    ## 3574                          WILLE,CHRISTA              Assoc Lecturer
    ## 3575                           WILLES,MEGAN                    Lecturer
    ## 3576                        WILLETT,REBEKAH         Associate Professor
    ## 3577                        WILLIAMS,JACK W                   Professor
    ## 3578                     WILLIAMS,JAHMESE M          Asst Faculty Assoc
    ## 3579                           WILLIAMS,JIM         Assoc Faculty Assoc
    ## 3580                   WILLIAMS,JUSTIN COLE                   Professor
    ## 3581                        WILLIAMS,MAKEBA         Clinical Assoc Prof
    ## 3582                     WILLIAMS,MICHAEL L           Faculty Associate
    ## 3583                        WILLIAMS,NOAH M                   Professor
    ## 3584                      WILLIAMS,SCOTT P.          Asst Faculty Assoc
    ## 3585                       WILLIAMSON,BRADY       Honorary Assoc/Fellow
    ## 3586                    WILLIAMSON,LILLIE D         Assistant Professor
    ## 3587                       WILLIAMSON,SARAH           Faculty Associate
    ## 3588                       WILLIFORD,DANIEL         Assistant Professor
    ## 3589                         WILLITS,ANGELA         Clinical Assoc Prof
    ## 3590                          WILLMANN,KARL       Assoc Professor (Chs)
    ## 3591                         WILSON,BETHANY          Adjunct Instructor
    ## 3592                            WILSON,PAUL                   Professor
    ## 3593                          WILTBANK,MILO                   Professor
    ## 3594                  WINCENTSEN,HEIDI LYNN           Faculty Associate
    ## 3595                     WINDSOR,JAMES MARK                    Lecturer
    ## 3596               WINKLE-WAGNER,RACHELLE L                   Professor
    ## 3597                           WINSTON,TINA           Faculty Associate
    ## 3598             WINTERSTEIN,ANDREW PATRICK           Dis Clinical Prof
    ## 3599                  WISWALL,MATTHEW JAMES                   Professor
    ## 3600                   WITZENBURG,COLLEEN M         Assistant Professor
    ## 3601                      WIXON,DEVIN LAURA                    Lecturer
    ## 3602                          WIYAKA,DENISE           Faculty Associate
    ## 3603                       WODZYNSKI,LUKASZ         Assistant Professor
    ## 3604                           WOLF,KIRSTEN                   Professor
    ## 3605                          WOLF,MARSHA J            Senior Scientist
    ## 3606                  WOLINSKY,ZACHARY EVAN              Assoc Lecturer
    ## 3607                          WOLLACK,JAMES                   Professor
    ## 3608                  WOLLACK,JODI ERIKSSON                    Lecturer
    ## 3609                   WONG,NANCY YEE CHING                   Professor
    ## 3610                            WOOD, SARAH             Senior Lecturer
    ## 3611                   WOOD,MICHAEL WILLAIM          Clinical Asst Prof
    ## 3612                              WOODS,JON                   Professor
    ## 3613                    WOODS,ROBERT CLAUDE                   Professor
    ## 3614                   WOODWARD,CATHERINE L         Assoc Faculty Assoc
    ## 3615                         WOODWARD,KEITH                   Professor
    ## 3616                    WORZELLA,TRACY JEAN       Honorary Assoc/Fellow
    ## 3617                          WRIGHT,DANIEL         Assistant Professor
    ## 3618                     WRIGHT,ELIZABETH R                   Professor
    ## 3619                            WRIGHT,JOHN              Professor Emer
    ## 3620                         WRIGHT,RANDALL                   Professor
    ## 3621                       WRIGHT,STEPHEN J                   Professor
    ## 3622                   WRIGHT,STEVEN HOWARD         Clinical Assoc Prof
    ## 3623                          WRIGHT,TRAVIS         Associate Professor
    ## 3624                            WU,BI CHENG              Assoc Lecturer
    ## 3625                              WU,CHENXI         Assistant Professor
    ## 3626                              WU,CHIN H                   Professor
    ## 3627                             WU,DESMUND              Assoc Lecturer
    ## 3628                          WU,SAU LAN YU                   Professor
    ## 3629                          WYNE,KEVIN T.           Faculty Associate
    ## 3630                          XENOS,MICHAEL                   Professor
    ## 3631                            XING,YONGNA         Associate Professor
    ## 3632                         XIONG,YANG SAO         Assistant Professor
    ## 3633                             XU,HUIFANG                   Professor
    ## 3634                                XU,TINA                    Lecturer
    ## 3635                                 XU,WEI                   Professor
    ## 3636                             XU,XIANGRU         Assistant Professor
    ## 3637                          YABLON,ROBERT         Associate Professor
    ## 3638                           YACKEE,JASON                   Professor
    ## 3639                         YACKEE,SUSAN W                   Professor
    ## 3640                          YAHN,JEREMIAH           Faculty Associate
    ## 3641                          YANDELL,BRIAN                   Professor
    ## 3642                                YANG,BO          Asst Faculty Assoc
    ## 3643                             YANG,SIJIA         Assistant Professor
    ## 3644                           YANG,TONGHAI                   Professor
    ## 3645                              YANG,YANG         Assistant Professor
    ## 3646                     YAUCH,CHARLENE ANN         Assoc Faculty Assoc
    ## 3647                         YAVAS,ABDULLAH                   Professor
    ## 3648                            YAVUZ,DENIZ                   Professor
    ## 3649                               YEN,ERIC         Associate Professor
    ## 3650                         YESILKOY,FILIZ         Assistant Professor
    ## 3651                          YETHIRAJ,ARUN                   Professor
    ## 3652                     YIN,JERRY CHI-PING                   Professor
    ## 3653                               YIN,JOHN                   Professor
    ## 3654                            YIN,TOM C T       Honorary Assoc/Fellow
    ## 3655                           YOON,TEHSHIK                   Professor
    ## 3656                            YOOSE,BECKY              Assoc Lecturer
    ## 3657                              YOUNG,DAN                   Professor
    ## 3658                           YOUNG,LOUISE                   Professor
    ## 3659                 YOUNG,MORGAN ELISABETH          Adjunct Instructor
    ## 3660                           YOUNG,MORRIS                   Professor
    ## 3661                        YOUNG,RICHARD F                   Professor
    ## 3662                          YOUNG,STEPHEN         Associate Professor
    ## 3663                            YU,JAE-HYUK                   Professor
    ## 3664                             YU,JIN-WEN                   Professor
    ## 3665                                  YU,JP         Assistant Professor
    ## 3666                                YU,LIAN                   Professor
    ## 3667                            YU,MENGGANG                   Professor
    ## 3668                             YU,TIMOTHY                   Professor
    ## 3669                            YU,XIANGYAO         Assistant Professor
    ## 3670                              YU,ZONGFU         Associate Professor
    ## 3671                          YUDKOFF,SUNNY         Assistant Professor
    ## 3672                        ZACHARIA,NICOLE         Assoc Faculty Assoc
    ## 3673                         ZACHARSKI,GREG        Professor Of Mil Sci
    ## 3674                          ZAHASKY,CHRIS         Assistant Professor
    ## 3675                       ZAKOWSKI,LAURA J             Professor (Chs)
    ## 3676                            ZALAPA,JUAN         Associate Professor
    ## 3677                       ZAMANIAN,MOSTAFA         Assistant Professor
    ## 3678                           ZAMAR,SHEILA              Assoc Lecturer
    ## 3679                    ZANNI,MARTIN THOMAS                   Professor
    ## 3680                  ZAPATA,JASMINE YVONNE        Asst Professor (Chs)
    ## 3681                          ZARZAUR,BEN L                   Professor
    ## 3682                   ZAVALA-TEJEDA,VICTOR         Associate Professor
    ## 3683                    ZAYAS-CABAN,GABRIEL         Assistant Professor
    ## 3684                     ZDEBLICK,THOMAS A.                   Professor
    ## 3685                         ZEDLER,PAUL H.                   Professor
    ## 3686                          ZEHMS,KARLA M                   Professor
    ## 3687                   ZELENSKI,AMY BARBARA        Asst Professor (Chs)
    ## 3688                   ZELEWSKI,LINDA MARIE             Senior Lecturer
    ## 3689                  ZEPEDA-NUNEZ,LEONARDO         Assistant Professor
    ## 3690                         ZERVOU,NATALIE         Assistant Professor
    ## 3691                         ZHANG CHUNMING                   Professor
    ## 3692                          ZHANG XIAOFEI        Asst Professor (Chs)
    ## 3693                             ZHANG,ANRU         Assistant Professor
    ## 3694                            ZHANG,DAYIN         Assistant Professor
    ## 3695                         ZHANG,HONGMING                   Professor
    ## 3696                             ZHANG,JIAO                    Lecturer
    ## 3697                             ZHANG,JING                   Professor
    ## 3698                               ZHANG,KE         Assistant Professor
    ## 3699                           ZHANG,TIANLU          Asst Faculty Assoc
    ## 3700                     ZHANG,XIUJUAN JANE                    Lecturer
    ## 3701                            ZHANG,YIWEI         Assistant Professor
    ## 3702                         ZHANG,YONGFENG         Assistant Professor
    ## 3703                         ZHANG,ZHENGJUN                   Professor
    ## 3704                             ZHANG,ZHOU         Assistant Professor
    ## 3705                               ZHAO,FEI         Assistant Professor
    ## 3706                             ZHAO,JIWEI         Assistant Professor
    ## 3707                             ZHAO,XINYU                   Professor
    ## 3708                            ZHAO,YUHANG         Assistant Professor
    ## 3709                             ZHENG,JING                   Professor
    ## 3710                           ZHONG,XUEHUA         Associate Professor
    ## 3711                           ZHOU,JIAZHEN              Assoc Prof L/I
    ## 3712                             ZHOU,SHIYU                   Professor
    ## 3713                          ZHOU,YONGMING                   Professor
    ## 3714                             ZHU,A-XING                   Professor
    ## 3715                              ZHU,JERRY                   Professor
    ## 3716                                ZHU,JUN                   Professor
    ## 3717                             ZHU,WEIHUA         Associate Professor
    ## 3718                            ZHU,ZHENHUA         Assistant Professor
    ## 3719                         ZICKUHR,THOMAS                    Lecturer
    ## 3720                     ZILBERGERTS,MARINA         Assistant Professor
    ## 3721                          ZIMMER,ANDREW         Assistant Professor
    ## 3722                        ZIMMERMAN,DAVID                   Professor
    ## 3723                          ZINK,DANIELLE              Assoc Lecturer
    ## 3724                              ZINN,MIKE         Associate Professor
    ## 3725                         ZITZER,NINA C.          Clinical Asst Prof
    ## 3726                          ZOET,LUCAS K.         Assistant Professor
    ## 3727                 ZOROMSKI,LORRAINE MARY           Faculty Associate
    ## 3728                    ZUCKERBERG,BENJAMIN         Associate Professor
    ## 3729                 ZUEHLKE,AMANDA CELESTE         Assoc Faculty Assoc
    ## 3730                       ZUELSDORFF,MEGAN         Assistant Professor
    ## 3731                        ZUMBRUNNEN,JOHN                   Professor
    ## 3732                 ZUMWALDE,NICHOLAS ALAN          Asst Faculty Assoc
    ## 3733                     ZURAWSKI,SARAH ANN                    Lecturer
    ## 3734                             ZWASKA,AMY              Assoc Lecturer
    ## 3735                           ZWECK,JORDAN         Associate Professor
    ## 3736                        ZWEIBEL,ELLEN G                   Professor
    ##                          department                                    degree
    ## 1           Obstetrics & Gynecology          PHD 1979 University of Edinburgh
    ## 2                    Anesthesiology              MD 2000 University of Assiut
    ## 3                               Art             PHD 2012 Royal College of Art
    ## 4                          Pharmacy        PHD 2013 Univ of Wisconsin-Madison
    ## 5                Information School         MA 2017 Univ of Wisconsin-Madison
    ## 6                        Psychology       PHD 1978 University of Pennsylvania
    ## 7                Accting & Info Sys       MACC 2005 Univ of Wisconsin-Madison
    ## 8    Atmospheric & Oceanic Sciences        PHD 1987 Colorado State University
    ## 9            Mechanical Engineering    PHD 2008 Univ of Michigan at Ann Arbor
    ## 10   Atmospheric & Oceanic Sciences         PHD 2018 University of Washington
    ## 11                          Nursing        DNP 2017 Univ of Wisconsin-Madison
    ## 12               Information School            MA University of South Florida
    ## 13        Animal And Dairy Sciences         PHD 2020 Univ of California Davis
    ## 14                       Psychology        PHD 1998 Univ of Wisconsin-Madison
    ## 15          School Of Human Ecology                   PHD 2012 Ithaca College
    ## 16            Afro-American Studies        PHD 1989 Univ of Wisconsin-Madison
    ## 17                  Volunteer Staff              MD 1989 University Of Aleppo
    ## 18       Curriculum And Instruction        PHD 2019 Univ of California Irvine
    ## 19      Engineering Research Center         MS 1997 Univ of Wisconsin-Madison
    ## 20         African Cultural Studies        PHD 2019 Univ of Wisconsin-Madison
    ## 21                  Plant Pathology        PHD 1981 Univ of Wisconsin-Madison
    ## 22                      Dermatology            PHD 1989 University of Lucknow
    ## 23             Neurological Surgery      MD 2003 Loyola University of Chicago
    ## 24       Asian Languages & Cultures            MA 2013 Ewha Womans University
    ## 25       Civil & Environmental Engr           PHD Univ of California Berkeley
    ## 26                              Art   MFA 2007 Maryland Institute Colg Of Art
    ## 27                         Medicine     MD 2002 U of California San Francisco
    ## 28                      Mathematics      PHD 2019 Univ of California Berkeley
    ## 29                       Law School              JD 1972 Marquette University
    ## 30                        Economics       PHD 2014 University of Pennsylvania
    ## 31    Engr Professional Development                                       PHD
    ## 32                Computer Sciences       PHD 2005 Carnegie-Mellon University
    ## 33                          Surgery            PHD 2012 University of Alberta
    ## 34                       Pediatrics                MD 2005 Al-Quds University
    ## 35        Industrial & Systems Engr         PHD 2004 University of Pittsburgh
    ## 36                         Oncology      PHD 1991 Univ of California Berkeley
    ## 37    Community & Environ Sociology               PHD 2002 Cornell University
    ## 38                Computer Sciences            PHD 2014 University of Toronto
    ## 39           Educational Psychology         PHD 2002 Arizona State University
    ## 40        Industrial & Systems Engr   PHD 2006 Univ of IL at Urbana-Champaign
    ## 41                         Medicine             MD 1984 University of Vermont
    ## 42           Spanish And Portuguese       PHD 1994 Univ Complutense de Madrid
    ## 43     Management & Human Resources        PHD 1974 Michigan State University
    ## 44                        Economics   PHD 2009 Univ of California Los Angeles
    ## 45                  Medical Physics            PHD 1994 University of Arizona
    ## 46                          English     MA 2007 University Of Central Florida
    ## 47                          Nursing        PHD 2018 Univ of Wisconsin-Madison
    ## 48                 Military Science                                   BA 2002
    ## 49      South Asian Sum Lang Instit                                       PHD
    ## 50                       Psychology            PHD 1994 University of Chicago
    ## 51             Neurological Surgery    PHD 2003 Univ of Michigan at Ann Arbor
    ## 52                  Plant Pathology    PHD 1987 VA Polytechnic Inst & State U
    ## 53                       Pediatrics                   MD 1980 Duke University
    ## 54               French And Italian                 PHD 2002 Emory University
    ## 55              Engineering Physics       PHD 2005 Georgia Inst of Technology
    ## 56                          English                  PHD 2006 Duke University
    ## 57       Electrical & Computer Engr         MS 1983 Univ of Wisconsin-Madison
    ## 58         Gender And Women Studies        PHD 2002 Univ of Wisconsin-Madison
    ## 59      Mead Witter School Of Music     PHD 2002 Cleveland Institute Of Music
    ## 60                 Academic Affairs        PHD 2006 Univ of Wisconsin-Madison
    ## 61                        Marketing    PHD 1996 Pennsylvania State University
    ## 62    Engr Professional Development        PHD 2013 Univ of Wisconsin-Madison
    ## 63                 Medical Sciences        DVM 2003 Michigan State University
    ## 64           Spanish And Portuguese             PHD Univ of Wisconsin-Madison
    ## 65                     Bacteriology                PHD 2007 Baylor University
    ## 66              Integrative Biology        PHD 1999 Univ of Wisconsin-Madison
    ## 67                     Biochemistry               PHD 1982 Indiana University
    ## 68                              Art        PHD 2018 Univ of Wisconsin-Madison
    ## 69                          English               PHD 2011 Indiana University
    ## 70               Information School        MS 2007 Georgia Inst of Technology
    ## 71                       Statistics                  PHD 2019 Ohio University
    ## 72    Rehab Psychology & Special Ed             PHD 2018 University of Kansas
    ## 73                     Bacteriology    PHD 2014 Univ of Michigan at Ann Arbor
    ## 74           Spanish And Portuguese        PHD 2004 Univ of Wisconsin-Madison
    ## 75          German, Nordic & Slavic           PHD 2015 University of Helsinki
    ## 76       Electrical & Computer Engr        PHD 1984 Univ of Wisconsin-Madison
    ## 77                      Mathematics                  PHD 2005 Duke University
    ## 78    Community & Environ Sociology        PHD 2019 Univ of Wisconsin-Madison
    ## 79                          Nursing        PHD 2006 Univ of Wisconsin-Madison
    ## 80           Mechanical Engineering        PHD 1998 Univ of Wisconsin-Madison
    ## 81             Nutritional Sciences         MS 1995 Univ of Wisconsin-Madison
    ## 82                   Administration    PHD 1982 Univ of Minnesota-Twin Cities
    ## 83                         Medicine   PHD 1999 Univ of Dublin-Trinity College
    ## 84                         Medicine         MD 1992 Univ of Missouri-Columbia
    ## 85                      Kinesiology    PHD 2015 Univ of Alabama at Birmingham
    ## 86                        Geography   PHD 2014 University Of Texas At El Paso
    ## 87           Mechanical Engineering                  PHD 2019 Duke University
    ## 88                 Consumer Science        MBA 2004 Univ of Wisconsin-Madison
    ## 89                      Mathematics      PHD 2010 Univ of California Berkeley
    ## 90                      Art History           PHD 2001 University of Delaware
    ## 91                           Botany     PHD 2000 U de Toulouse II (Le Mirail)
    ## 92                     Bacteriology     PHD 2002 U de Toulouse II (Le Mirail)
    ## 93   Biological Systems Engineering         PHD 1995 Univ of California Davis
    ## 94                      Mathematics             PHD 1986 State Univ Of Leiden
    ## 95                 Medical Sciences     DVM 1999 Univ Ncnl Autonoma de Mexico
    ## 96          School Of Human Ecology   MFA 1991 Sch Of The Art Inst Of Chicago
    ## 97                         Agronomy         MS 2020 Univ of Wisconsin-Madison
    ## 98                          Nursing     MSN 2007 Univ of Wisconsin-Eau Claire
    ## 99                    Asian Studies                                    M.PHIL
    ## 100            Nutritional Sciences         BS 2013 Univ of Wisconsin-Madison
    ## 101                    Biochemistry          PHD 1995 Northwestern University
    ## 102         Obstetrics & Gynecology           MD 2008 University Of Rochester
    ## 103  Engineering Student Developmnt       MS 1996 Univ of Wisconsin-Green Bay
    ## 104                         History              PHD 1971 Columbia University
    ## 105                      Law School                  PHD 2017 Yale University
    ## 106   Real Estate & Urgan Land Econ                   PHD Stanford University
    ## 107         Comparative Biosciences        PHD 2002 Univ of Wisconsin-Madison
    ## 108                         English         MA 1972 Univ of Wisconsin-Madison
    ## 109                     Mathematics                    PHD Harvard University
    ## 110          Spanish And Portuguese            PHD 2011 Georgetown University
    ## 111              French And Italian           PHD 2013 University of Virginia
    ## 112                 Volunteer Staff         MD 2005 Univ of Wisconsin-Madison
    ## 113   Materials Science&Engineering          PHD 2006 Northwestern University
    ## 114                Small Animal Iii        DPT 1994 Univ of Wisconsin-Madison
    ## 115                       Marketing            PHD 1995 Ohio State University
    ## 116               Computer Sciences      PHD 1998 Univ of California Berkeley
    ## 117               Computer Sciences      PHD 1998 Univ of California Berkeley
    ## 118                    Soil Science        PHD 2000 Univ of Wisconsin-Madison
    ## 119       Animal And Dairy Sciences    PHD 2013 VA Polytechnic Inst & State U
    ## 120                             Art   MFA 2000 Pennsylvania Acad Of Fine Arts
    ## 121        Pathobiological Sciences                                  PHD 2014
    ## 122              Communication Arts          PHD 1998 Northwestern University
    ## 123         School Of Human Ecology      PHD 2014 Univ of California Berkeley
    ## 124          Biomedical Engineering      PHD 2007 Rensselaer Polytechnic Inst
    ## 125      Asian Languages & Cultures              EDD 2015 University of Leeds
    ## 126          Educational Psychology               PHD 1995 University of Iowa
    ## 127             Integrative Biology        PHD 1994 Univ of Wisconsin-Madison
    ## 128                        Medicine         PHD 2000 Johns Hopkins University
    ## 129                         Nursing                 MSN 2009 Edgewood College
    ## 130                      Law School          PHD 1995 University of Cambridge
    ## 131                    Biochemistry     PHD 1980 Univ of California San Diego
    ## 132                    Horticulture               PHD 2012 Cornell University
    ## 133          Biomolecular Chemistry     PHD 2002 Univ of California San Diego
    ## 134  Liberal Arts & Applied Studies         PHD 1981 University of Washington
    ## 135                      Psychology    PHD 1998 Univ of Massachusetts Amherst
    ## 136                     Dermatology      MD 1997 Medical College Of Wisconsin
    ## 137            Madison Microbiology        PHD 2010 Univ of Wisconsin-Madison
    ## 138              Information School        MS 2003 Carnegie-Mellon University
    ## 139                     Kinesiology      PHD 2009 Univ of Southern California
    ## 140                      Psychology      PHD 2012 Univ of California Berkeley
    ## 141                       Radiology          MD 2005 University of Washington
    ## 142               Political Science            PHD 2004 Georgetown University
    ## 143               Computer Sciences     PHD 2009 Uni Pierre&Marie Curie Paris
    ## 144                        Pharmacy           PHD Univ of Illinois at Chicago
    ## 145                         English        PHD 2011 Univ of Wisconsin-Madison
    ## 146                 Theatre & Drama         MFA 2014 University of Cincinnati
    ## 147                      Pediatrics          MD 2012 University of Cincinnati
    ## 148   Operations & Information Mgmt    PHD 2020 Univ of Minnesota-Twin Cities
    ## 149   Materials Science&Engineering       PHD 1987 Massachusetts Inst Of Tech
    ## 150               Computer Sciences      PHD 1984 Univ of California Berkeley
    ## 151                Medical Sciences        DVM 2000 Univ Of Minnesota-St Paul
    ## 152            Nutritional Sciences                MPH 2008 Tulane University
    ## 153  Atmospheric & Oceanic Sciences         PHD 2007 University of Washington
    ## 154      Civil & Environmental Engr    PHD 1991 Pennsylvania State University
    ## 155                         Physics                       PHD Yale University
    ## 156  Admin:Student Academic Affairs    MA 2013 Clg of William & Mary-Virginia
    ## 157                      Law School                                   JD 2013
    ## 158                       Geography   PHD 2008 University of British Columbia
    ## 159                         Nursing         MS 2009 Univ of Wisconsin-Madison
    ## 160      Curriculum And Instruction        PHD 1997 Univ of Wisconsin-Madison
    ## 161         Comparative Biosciences        PHD 2001 Univ of Wisconsin-Madison
    ## 162  Civil Society And Comm Studies        PHD 1998 Univ of Wisconsin-Madison
    ## 163                      Psychiatry     PHD 1998 Univ of California San Diego
    ## 164   Rehab Psychology & Special Ed         PHD 2009 Arizona State University
    ## 165                         Physics                  PHD 1982 Yale University
    ## 166                             Art            PHD 1994 University of Warwick
    ## 167                      Psychiatry     PHD 1998 Univ of California San Diego
    ## 168      Educational Policy Studies              PHD 2012 Columbia University
    ## 169           Counseling Psychology      EDM 2016 Univ of Wisconsin-La Crosse
    ## 170           Ft Mba Program Office                                  MBA 2013
    ## 171             Integrative Biology     PHD 2017 George Washington University
    ## 172                    Soil Science              PHD 1999 University of Idaho
    ## 173                         History               PHD 2018 Harvard University
    ## 174               Computer Sciences    PHD 2003 Univ of MD-University College
    ## 175                  Anesthesiology        PHD 1992 Univ of Wisconsin-Madison
    ## 176                    Soil Science   PHD 1987 Hebrew University of Jerusalem
    ## 177                 Plant Pathology         PHD 2000 Univ of California Davis
    ## 178                      Law School              JD 2006 Marquette University
    ## 179        Gender And Women Studies    PHD 2016 Univ of Massachusetts Amherst
    ## 180                        Medicine       MD 1989 Univ of Illinois at Chicago
    ## 181   Sustainability&Global Environ               PHD 1997 Harvard University
    ## 182               Computer Sciences                PHD 2000 Boston University
    ## 183                       Astronomy          PHD 1997 University of Cambridge
    ## 184                         Physics     PHD 1963 Pennsylvania State U-Hershey
    ## 185  Agricultural&Applied Economics              PHD 1988 Stanford University
    ## 186   Engr Professional Development                         JD Boston College
    ## 187                Risk & Insurance         JD 2009 Univ of Wisconsin-Madison
    ## 188      Asian Languages & Cultures    PHD 2004 Leeds Metropolitan University
    ## 189           Ft Mba Program Office                                  PHD 2002
    ## 190                     Kinesiology    PHD 2009 University of Texas at Austin
    ## 191                        Pharmacy     PHARMD 2004 Univ of Wisconsin-Madison
    ## 192                 Family Medicine        PHD 1992 Univ of Wisconsin-Madison
    ## 193                          Botany        PHD 2019 Univ of Wisconsin-Madison
    ## 194                       Sociology        PHD 1997 Univ of Wisconsin-Madison
    ## 195                         English    MFA 1997 Univ of Michigan at Ann Arbor
    ## 196                             Art           BA 1978 Evergreen State College
    ## 197       Planning & Landscape Arch        PHD 2003 Rutgers State Univ-Newark
    ## 198                       Chemistry   PHD 2007 University of British Columbia
    ## 199         School Of Human Ecology        PHD 1997 Univ of Wisconsin-Madison
    ## 200              Accting & Info Sys       MACC 2020 Univ of Wisconsin-Madison
    ## 201        Pathobiological Sciences        PHD 2004 Univ of Wisconsin-Madison
    ## 202               Surgical Sciences        DVM 2017 Univ of Wisconsin-Madison
    ## 203                      Pediatrics             MD 1995 University of Arizona
    ## 204      Educational Policy Studies        PHD 2001 Univ Of NC At Chapel Hill
    ## 205             Engineering Physics         DS 2013 Univ of Wisconsin-Madison
    ## 206       Planning & Landscape Arch        MS 1989 University of North Dakota
    ## 207                        Pharmacy     PHD 1999 California Institute of Tech
    ## 208            Neurological Surgery                 MD 1987 Ankara University
    ## 209                       Chemistry        PHD 2010 University Of Mississippi
    ## 210                     Mathematics              PHD 2019 Stanford University
    ## 211   Operations & Information Mgmt       PHD 2013 University of Pennsylvania
    ## 212         Biology Core Curriculum   PHD 1998 Univ of IL at Urbana-Champaign
    ## 213                      Pediatrics                MD 2012 University of Iowa
    ## 214                      Geoscience       PHD 2017 Massachusetts Inst Of Tech
    ## 215                Risk & Insurance                   DS 2007 Universitat Ulm
    ## 216       Planning & Landscape Arch                MA 2003 Harvard University
    ## 217                          Botany            PHD 1991 Washington University
    ## 218                      Statistics                                  MS2 2009
    ## 219      Population Health Sciences         PHD 1993 Johns Hopkins University
    ## 220   Operations & Information Mgmt       PHD 2014 University of Pennsylvania
    ## 221                  Human Oncology     PHD 1993 Univ of TX Health Sci Center
    ## 222                       Neurology            PHD 2008 Vanderbilt University
    ## 223         School Of Human Ecology               PHD 2019 Cornell University
    ## 224  Agricultural&Applied Economics         MS 2011 Univ of Wisconsin-Madison
    ## 225                 Family Medicine      MD 1999 Loyola University of Chicago
    ## 226                      Statistics      PHD 2014 Univ of California Berkeley
    ## 227                         English              PHD 2006 New York University
    ## 228               Academic Programs       PHD 1998 Massachusetts Inst Of Tech
    ## 229                         Physics              PHD 2012 Stanford University
    ## 230                Academic Affairs              MA Univ of Wisconsin-Madison
    ## 231                             Art         MA Sch Of The Art Inst Of Chicago
    ## 232                   Asian Studies        PHD 2016 Univ of Wisconsin-Madison
    ## 233                    Biochemistry        PHD 1992 Michigan State University
    ## 234                 Medical Physics      PHD 2008 Rensselaer Polytechnic Inst
    ## 235   Pathology&Laboratory Medicine        PHD 1994 Univ of Wisconsin-Madison
    ## 236                Academic Affairs      MS 2004 Univ of Wisconsin-Whitewater
    ## 237                         English           PHD 1989 University of Virginia
    ## 238      Electrical & Computer Engr    PHD 2006 Univ of Michigan at Ann Arbor
    ## 239           Counseling Psychology        PSYD 2014 North Central University
    ## 240              Information School       MLIS 2016 Univ of Wisconsin-Madison
    ## 241     Mead Witter School Of Music                                     OQUAL
    ## 242          Spanish And Portuguese            PHD 1998 University of Chicago
    ## 243                     Kinesiology        PHD 2010 Univ Of NC At Chapel Hill
    ## 244   Community & Environ Sociology                  PHD 1992 Yale University
    ## 245   Engr Professional Development                                        MS
    ## 246          Educational Psychology        PHD 2001 University of Connecticut
    ## 247                     Mathematics         PHD 2017 University of Birmingham
    ## 248             Integrative Biology         PHD 1991 Arizona State University
    ## 249                        Medicine     MD 2004 Univ of Minnesota-Twin Cities
    ## 250                        Medicine            PHD 2006 University of Arizona
    ## 251   Classic & Ancient Near E Stds        PHD 2002 Univ Of NC At Chapel Hill
    ## 252                      Philosophy    PHD 2010 University of Texas at Austin
    ## 253                     Mathematics        PHD 2014 Univ of Wisconsin-Madison
    ## 254                      Psychology            PHD 1996 University Of Memphis
    ## 255                      Law School         JD 2008 Univ of Wisconsin-Madison
    ## 256                        Medicine                 MD 2002 Dartmouth College
    ## 257                 Plant Pathology       PHD 1989 Massachusetts Inst Of Tech
    ## 258               Surgical Sciences            DVM 1993 University of Florida
    ## 259                         Surgery                 MD 1984 Temple University
    ## 260                     Social Work              PHD 2002 Columbia University
    ## 261                         Physics              PHD 1994 SUNY At Stony Brook
    ## 262       Forest & Wildlife Ecology    PHD 1997 VA Polytechnic Inst & State U
    ## 263      Curriculum And Instruction          PHD 2008 Northwestern University
    ## 264      Curriculum And Instruction          PHD 2008 Northwestern University
    ## 265        Pathobiological Sciences        PHD 1995 Univ of Wisconsin-Madison
    ## 266                         English              PHD 1991 SUNY At Stony Brook
    ## 267   Cooperatives, Univ Center For         MS 2011 Univ of Wisconsin-Madison
    ## 268                      Pediatrics         MD 1989 Univ of Wisconsin-Madison
    ## 269                      Psychology            PHD 1988 University of Florida
    ## 270                       Chemistry           PHD 2004 Texas A & M University
    ## 271                       Astronomy            PHD 1992 University of Chicago
    ## 272          Mechanical Engineering           PHD 2007 Ecole Centrale de Lyon
    ## 273          Biomedical Engineering        PHD 1976 Univ of Wisconsin-Madison
    ## 274                 Theatre & Drama          BFA Univ of Wisconsin-Whitewater
    ## 275                     Kinesiology                  PHD 2007 Yale University
    ## 276                       Chemistry      PHD 2006 Univ of California Berkeley
    ## 277   Rehab Psychology & Special Ed        PHD 1973 Univ of Wisconsin-Madison
    ## 278                     Amer Ind St         BA 2019 Univ of Wisconsin-Madison
    ## 279                         English         MA 2009 Univ of Wisconsin-Madison
    ## 280                    Horticulture      PHD 1995 Univ of California Berkeley
    ## 281  Ms In Biotechnology Degree Prg     PHD 1992 Univ of Nebraska Medical Ctr
    ## 282   Cell And Regenerative Biology         PHD 1993 University of Cincinnati
    ## 283               Political Science              PHD 2010 Stanford University
    ## 284       Industrial & Systems Engr       PHD 1983 Massachusetts Inst Of Tech
    ## 285          Spanish And Portuguese               PHD 1990 University of Iowa
    ## 286                      Law School         JD 1993 Univ of Wisconsin-Madison
    ## 287                  Anesthesiology     MD 1999 Johannes Gutenburg Univ Mainz
    ## 288                      Law School         JD 2001 Univ of Wisconsin-Madison
    ## 289         Obstetrics & Gynecology             PHD 1987 University of London
    ## 290                      Pediatrics         MS 2007 Univ of Wisconsin-Madison
    ## 291                      Psychiatry     PHD 1999 Medical College Of Wisconsin
    ## 292                     Social Work         PHD 2015 University of Pittsburgh
    ## 293   Rehab Psychology & Special Ed        PHD 2000 Univ of Wisconsin-Madison
    ## 294                         English            MFA 2010 University Of Houston
    ## 295                         History      PHD 2011 Univ of California Berkeley
    ## 296      Curriculum And Instruction        PHD 2019 Univ of Wisconsin-Madison
    ## 297               Surgical Sciences   DVM 1978 Univ of IL at Urbana-Champaign
    ## 298                         Physics                PHD 2005 Boston University
    ## 299                       Chemistry     PHD 1999 California Institute of Tech
    ## 300             Integrative Biology      PHD 1982 Univ of California Berkeley
    ## 301                  Anesthesiology         MD 2006 Univ of Wisconsin-Madison
    ## 302                         Nursing                 MSN 2010 Edgewood College
    ## 303     Mead Witter School Of Music             PHD 1994 Princeton University
    ## 304           Cals Academic Affairs         MS 2010 Univ of Wisconsin-Madison
    ## 305                    Soil Science               PHD 1984 Cornell University
    ## 306               Surgical Sciences   DVM 2005 Univ of IL at Urbana-Champaign
    ## 307                         History               PHD 2018 Harvard University
    ## 308      Civil & Environmental Engr       PHD 2006 Univ of Colorado at Denver
    ## 309                       Chemistry        PHD 2012 Univ of Wisconsin-Madison
    ## 310          Biomedical Engineering              PHD 1998 Stanford University
    ## 311                Academic Affairs                    DPT Arcadia University
    ## 312              Information School            MS 1981 Wayne State University
    ## 313       Planning & Landscape Arch         MS 2000 Univ of Wisconsin-Madison
    ## 314   Cell And Regenerative Biology   PHD 2009 Hebrew University of Jerusalem
    ## 315      Civil & Environmental Engr                                       PHD
    ## 316                       Marketing         MS 2002 Univ of Wisconsin-Madison
    ## 317      Civil & Environmental Engr         BS 2000 Univ of Wisconsin-Madison
    ## 318    Madison Pathology/Toxicology               PHD 1989 Cornell University
    ## 319    Management & Human Resources                 MBA 1991 Edgewood College
    ## 320                     Social Work        MSW 1988 Univ of Wisconsin-Madison
    ## 321  Erdman Ctr For Ops & Tech Mgmt                 MBA 1991 Edgewood College
    ## 322   Cell And Regenerative Biology        PHD 1991 Univ of Wisconsin-Madison
    ## 323         Obstetrics & Gynecology        PHD 2013 Univ of Wisconsin-Madison
    ## 324               Political Science    PHD 2019 Louisiana State U-Baton Rouge
    ## 325                     Social Work         JD 1982 Univ of Wisconsin-Madison
    ## 326                 Volunteer Staff        PHD 2013 Univ of Wisconsin-Madison
    ## 327                         Physics             PHD 1999 Princeton University
    ## 328                    Food Science        PHD 2007 Univ of Wisconsin-Madison
    ## 329          Educational Psychology   PHD 1999 Univ of IL at Urbana-Champaign
    ## 330                       Neurology          PHD Universite de l'Etat a Liege
    ## 331                         Nursing            MSN 2005 University of Phoenix
    ## 332                      Geoscience        PHD 2013 Univ of Wisconsin-Madison
    ## 333             Engineering Physics     PHD 1992 California Institute of Tech
    ## 334                 Family Medicine      MD 2009 Loyola University of Chicago
    ## 335   Engr Professional Development        PHD 2014 North Carolina State Univ
    ## 336      Electrical & Computer Engr    PHD 1985 Univ of Michigan at Ann Arbor
    ## 337               Academic Programs        PHD 2011 Univ of Wisconsin-Madison
    ## 338   Communication Sci & Disorders       PHD 2014 Trinity Western University
    ## 339         German, Nordic & Slavic                                        MA
    ## 340                         Physics              PHD 2007 Columbia University
    ## 341                    Soil Science        PHD 2018 Univ of Wisconsin-Madison
    ## 342                         History      PHD 1988 Univ of California Berkeley
    ## 343                Integ Liberal St        PHD 2012 Univ of Wisconsin-Madison
    ## 344      Electrical & Computer Engr      PHD 1976 Univ of California Berkeley
    ## 345     Life Sciences Communication      BS 1983 Univ of Wisconsin-Whitewater
    ## 346    Wisconsin School Of Business         JD 1977 Univ of Wisconsin-Madison
    ## 347                     Social Work       MSSW 2005 Univ of Wisconsin-Madison
    ## 348                      Geoscience    PHD 1995 Univ of Michigan at Ann Arbor
    ## 349    Wisconsin School Of Business        PHD 2018 Univ of Wisconsin-Madison
    ## 350              French And Italian    PHD 1983 U de Provence Aix-Marseille I
    ## 351       Industrial & Systems Engr                 PHD University of Toronto
    ## 352                         English    PHD 1993 Univ of California Santa Cruz
    ## 353       Forest & Wildlife Ecology        PHD 2000 Virginia State University
    ## 354                      Law School                   JD 2002 Yale University
    ## 355          Mechanical Engineering        PHD 1992 Univ of Wisconsin-Madison
    ## 356                         Nursing    PHD 1984 U of California San Francisco
    ## 357                    Anthropology            PHD 1988 University of Chicago
    ## 358                         English      PHD 2018 City University Of New York
    ## 359                       Chemistry        PHD 2006 Univ of Wisconsin-Madison
    ## 360                       Chemistry    PHD 2007 University of Texas at Austin
    ## 361                       Radiology        PHD 2005 Univ of Wisconsin-Madison
    ## 362                       Marketing              MA 1990 Marquette University
    ## 363                          Botany        PHD 2014 Univ of Wisconsin-Madison
    ## 364                         Surgery         MS 2006 Univ of Wisconsin-Madison
    ## 365                        Oncology      PHD 1986 Univ of California Berkeley
    ## 366                  Human Oncology         MD 1999 Univ of Wisconsin-Madison
    ## 367   A.C. Nielsen Ctr For Mkt Rsch        MBA 2002 Univ of Wisconsin-Madison
    ## 368                     Kinesiology        PHD 1996 Univ of Wisconsin-Madison
    ## 369   Ophthalmology&Visual Sciences              PHD 1984 Columbia University
    ## 370         German, Nordic & Slavic                  PHD 1987 Yale University
    ## 371                         Physics      PHD 2010 Univ of California Berkeley
    ## 372                        Medicine     MD 1983 U of California San Francisco
    ## 373                         Nursing        PHD 2009 Univ of Wisconsin-Madison
    ## 374                      Psychology      PHD 1994 Univ of Colorado at Boulder
    ## 375                     Social Work       MSSW 1982 Univ of Wisconsin-Madison
    ## 376                          Botany        PHD 2020 Univ of Wisconsin-Madison
    ## 377                      Law School                  PHD 2017 Yale University
    ## 378              Information School    MLIS 1993 Northern Illinois University
    ## 379                      Law School                                   JD 2010
    ## 380                     Social Work        MSW 2012 Univ of Wisconsin-Madison
    ## 381   Real Estate & Urgan Land Econ          BS 1979 University of Notre Dame
    ## 382               Ctr For Jewish St                  PHD 1986 York University
    ## 383             Integrative Biology        PHD 2013 Univ of Wisconsin-Madison
    ## 384                        Pharmacy         BS 1975 Univ of Wisconsin-Madison
    ## 385   Cell And Regenerative Biology    PHD 1989 Univ of Michigan at Ann Arbor
    ## 386          Madison Administration        DMV 2012 Univ of Wisconsin-Madison
    ## 387             Integrative Biology         MS 2018 Univ of Wisconsin-Madison
    ## 388           Counseling Psychology     MA 2012 University of Texas at Austin
    ## 389                      Philosophy      PHD 1991 Univ of Southern California
    ## 390              Information School     MLIS 2014 Univ of Wisconsin-Milwaukee
    ## 391                         English              PHD 2000 University of Leeds
    ## 392                      Law School                JD 1989 Harvard University
    ## 393   Classic & Ancient Near E Stds                  PHD 2012 Yale University
    ## 394   Biostatistics&Med Informatics      PHD 1997 Univ of California Berkeley
    ## 395             Engineering Physics       PHD 1991 Massachusetts Inst Of Tech
    ## 396               Political Science    PHD 2015 University of Texas at Austin
    ## 397   Pathology&Laboratory Medicine         MD 2005 Univ of Wisconsin-Madison
    ## 398            Neurological Surgery      MD 2002 Medical College Of Wisconsin
    ## 399               Surgical Sciences          DVM 2011 Kansas State University
    ## 400     Life Sciences Communication               PHD 2002 Cornell University
    ## 401               Surgical Sciences               DVM 1999 Utrecht University
    ## 402          Biomolecular Chemistry     PHD 1986 Univ of California San Diego
    ## 403          Educational Psychology            PHD 1979 University of Chicago
    ## 404                         Finance              PHD 1984 Stanford University
    ## 405                      Law School               JD 2007 New York University
    ## 406         Obstetrics & Gynecology                  MD 2006 Brown University
    ## 407                     Kinesiology      PHD 2013 Univ of Southern California
    ## 408      Population Health Sciences       PHD 2010 Univ of Tennessee, Memphis
    ## 409                         Surgery             PHD Univ of Wisconsin-Madison
    ## 410        African Cultural Studies        PHD 2014 Univ of Wisconsin-Madison
    ## 411                 Family Medicine          MD 1996 University of Washington
    ## 412                     Social Work       MSSW 1999 Univ of Wisconsin-Madison
    ## 413                        Genetics      PHD 2015 Univ of California Berkeley
    ## 414                       Chemistry                PHD 1997 Universitat Berne
    ## 415                         Nursing        DNP 2012 Univ of Wisconsin-Madison
    ## 416       Forest & Wildlife Ecology         MS 2015 Univ of Wisconsin-Madison
    ## 417              French And Italian                 PHD 1988 Brown University
    ## 418                       Chemistry         DS 2018 Univ of Wisconsin-Madison
    ## 419                      Law School         JD 1993 Univ of Wisconsin-Madison
    ## 420                       Geography            MA 2016 Alfred Adler Institute
    ## 421           Counseling Psychology        PHD 2011 Univ of Wisconsin-Madison
    ## 422                        Pharmacy               PHD 2003 University of Utah
    ## 423                       Marketing        MBA 2003 Univ of Wisconsin-Madison
    ## 424      Asian Languages & Cultures                 PHD 1980 Universitat Wien
    ## 425   Communication Sci & Disorders            AUD 2006 University of Florida
    ## 426                             Art    MFA 1996 Univ of Minnesota-Twin Cities
    ## 427                       Chemistry         PHD 2013 Johns Hopkins University
    ## 428      Curriculum And Instruction         PHD 2013 Georgia State University
    ## 429               Academic Programs               PHD 2017 Cornell University
    ## 430                    Anthropology      PHD 1982 Univ of California Berkeley
    ## 431               Political Science            PHD 1998 Ohio State University
    ## 432                       Neurology       PHD 1994 Univ of Colorado at Denver
    ## 433                        Oncology               PHD 1969 Harvard University
    ## 434              Accting & Info Sys       MACC 2020 Univ of Wisconsin-Madison
    ## 435       Forest & Wildlife Ecology   PHD 2015 Eidgenossische Tec Hoch Zurich
    ## 436                      Psychology                PHD 1998 Auburn University
    ## 437                        Medicine          PHD 2001 University Of Rochester
    ## 438  Human Development&Family Study        PHD 2003 Univ of Wisconsin-Madison
    ## 439                     Social Work        MSW 2004 Univ of Wisconsin-Madison
    ## 440                         Surgery              PHD 1979 Syracuse University
    ## 441                        Pharmacy       EDD 2014 St Marys Univ of Minnesota
    ## 442      Population Health Sciences        PHD 2008 Univ of Wisconsin-Madison
    ## 443                       Chemistry   PHD 1986 Univ of California Los Angeles
    ## 444   Ed Leadership&Policy Analysis                 PHD 2014 University of MI
    ## 445                Medical Sciences            PHD 2014 University of Georgia
    ## 446                    Bacteriology       PHD 2003 Massachusetts Inst Of Tech
    ## 447               Political Science         PHD 2020 University of Notre Dame
    ## 448                     Mathematics     PHD 2020 Univ of Tennessee, Knoxville
    ## 449                 Family Medicine                                        MS
    ## 450                        Medicine         MD 1966 Univ of Wisconsin-Madison
    ## 451                         History     MA 2019 Univ of Minnesota-Twin Cities
    ## 452                    Biochemistry            PHD 1995 University of Vermont
    ## 453                             Art         BS 2018 Univ of Wisconsin-Madison
    ## 454     Mead Witter School Of Music            PHD 2000 Ohio State University
    ## 455                       Economics                  PHD 2019 Yale University
    ## 456                         Nursing        PHD 2014 Univ of Wisconsin-Madison
    ## 457                Consumer Science                                        MA
    ## 458                           Dance                 MS 2009 Drexel University
    ## 459       Animal And Dairy Sciences            PHD 2004 University of Florida
    ## 460         Comparative Biosciences          PHD 2011 Northwestern University
    ## 461                     Art History      PHD 1991 Univ of California Berkeley
    ## 462               Computer Sciences               PHD 1986 Cornell University
    ## 463                       Radiology     PHD 2004 Univ of California San Diego
    ## 464                     Mathematics               PHD 2000 Cornell University
    ## 465                    Horticulture        PHD 2010 Univ of Wisconsin-Madison
    ## 466     Mead Witter School Of Music          MM 1975 Univ Of NC At Greensboro
    ## 467                      Psychology             PHD 1988 University of Denver
    ## 468                         English           PHD 2012 University of Delaware
    ## 469                         History          PHD 2012 Northwestern University
    ## 470         German, Nordic & Slavic               PHD 1982 Harvard University
    ## 471                    Anthropology            PHD 2011 Washington University
    ## 472                 Theatre & Drama          MFA Univ of California San Diego
    ## 473                          Botany        PHD 1996 Univ Of NC At Chapel Hill
    ## 474                Medical Sciences             BVM 2009 University of London
    ## 475   Real Estate & Urgan Land Econ            MBA 1992 Washington University
    ## 476          Biomedical Engineering                  PHD 1992 Yale University
    ## 477        Gender And Women Studies        MFA 2006 Univ of Wisconsin-Madison
    ## 478                Military Science                 BS 2021 Excelsior College
    ## 479               Political Science    PHD 1987 Univ of Minnesota-Twin Cities
    ## 480                    Biochemistry    PHD 2010 University of Texas at Austin
    ## 481              Accting & Info Sys       MACC 2020 Univ of Wisconsin-Madison
    ## 482                      Pediatrics           MD 2002 University Of Rochester
    ## 483               Computer Sciences                  MS 2015 Edgewood College
    ## 484       Industrial & Systems Engr        PHD 1988 Univ of Wisconsin-Madison
    ## 485               Computer Sciences        PHD 2016 Univ of Wisconsin-Madison
    ## 486                         Surgery        MD 2006 Virginia Commonwealth Univ
    ## 487                     Kinesiology        PHD 1990 Univ of Wisconsin-Madison
    ## 488                      Geoscience              PHD 2010 Stanford University
    ## 489         Comparative Biosciences         PHD 1983 Univ of California Davis
    ## 490   Ed Leadership&Policy Analysis        PHD 2004 Michigan State University
    ## 491                         Physics            PHD 1984 University of Chicago
    ## 492      Civil & Environmental Engr                                   MS 1988
    ## 493                       Sociology    PHD 1999 Univ of Michigan at Ann Arbor
    ## 494                        Medicine     MD 1995 Univ of Michigan at Ann Arbor
    ## 495                         History        PHD 2006 Univ of Wisconsin-Madison
    ## 496                      Law School                JD 2002 University of Iowa
    ## 497                Medical Sciences                                   MS 2018
    ## 498                      Geoscience              PHD 1991 Stanford University
    ## 499                             Art        PHD 2018 Univ of Wisconsin-Madison
    ## 500                      Law School                   MA 1968 Yale University
    ## 501                         Centers               PHD 2010 Harvard University
    ## 502   Journalism&Mass Communication       PHD 2017 University of Pennsylvania
    ## 503                     Art History               PHD 1999 Harvard University
    ## 504                      Law School               JD 1999 Stanford University
    ## 505                         English    PHD 1992 Univ of California Santa Cruz
    ## 506                         Nursing     MSN 2000 Loyola University of Chicago
    ## 507                        Medicine      MD 1996 Loyola University of Chicago
    ## 508   Communication Sci & Disorders      MS 2005 Univ of Wisconsin-Eau Claire
    ## 509                       Chemistry     PHD 1996 California Institute of Tech
    ## 510                Medical Sciences        DVM 2017 Univ of Wisconsin-Madison
    ## 511         German, Nordic & Slavic        PHD 2016 Univ of Wisconsin-Madison
    ## 512                      Pediatrics                MD 1996 Marmara University
    ## 513                Military Science                MS 2011 Capella University
    ## 514          Spanish And Portuguese   PHD 2008 Univ of IL at Urbana-Champaign
    ## 515                   Naval Science              BA 2013 Marquette University
    ## 516      Asian Languages & Cultures            PHD 2007 University of Chicago
    ## 517                       Neurology      MD 2000 Medical College Of Wisconsin
    ## 518                         Surgery        MD 2007 Baylor College Of Medicine
    ## 519  Orthopedics And Rehabilitation        PHD 2010 Univ of Wisconsin-Madison
    ## 520           Counseling Psychology            EDD 1990 University of Florida
    ## 521                         History              PHD 2013 Columbia University
    ## 522                       Economics   PHD 2008 Univ of California Los Angeles
    ## 523     Mead Witter School Of Music            PHD 2018 University of Chicago
    ## 524                     Social Work             MA 1990 University of Chicago
    ## 525      Department Of Neuroscience                            PHD 1998 India
    ## 526                     Mathematics        PHD 1993 Univ of Wisconsin-Madison
    ## 527          Nicholas Ctr For Cf&Ib             JD 2007 University of Chicago
    ## 528                         Finance          PHD 2012 Northwestern University
    ## 529                     Dermatology     PHD 2008 Univ of TX Health Sci Center
    ## 530                       Wiscience         MS 2018 Univ of Wisconsin-Madison
    ## 531                        Genetics       PHD 2000 University of Pennsylvania
    ## 532                     Mathematics    PHD 2019 Louisiana State U-Baton Rouge
    ## 533      Department Of Neuroscience         PHD 1992 University of Washington
    ## 534                        Medicine         MD 2008 Univ of Wisconsin-Madison
    ## 535                      Statistics            PHD 1990 University of Chicago
    ## 536                     Social Work        PHD 2009 Univ Of NC At Chapel Hill
    ## 537                      Law School               JD 1982 Columbia University
    ## 538               Computer Sciences               PHD 2019 Cornell University
    ## 539                         English        MFA 2015 North Carolina State Univ
    ## 540  Agricultural&Applied Economics        PHD 1978 Univ of Missouri-Columbia
    ## 541         German, Nordic & Slavic    PHD 1992 University of Texas at Austin
    ## 542      Chemical & Biological Engr               PHD 1985 University of Utah
    ## 543               Computer Sciences       PHD 2005 Carnegie-Mellon University
    ## 544          Mechanical Engineering        PHD 2012 Univ of Wisconsin-Madison
    ## 545                     Mathematics                   PHD SUNY At Stony Brook
    ## 546                 Medical Physics               PHD 2000 University of Utah
    ## 547   Biostatistics&Med Informatics        PHD 2014 Univ Of NC At Chapel Hill
    ## 548                     Kinesiology        PHD 2016 Univ of Wisconsin-Madison
    ## 549     Life Sciences Communication              PHD 2019 Stanford University
    ## 550          Mechanical Engineering        PHD 2009 Zhejiang Univ of Sciences
    ## 551                     Mathematics              PHD 2016 New York University
    ## 552                Military Science                                   MS 2010
    ## 553                         History        PHD 2004 Univ of California Irvine
    ## 554                  Design Studies        MFA 2017 Univ of Wisconsin-Madison
    ## 555       Forest & Wildlife Ecology        PHD 2016 Colorado State University
    ## 556          Biomedical Engineering               PHD 1996 Harvard University
    ## 557                        Pharmacy        PHD 1973 Univ of Wisconsin-Madison
    ## 558                       Economics            PHD 2020 Vanderbilt University
    ## 559                      Statistics       PHD 2006 Georgia Inst of Technology
    ## 560              School For Workers     PHD 2004 Southern IL Univ.-Carbondale
    ## 561  Lafollette Sch Of Publ Affairs      PHD 1991 Univ of California Berkeley
    ## 562     Life Sciences Communication    PHD 2015 Univ of Michigan at Ann Arbor
    ## 563     Mead Witter School Of Music                MM 1973 Indiana University
    ## 564      Department Of Neuroscience         PHD 1977 University of Washington
    ## 565                         English               PHD 2012 University of Iowa
    ## 566  Biological Systems Engineering        PHD 1990 Colorado State University
    ## 567                       Chemistry        PHD 2000 Michigan State University
    ## 568              Accting & Info Sys                 PHD 2011 Emory University
    ## 569                     Art History      PHD 2003 Univ of California Berkeley
    ## 570                   Naval Science                                   MA 2013
    ## 571      Asian Languages & Cultures               MA 2009 University of Leeds
    ## 572             Engineering Physics               PHD 2013 Harvard University
    ## 573                           Dance      MFA 2006 Univ of Wisconsin-Milwaukee
    ## 574                      Law School              JD 1985 Marquette University
    ## 575      Curriculum And Instruction        EDM 2012 Univ of Wisconsin-Madison
    ## 576                 Medical Physics        PHD 1994 Univ of Wisconsin-Madison
    ## 577                    Bacteriology        PHD 2011 Univ of Wisconsin-Madison
    ## 578   Journalism&Mass Communication            PHD 2016 Ohio State University
    ## 579                        Pharmacy                PHD 2001 Purdue University
    ## 580   Rehab Psychology & Special Ed        PHD 2017 Michigan State University
    ## 581                Medical Sciences        DVM 1991 Univ of Wisconsin-Madison
    ## 582                         Physics            PHD 1998 University of Chicago
    ## 583                       Marketing       PHD 2013 Carnegie-Mellon University
    ## 584   Biostatistics&Med Informatics                PHD 2001 McGill University
    ## 585              Accting & Info Sys       MACC 2020 Univ of Wisconsin-Madison
    ## 586                         History              PHD 2011 Stanford University
    ## 587                      Psychiatry       PHD 1993 Scuola Normale Sup de Pisa
    ## 588      Civil & Environmental Engr                                       PHD
    ## 589                      Psychiatry   PHD 2010 Univ of Arkansas, Fayetteville
    ## 590   Communication Sci & Disorders            PHD 2006 University of Arizona
    ## 591      Educational Policy Studies          PHD 2007 Northwestern University
    ## 592         Comparative Biosciences        DVM 2000 Univ of Wisconsin-Madison
    ## 593               Political Science    PHD 1998 U of California-Santa Barbara
    ## 594                             Art        MFA 1983 Rutgers State Univ-Newark
    ## 595                        Medicine     PHD 2014 Univ of California San Diego
    ## 596                      Psychiatry          PHD 1983 Northwestern University
    ## 597                     Kinesiology         MS 2003 Univ of Wisconsin-Madison
    ## 598                     Social Work        MSW 2005 Univ of Wisconsin-Madison
    ## 599           Afro-American Studies               PHD 2006 University of Iowa
    ## 600    Madison Pathology/Toxicology            PHD 2018 University of Georgia
    ## 601                      Philosophy        PHD 2015 Univ of Wisconsin-Madison
    ## 602       Animal And Dairy Sciences          PHD 1989 Kansas State University
    ## 603                       Chemistry        PHS Univ of IL at Urbana-Champaign
    ## 604                    Anthropology         PHD 2009 Arizona State University
    ## 605          Spanish And Portuguese                  PHD 1997 Yale University
    ## 606                Academic Affairs                   MS 2006 Ohio University
    ## 607  Orthopedics And Rehabilitation               PHD 2015 University of Iowa
    ## 608                         Nursing      PHD 2018 Univ of Wisconsin-Milwaukee
    ## 609      Population Health Sciences               PHD 2013 Cornell University
    ## 610                         Nursing     MBA 2005 Univ of Wisconsin-Whitewater
    ## 611      Chemical & Biological Engr    PHD 2001 Univ of Minnesota-Twin Cities
    ## 612                      Pediatrics      MD 2007 Medical College Of Wisconsin
    ## 613                      Psychology         PHD 1976 Brooklyn College Of Cuny
    ## 614             Engineering Physics                PHD Universitat Dusseldorf
    ## 615    Management & Human Resources   PHD 1993 Univ of California Los Angeles
    ## 616                      Psychology            PHD 1994 University of Vermont
    ## 617                      Law School         JD 1980 Univ of Wisconsin-Madison
    ## 618   Communication Sci & Disorders    MA 1990 California State U- Long Beach
    ## 619                       Geography       MS 2007 Rochester Institute Of Tech
    ## 620                      Law School       PHD 2011 University of Pennsylvania
    ## 621                        Pharmacy              PHD 2002 Stanford University
    ## 622                         Nursing      MSN 2013 Cardinal Stritch University
    ## 623         School Of Human Ecology               PHD 2008 Cornell University
    ## 624   Community & Environ Sociology            PHD 1981 University of Florida
    ## 625                Consumer Science         JD 2005 Univ of Wisconsin-Madison
    ## 626        Pathobiological Sciences            PHD 1975 University of Georgia
    ## 627                      Law School         JD 1995 Univ of Wisconsin-Madison
    ## 628   Cell And Regenerative Biology        PHD 1998 Univ of Wisconsin-Madison
    ## 629               Surgical Sciences        PHD 2012 Univ of Wisconsin-Madison
    ## 630                    Horticulture        PHD 2000 Univ of Wisconsin-Madison
    ## 631                     Kinesiology          PHD 2007 Texas Womans University
    ## 632                   Dairy Science        PHD 1985 Univ of Wisconsin-Madison
    ## 633        Strategic Communications        PHD 2015 Univ of Wisconsin-Madison
    ## 634                        Agronomy        PHD 2001 Univ of Wisconsin-Madison
    ## 635                     Social Work       MSSW 2003 Univ of Wisconsin-Madison
    ## 636          Mechanical Engineering         MS 1994 Univ of Wisconsin-Madison
    ## 637   Communication Sci & Disorders        PHD 1997 Univ of Wisconsin-Madison
    ## 638   Ed Leadership&Policy Analysis    PHD 1975 Univ of Michigan at Ann Arbor
    ## 639                 Theatre & Drama             MFA 2017 University of London
    ## 640              Community Dev Inst        PHD 2014 Colorado State University
    ## 641                       Sociology    PHD 2008 U of California-Santa Barbara
    ## 642              Communication Arts   PHD 1999 Univ of California Los Angeles
    ## 643                       Sociology          PHD 2017 Northwestern University
    ## 644                     Kinesiology            PHD 1998 University of Georgia
    ## 645                Medical Sciences            DVM 1992 University of Bristol
    ## 646     Mead Witter School Of Music    PHD 1985 Univ of Michigan at Ann Arbor
    ## 647   Biostatistics&Med Informatics        PHD 1993 Univ of Wisconsin-Madison
    ## 648          Biomolecular Chemistry            PHD 2002 University of Florida
    ## 649                    Bacteriology            PHD 2017 University of Georgia
    ## 650                         English              PHD 2003 Columbia University
    ## 651                     Social Work    MSW 1991 Univ of Michigan at Ann Arbor
    ## 652               Political Science               PHD 2005 Harvard University
    ## 653           Counseling Psychology                                   MS 2016
    ## 654                         Physics               PHD 1983 Cornell University
    ## 655                         Finance                  PHD 1990 Yale University
    ## 656                           Dance   MFA 2007 Univ of IL at Urbana-Champaign
    ## 657                     Mathematics                                  PHD 2018
    ## 658          Spanish And Portuguese    PHD 1982 Univ of Michigan at Ann Arbor
    ## 659      Educational Policy Studies              JD Univ of Wisconsin-Madison
    ## 660                      Psychiatry               PHD 2006 University of Iowa
    ## 661                Academic Affairs       PHD 2011 Case Western Reserve Univ.
    ## 662             Engineering Physics    PHD 2014 Pennsylvania State University
    ## 663                       Wiscience    PHD 2008 Univ of Minnesota-Twin Cities
    ## 664              Accting & Info Sys    PHD 1978 Pennsylvania State University
    ## 665                      Statistics         MS 2018 Univ of Wisconsin-Madison
    ## 666                European Studies   PHD 1998 Calif. State Univ. Los Angeles
    ## 667                      Pediatrics      MD 2008 Loyola University of Chicago
    ## 668                    Biochemistry              PHD 1980 Brandeis University
    ## 669  Agricultural&Applied Economics   PHD 1989 Australian National University
    ## 670                    Biochemistry    PHD 2015 U of California San Francisco
    ## 671                      Law School         JD 1995 Univ of Wisconsin-Madison
    ## 672                Risk & Insurance               MS 1996 Stanford University
    ## 673                     Mathematics            PHD 2002 Ohio State University
    ## 674                    Biochemistry            PHD 1972 Washington University
    ## 675   Communication Sci & Disorders   AUD 2017 Univ of Wisconsin-StevensPoint
    ## 676                      Entomology               PHD 2017 Harvard University
    ## 677               Political Science    PHD 2000 Univ of Michigan at Ann Arbor
    ## 678      Civil & Environmental Engr        PHD 1984 Colorado State University
    ## 679   Biostatistics&Med Informatics        PHD 1996 Univ of Wisconsin-Madison
    ## 680        Pathobiological Sciences                                  PHD 2011
    ## 681       Animal And Dairy Sciences   PHD 1980 University of Nebraska-Lincoln
    ## 682   Ed Leadership&Policy Analysis    EDD 2006 Pennsylvania State University
    ## 683             Engineering Physics    PHD 1998 Univ of Minnesota-Twin Cities
    ## 684                         History                  PHD 1990 Yale University
    ## 685     Mead Witter School Of Music             PHD 1991 Princeton University
    ## 686           Ev Mba Program Office       MS 1983 Rensselaer Polytechnic Inst
    ## 687                         English         MA 2013 Univ of Wisconsin-Madison
    ## 688   Ophthalmology&Visual Sciences         PHD 1987 University of Pittsburgh
    ## 689                        Medicine                MD 1987 Harvard University
    ## 690                 Medical Physics        PHD 2006 Univ of Wisconsin-Madison
    ## 691                   Asian Studies        PHD 1989 Michigan State University
    ## 692               Surgical Sciences          DVM 2000 Kansas State University
    ## 693   Journalism&Mass Communication        PHD 1999 Univ of Wisconsin-Madison
    ## 694                         Physics   PHD 1999 Univ Joseph Fourier Grenoble I
    ## 695                    Bacteriology            PHD 2000 University of Toronto
    ## 696     Mead Witter School Of Music          DMA 2015 Northwestern University
    ## 697                      Psychology         PHD 2000 Florida State University
    ## 698   Community & Environ Sociology         PHD 2003 University of Washington
    ## 699           Cals Academic Affairs         MS 2010 Univ of Wisconsin-Madison
    ## 700      Department Of Neuroscience    PHD 1987 SUNY Health Sci Cntr-Brooklyn
    ## 701        Pathobiological Sciences        PHD 1980 Univ of Wisconsin-Madison
    ## 702               Computer Sciences     MS 2003 Univ of Minnesota-Twin Cities
    ## 703      Chemical & Biological Engr                                        ME
    ## 704                        Pharmacy                PHD 2000 Tulane University
    ## 705                      Innovation        PHD 1998 Univ of Wisconsin-Madison
    ## 706                     Art History         PHD 1990 Johns Hopkins University
    ## 707             Integrative Biology        PHD 2005 North Carolina State Univ
    ## 708         German, Nordic & Slavic                 PHD 1995 Brown University
    ## 709                      Pediatrics                          PHD 1998 Hungary
    ## 710               Computer Sciences       PHD 2015 University of Pennsylvania
    ## 711                         Physics          PHD 1988 University Of Rochester
    ## 712                      Psychology               PHD 1976 Harvard University
    ## 713  Ms In Biotechnology Degree Prg                     MS UW Colleges Online
    ## 714                        Medicine            PHD 2001 University of Chicago
    ## 715                Academic Affairs   PHD 1995 Univ of California Los Angeles
    ## 716   Engr Professional Development        PHD 1987 Univ of Wisconsin-Madison
    ## 717                      Law School         JD 2002 Univ of Wisconsin-Madison
    ## 718           Afro-American Studies              PHD 2014 New York University
    ## 719      Electrical & Computer Engr    PHD 2006 Univ of Maryland College Park
    ## 720                    Horticulture               PHD 2008 Cornell University
    ## 721          Spanish And Portuguese              PHD 2000 Columbia University
    ## 722               Surgical Sciences      DVM 2008 Univ Federal de Santa Maria
    ## 723                        Agronomy        PHD 2002 Univ of Wisconsin-Madison
    ## 724                        Pharmacy       PHD 1993 Potchefstroomse University
    ## 725                 Medical Physics        PHD 1970 Univ of Wisconsin-Madison
    ## 726    Wisconsin School Of Business         JD 1975 Univ of Wisconsin-Madison
    ## 727                      Pediatrics                      PHD Brown University
    ## 728            Grainger Ctr For Scm        MBA 2009 Univ of Wisconsin-Madison
    ## 729              French And Italian      PHD 1984 Univ of California Berkeley
    ## 730                Medical Sciences         DVM 1981 Univ of California Davis
    ## 731                 Family Medicine             MD 1980 University of Florida
    ## 732          Mechanical Engineering        PHD 2009 Univ of Wisconsin-Madison
    ## 733   Operations & Information Mgmt              PHD 1992 Stanford University
    ## 734              French And Italian        PHD 1994 Univ of Wisconsin-Madison
    ## 735       Industrial & Systems Engr       PHD 2009 Univ degli Studi di Padova
    ## 736        Law, Society And Justice         MS 2001 Univ of Wisconsin-Madison
    ## 737                         English   PHD 2000 Univ of California Los Angeles
    ## 738  Agricultural&Applied Economics   PHD 1988 Univ of IL at Urbana-Champaign
    ## 739   Communication Sci & Disorders          MS 1991 West Virginia University
    ## 740                    Biochemistry        PHD 1955 Univ of Wisconsin-Madison
    ## 741      Electrical & Computer Engr      PHD 1984 Univ of California Berkeley
    ## 742                      Geoscience          PHD 1988 Northwestern University
    ## 743   Biostatistics&Med Informatics    PHD 1970 Univ of Minnesota-Twin Cities
    ## 744                        Medicine         MD 2007 Univ of Wisconsin-Madison
    ## 745                         Finance            PHD 2008 Texas Tech University
    ## 746            Neurological Surgery             MD 1977 University of Chicago
    ## 747                      Pediatrics     MD 1989 Univ of Michigan at Ann Arbor
    ## 748                         Physics        PHD 1989 Univ of Wisconsin-Madison
    ## 749                       Economics        PHD 1983 Univ of Wisconsin-Madison
    ## 750                     Mathematics            PHD 2016 University of Wyoming
    ## 751   Real Estate & Urgan Land Econ                                       PHD
    ## 752                     Mathematics      PHD 1999 Moscow State Univ Lomonosov
    ## 753       Planning & Landscape Arch    PHD 2000 Pennsylvania State University
    ## 754                         History    PHD 2004 Univ of Minnesota-Twin Cities
    ## 755           Ft Mba Program Office                                   BS 1985
    ## 756      Department Of Neuroscience        PHD 2001 Univ of Wisconsin-Madison
    ## 757          Biomolecular Chemistry           PHD 1993 Texas A & M University
    ## 758               Computer Sciences         MS 2000 Univ of Wisconsin-Madison
    ## 759  Atmospheric & Oceanic Sciences    PHD 2006 Pennsylvania State University
    ## 760                      Law School       JD 1994 Univ of California Berkeley
    ## 761                         History      PHD 1985 Univ of California Berkeley
    ## 762                     Mathematics                                  PHD 2018
    ## 763      Asian Languages & Cultures             PHD 2000 Princeton University
    ## 764      Asian Languages & Cultures              PHD 2015 Columbia University
    ## 765                      Psychology            PHD 1985 Ohio State University
    ## 766                 Family Medicine                                  MMS 2000
    ## 767  Orthopedics And Rehabilitation         DS 2009 ROCKY MOUNTAIN UNIVERSITY
    ## 768   Biostatistics&Med Informatics      PHD 2006 Univ of California Berkeley
    ## 769            Neurological Surgery        MD 2007 Baylor College Of Medicine
    ## 770                         English    PHD 1990 Pennsylvania State University
    ## 771                         English            PHD 1989 University of Chicago
    ## 772               Computer Sciences              PHD 2011 Columbia University
    ## 773               Computer Sciences              PHD 2016 Columbia University
    ## 774                      Pediatrics      MD 1985 U Health Sci/Chicago Med Sch
    ## 775   Ed Leadership&Policy Analysis          PHD 1998 Northwestern University
    ## 776                Medical Sciences            DVM 2011 Universidade do Porto
    ## 777               Pharmacy Outreach         PHD 2003 University of Washington
    ## 778             Engineering Physics                  PHD Princeton University
    ## 779                     Social Work        MSW 2014 Univ of Wisconsin-Madison
    ## 780      Population Health Sciences        PHD 1997 Univ of Wisconsin-Madison
    ## 781                     Kinesiology        PHD 1991 Univ of California Irvine
    ## 782  Biological Systems Engineering        PHD 2009 Univ of Wisconsin-Madison
    ## 783     Mead Witter School Of Music             PHD 1988 Princeton University
    ## 784            Medical Microbiology    PHD 1994 Univ of Alabama at Birmingham
    ## 785         School Of Human Ecology        PHD 2001 Rutgers State Univ-Newark
    ## 786        African Cultural Studies    PHD 2010 Univ of Minnesota-Twin Cities
    ## 787    Se Asian Summer Studies Inst                    BA 1998 Univ Of Da Lat
    ## 788                        Oncology                      PHD Universitat Wien
    ## 789           Counseling Psychology       MS 2012 Rensselaer Polytechnic Inst
    ## 790  Civil Society And Comm Studies                MS 1988 Harvard University
    ## 791                         English               PHD 2016 Cornell University
    ## 792     Mead Witter School Of Music    PHD 2000 Univ of Michigan at Ann Arbor
    ## 793               Computer Sciences         PHD 2002 University of Washington
    ## 794     Mead Witter School Of Music          PHD 2005 Northwestern University
    ## 795         School Of Human Ecology          PHD 2005 University of St Thomas
    ## 796                        Genetics        PHD 1980 Univ of Wisconsin-Madison
    ## 797               Computer Sciences     PHD 2002 U of South Carolina-Columbia
    ## 798     Mead Witter School Of Music         MM 1984 University of Connecticut
    ## 799     Mead Witter School Of Music              PHD 1984 University Of Miami
    ## 800                     Amer Ind St        PHD 2005 Michigan State University
    ## 801  Agricultural&Applied Economics          PHD 2003 Kansas State University
    ## 802         School Of Human Ecology       MFA 1988 Virginia Commonwealth Univ
    ## 803                       Astronomy       PHD 2003 Univ degli Studi di Milano
    ## 804                Medical Sciences                                  DVM 2014
    ## 805                    Bacteriology    PHD 1980 Pennsylvania State University
    ## 806                Medical Sciences       DVM 1992 Justus Liebig Univ Giessen
    ## 807                        Pharmacy     PHARMD 1999 Univ of Wisconsin-Madison
    ## 808   Rehab Psychology & Special Ed                PHD 1987 Temple University
    ## 809  Orthopedics And Rehabilitation           MD 2002 Northwestern University
    ## 810               Surgical Sciences    DVM 2013 Louisiana State U-Baton Rouge
    ## 811   Communication Sci & Disorders        AUD 2006 Univ of Wisconsin-Madison
    ## 812  Agricultural&Applied Economics              PHD 2008 New York University
    ## 813   Journalism&Mass Communication         PHD 2000 Johns Hopkins University
    ## 814  Lafollette Sch Of Publ Affairs                JD 1972 Harvard University
    ## 815       Forest & Wildlife Ecology        PHD 2000 North Carolina State Univ
    ## 816                         Nursing       MS 2007 University of New Hampshire
    ## 817                     Social Work    PHD 1994 Univ of Michigan at Ann Arbor
    ## 818   Classic & Ancient Near E Stds         PHD 2009 University of Washington
    ## 819          Mechanical Engineering        PHD 2018 Univ of Wisconsin-Madison
    ## 820                     Art History              PHD 1973 Columbia University
    ## 821  Biological Systems Engineering        PHD 2017 Univ of Wisconsin-Madison
    ## 822                         English      PHD 2011 Univ of Illinois at Chicago
    ## 823  Agricultural&Applied Economics    PHD 2008 Iowa State Univ of Sci & Tech
    ## 824         German, Nordic & Slavic       PHD 1990 University of Pennsylvania
    ## 825         Obstetrics & Gynecology               PHD 1977 University of Iowa
    ## 826                Academic Affairs         MS 1993 Univ of Wisconsin-Madison
    ## 827                 Family Medicine         MD 2013 Univ of Wisconsin-Madison
    ## 828             Integrative Biology      PHD 2014 Univ of Illinois at Chicago
    ## 829      Chemical & Biological Engr              PHD 1974 Stanford University
    ## 830                Medical Sciences            PHD 1975 University of Glasgow
    ## 831                Academic Affairs        DPT 2016 College Of St Scholastica
    ## 832         School Of Human Ecology    PHD 2007 Pennsylvania State University
    ## 833           Ev Mba Program Office   PHD 1975 Univ of IL at Urbana-Champaign
    ## 834                     Social Work                MSW 2011 Aurora University
    ## 835                     Social Work                MSW 2009 Aurora University
    ## 836      Asian Languages & Cultures               PHD 1999 Harvard University
    ## 837      Population Health Sciences        PHD 1982 Univ of Wisconsin-Madison
    ## 838  Lafollette Sch Of Publ Affairs            PHD 2007 University of Florida
    ## 839        Pathobiological Sciences        DVM 2011 Univ of Wisconsin-Madison
    ## 840                      Geoscience    PHD 2003 Univ of Michigan at Ann Arbor
    ## 841                         Nursing      PHD 2014 Univ of Wisconsin-Milwaukee
    ## 842                       Sociology        PHD 2004 Univ of Wisconsin-Madison
    ## 843                      Law School         JD 1965 Univ of Wisconsin-Madison
    ## 844                     Mathematics            PHD 2007 University of Chicago
    ## 845              French And Italian        PHD 2015 Univ of Wisconsin-Madison
    ## 846                  Design Studies              AA 1983 University of London
    ## 847                       Sociology        PHD 2006 Univ of Wisconsin-Madison
    ## 848   Communication Sci & Disorders                           PHD 2014 Canada
    ## 849                      Geoscience         MS 2004 Univ of Wisconsin-Madison
    ## 850               Surgical Sciences                                  DVM 2006
    ## 851                        Pharmacy PHARMD 1983 University of Texas at Austin
    ## 852    Management & Human Resources    PHD 2003 Univ of Maryland College Park
    ## 853                        Medicine             MD 1999 Georgetown University
    ## 854                Academic Affairs                                      DRPH
    ## 855                     Social Work       MSSW 2001 Univ of Wisconsin-Madison
    ## 856  Admin:Student Academic Affairs        PHD 1983 Univ of Wisconsin-Madison
    ## 857                       Chemistry              PHD 1984 Stanford University
    ## 858           Afro-American Studies                BA 2011 Cornell University
    ## 859                         English                  PHD 2016 Duke University
    ## 860     Engineering Research Center         BS 2000 Univ of Wisconsin-Madison
    ## 861                     Kinesiology            PHD 1980 Washington University
    ## 862  Hawk Center For Invst Analysis         MS 1997 Univ of Wisconsin-Madison
    ## 863                     Kinesiology               PHD 2017 Indiana University
    ## 864  Lafollette Sch Of Publ Affairs       PHD 2018 Massachusetts Inst Of Tech
    ## 865                      Law School            JD 1989 Wayne State University
    ## 866                     Social Work        MSW 2013 Univ of Wisconsin-Madison
    ## 867          Spanish And Portuguese               PHD 1999 Harvard University
    ## 868                         Physics             PHD 1998 University of Oxford
    ## 869               Academic Programs      JD 1987 George Washington University
    ## 870                      Pediatrics         MD 2002 Univ of Wisconsin-Madison
    ## 871         Obstetrics & Gynecology     MD 1986 Univ of Massachusetts Med Sch
    ## 872             Integrative Biology                 PHD 2013 Emory University
    ## 873                      Psychiatry             MD 1968 University of Chicago
    ## 874            Nutritional Sciences        PHD 1987 Univ of Wisconsin-Madison
    ## 875   Rehab Psychology & Special Ed        EDM 1996 Univ of Wisconsin-Madison
    ## 876            Nutritional Sciences        PHD 1985 Univ of Wisconsin-Madison
    ## 877   Communication Sci & Disorders         MS 2000 Univ of Wisconsin-Madison
    ## 878               Surgical Sciences                                  DVM 2016
    ## 879          Educational Psychology    PHD 2011 U of California-Santa Barbara
    ## 880              French And Italian           PHD 2000 University of Montreal
    ## 881         German, Nordic & Slavic            PHD 2012 University of Chicago
    ## 882                      Pediatrics          MD 1986 University Of New Mexico
    ## 883                     Social Work               MSW 2015 University of Iowa
    ## 884        Pathobiological Sciences                                  PHD 2014
    ## 885                 Medical Physics        PHD 2016 Univ of Wisconsin-Madison
    ## 886                      Statistics           PHD 2019 University of Virginia
    ## 887                     Mathematics               PHD 1998 Harvard University
    ## 888  Lafollette Sch Of Publ Affairs    M.P.AFF 2003 Univ of Wisconsin-Madison
    ## 889   Communication Sci & Disorders               PHD 1981 Indiana University
    ## 890              Communication Arts                 MFA 2007 Columbia College
    ## 891                       Chemistry        PHD 2017 Univ of Wisconsin-Madison
    ## 892                 Medical Physics        PHD 2015 Univ of Wisconsin-Madison
    ## 893                    Horticulture         PHD 2012 Univ of California Davis
    ## 894    Madison Pathology/Toxicology        DVM 2013 Univ of Wisconsin-Madison
    ## 895                       Sociology               PHD 2006 Harvard University
    ## 896                 Medical Physics      PHD 1993 Universidad de Buenos Aires
    ## 897                       Sociology               PHD 1989 Harvard University
    ## 898                          Botany               PHD 1999 Cornell University
    ## 899                    Horticulture      PHD 2011 Washington State University
    ## 900                Risk & Insurance              BS 1983 Princeton University
    ## 901                         Nursing        DNP 2013 Univ of Wisconsin-Madison
    ## 902     Mead Witter School Of Music    DM 2020 Univ of IL at Urbana-Champaign
    ## 903                       Economics      PHD 1983 Univ of California Berkeley
    ## 904      Population Health Sciences       PHD 2006 Univ of Colorado at Denver
    ## 905                       Sociology         PHD 2010 Johns Hopkins University
    ## 906          Biomolecular Chemistry       PHD 2007 Baylor College Of Medicine
    ## 907        African Cultural Studies      PHD 2011 Univ of California Berkeley
    ## 908                 Medical Physics        PHD 2011 Univ of Wisconsin-Madison
    ## 909        Gender And Women Studies    PHD 1999 Univ of Minnesota-Twin Cities
    ## 910          Educational Psychology    PHD 1976 Univ of Minnesota-Twin Cities
    ## 911                    Anthropology            PHD 2014 University of Chicago
    ## 912                         English               PHD 2012 Cornell University
    ## 913   Community & Environ Sociology    PHD 1993 Univ of Minnesota-Twin Cities
    ## 914   Materials Science&Engineering              PHD 1991 Stanford University
    ## 915                       Marketing   PHD 2008 University of Nebraska-Lincoln
    ## 916              Accting & Info Sys  MACC 2001 University of Nebraska-Lincoln
    ## 917   Graaskamp Ctr For Real Estate             PHD Univ of Wisconsin-Madison
    ## 918                         Finance            PHD 2001 University of Chicago
    ## 919     South Asian Sum Lang Instit        PHD 2018 Univ of Wisconsin-Madison
    ## 920                         Physics               PHD 1997 Harvard University
    ## 921          Mechanical Engineering   PHD 2011 Univ of IL at Urbana-Champaign
    ## 922                      Statistics         MS 2018 Univ of Wisconsin-Madison
    ## 923                      Law School      PHD 1971 Univ of California Berkeley
    ## 924                       Sociology            PHD 1997 University of Chicago
    ## 925                     Mathematics      PHD 2010 Univ of California Berkeley
    ## 926                         Nursing               PHD 2008 University of Iowa
    ## 927              Information School              PHD 2000 Syracuse University
    ## 928            Nutritional Sciences      MA 1980 Indiana Univ Of Pennsylvania
    ## 929                        Medicine    DO 2013 Philadelphia Colg of Osteopath
    ## 930                       Chemistry        PHD 2012 Univ of Wisconsin-Madison
    ## 931                    Food Science      PHD 1983 Univ of California Berkeley
    ## 932                       Economics      PHD 1993 Univ of California Berkeley
    ## 933   Pathology&Laboratory Medicine        PHD 1997 Univ of Wisconsin-Madison
    ## 934                         English         MA 1998 Univ of Wisconsin-Madison
    ## 935   Materials Science&Engineering               PHD 2000 Harvard University
    ## 936         German, Nordic & Slavic    PHD 1996 Univ of Michigan at Ann Arbor
    ## 937                 Family Medicine         MD 1995 Univ of Wisconsin-Madison
    ## 938                         Physics       PHD 1998 University of Pennsylvania
    ## 939   Pathology&Laboratory Medicine         PHD 1984 Eotvos Lorand University
    ## 940                        Oncology        PHD 1975 Univ of Wisconsin-Madison
    ## 941                     Social Work             MA 2006 University of Chicago
    ## 942                 Medical Physics                  PHD 2000 Mayo Foundation
    ## 943               Academic Programs              JD Univ of Wisconsin-Madison
    ## 944  Ms In Biotechnology Degree Prg         JD 1997 Univ of Wisconsin-Madison
    ## 945                       Neurology                MD 2000 University of Iowa
    ## 946            Nutritional Sciences             PHD 2014 Princeton University
    ## 947                 Theatre & Drama                MFA 1991 Boston University
    ## 948                     Mathematics                                       PHD
    ## 949                         Physics            PHD 2015 University of Chicago
    ## 950                         Urology            MD 1992 Beirut Arab University
    ## 951   Ed Leadership&Policy Analysis      PHD 1995 Univ of Illinois at Chicago
    ## 952      Electrical & Computer Engr                 PHD 2017 University of MI
    ## 953                         English     PHD 2012 George Washington University
    ## 954                    Horticulture           PHD 2020 Texas A & M University
    ## 955                         Finance        PHD 1988 Univ of Wisconsin-Madison
    ## 956                      Geoscience       PHD 1991 Massachusetts Inst Of Tech
    ## 957      Curriculum And Instruction              PHD 2008 Stanford University
    ## 958                     Mathematics      PHD 1994 Univ of California Berkeley
    ## 959                        Medicine               MD 1996 SUNY At Stony Brook
    ## 960                       Neurology        PHD 2007 Univ of Wisconsin-Madison
    ## 961   Materials Science&Engineering           PHD 2015 Texas A & M University
    ## 962              Accting & Info Sys    PHD 2020 Univ of Maryland College Park
    ## 963                     Social Work       MSSW 1984 Univ of Wisconsin-Madison
    ## 964               Computer Sciences    PHD 2017 Univ of Michigan at Ann Arbor
    ## 965                          Botany      PHD 1987 Univ of Colorado at Boulder
    ## 966       Animal And Dairy Sciences        PHD 2015 Univ of Wisconsin-Madison
    ## 967                       Sociology               PHD 1976 Harvard University
    ## 968               Surgical Sciences          DVM 2005 Univ Federal Fluminense
    ## 969                      Geoscience      PHD 2009 Univ of California Berkeley
    ## 970               Computer Sciences          PHD 1988 University of Cambridge
    ## 971                         Nursing        DNP 2012 Univ of Wisconsin-Madison
    ## 972               Computer Sciences         BS 2005 Univ of Wisconsin-Madison
    ## 973                            #N/A               PHD 2012 Cornell University
    ## 974                     Kinesiology        PHD 2017 Colorado State University
    ## 975                   Asian Studies                                       PHD
    ## 976                      Law School                   JD 1985 Yale University
    ## 977                      Law School               JD 2009 Stanford University
    ## 978   Communication Sci & Disorders        PHD 2016 Univ of Wisconsin-Madison
    ## 979                         English        PHD 2009 Univ of Wisconsin-Madison
    ## 980          Educational Psychology        PHD 2015 Univ of Wisconsin-Madison
    ## 981                      Statistics        PHD 1989 Univ of Wisconsin-Madison
    ## 982     Mead Witter School Of Music     MA 1982 New England Cnsrvtry Of Music
    ## 983                        Pharmacy PHARMD 1993 Univ of Minnesota-Twin Cities
    ## 984     Life Sciences Communication        PHD 1998 Univ of Wisconsin-Madison
    ## 985                     Social Work        MSW 1989 Univ of Wisconsin-Madison
    ## 986   Pathology&Laboratory Medicine          MD 2014 University Of New Mexico
    ## 987                             Art   MFA 2005 Univ of California Los Angeles
    ## 988         School Of Human Ecology    PHD 1987 Univ of Michigan at Ann Arbor
    ## 989                             Art        MFA 1988 Univ of Wisconsin-Madison
    ## 990                      Philosophy            PHD 2012 University of Toronto
    ## 991  Lafollette Sch Of Publ Affairs        PHD 2006 Univ of Wisconsin-Madison
    ## 992   Engr Professional Development    MS 2017 Univ of IL at Urbana-Champaign
    ## 993                        Medicine          PHD 2007 Northwestern University
    ## 994  Agricultural&Applied Economics        PHD 1998 Univ of Wisconsin-Madison
    ## 995             Engineering Physics        PHD 1978 Univ of Wisconsin-Madison
    ## 996          Spanish And Portuguese            PHD 2010 Ohio State University
    ## 997                        Pharmacy        PHD 2004 Univ of Wisconsin-Madison
    ## 998                         Physics             PHD 1992 Princeton University
    ## 999                    Bacteriology             PHD 1993 Princeton University
    ## 1000              Surgical Sciences       DVM 1988 University of Pennsylvania
    ## 1001  Journalism&Mass Communication           MS 1999 Northwestern University
    ## 1002                     Pediatrics                   MD 1964 Yale University
    ## 1003                      Radiology        PHD 2005 Univ of Wisconsin-Madison
    ## 1004  Communication Sci & Disorders          PHD 1980 Northwestern University
    ## 1005                     Law School                  JD 2003 Emory University
    ## 1006                   Biochemistry    PHD 1989 Univ of Minnesota-Twin Cities
    ## 1007         Biomolecular Chemistry        PHD 1992 Univ of Wisconsin-Madison
    ## 1008                        English     PHD 1998 Loyola University of Chicago
    ## 1009               Consumer Science             MS 1986 Ohio State University
    ## 1010         Mechanical Engineering               MS 1993 Stanford University
    ## 1011                        Surgery           MD 2004 University Of Rochester
    ## 1012         Mechanical Engineering                                  PHD 2008
    ## 1013            Engineering Physics     PHD 2009 California Institute of Tech
    ## 1014                        Nursing        DNP 2016 Univ of Wisconsin-Madison
    ## 1015    Administration-Acad Affairs         MS 2014 Univ of Wisconsin-Madison
    ## 1016                    Social Work          MSW 2005 College Of St Catherine
    ## 1017                    Social Work        MPA 2008 Univ of Wisconsin-Madison
    ## 1018               Medical Sciences        DVM 2017 Univ of Wisconsin-Madison
    ## 1019     Civil & Environmental Engr       PHD 1999 Georgia Inst of Technology
    ## 1020     Electrical & Computer Engr        PHD 2009 Univ of Wisconsin-Madison
    ## 1021                      Chemistry               PHD 2005 Cornell University
    ## 1022                   Soil Science     PHD 2012 Rutgers St Unv-New Brunswick
    ## 1023                      Sociology      PHD 1994 Univ of California Berkeley
    ## 1024          Cals Academic Affairs                                  MPA 2012
    ## 1025     Curriculum And Instruction                 MS 2011 DePaul University
    ## 1026      Animal And Dairy Sciences    PHD 1996 North Dakota State University
    ## 1027  Journalism&Mass Communication              PHD 1985 Brandeis University
    ## 1028                     Law School         JD 1992 Univ of Wisconsin-Madison
    ## 1029                      Economics        PHD 2015 Univ of Wisconsin-Madison
    ## 1030                        English        PHD 1973 Univ of Wisconsin-Madison
    ## 1031       Pathobiological Sciences        PHD 2003 Univ of Wisconsin-Madison
    ## 1032       Pathobiological Sciences        DVM 1991 Univ of Wisconsin-Madison
    ## 1033                   Biochemistry        PHD 1983 Univ of Wisconsin-Madison
    ## 1034  Pathology&Laboratory Medicine        PHD 1991 Univ of Wisconsin-Madison
    ## 1035          Counseling Psychology       PSYD 2017 Univ of Wisconsin-Madison
    ## 1036                      Economics       PHD 2010 University of Pennsylvania
    ## 1037                    Mathematics           PHD 2017 Texas A & M University
    ## 1038             Accting & Info Sys       MACC 2000 Univ of Wisconsin-Madison
    ## 1039                      Sociology      PHD 1986 Univ of California Berkeley
    ## 1040    Mead Witter School Of Music     MA 1976 New England Cnsrvtry Of Music
    ## 1041 Ms In Biotechnology Degree Prg        MS 1977 Massachusetts Inst Of Tech
    ## 1042                        Surgery      MD 2005 Loyola University of Chicago
    ## 1043             Information School                   MS 2012 Bentley College
    ## 1044                Theatre & Drama    MFA 1982 University of Hawaii at Manoa
    ## 1045     Curriculum And Instruction        EDM 2019 Univ of Wisconsin-Madison
    ## 1046  Classic & Ancient Near E Stds            PHD 2019 Ohio State University
    ## 1047        School Of Human Ecology                  PHD 2014 Yale University
    ## 1048              Academic Programs            PHD 1999 University of Chicago
    ## 1049             Accting & Info Sys            PHD 2011 University of Arizona
    ## 1050                        Nursing        MSN 2011 Univ of Wisconsin-Oshkosh
    ## 1051                       Medicine            MD 1988 University of Montreal
    ## 1052                      Neurology        MD 1993 Univ of Colorado at Denver
    ## 1053                       Pharmacy     PHARMD 2005 Univ of Wisconsin-Madison
    ## 1054                     Psychology           PHD Washington State University
    ## 1055                       Medicine       PHD 2010 Univ degli Studi di Milano
    ## 1056                        Nursing           MD 1983 Univ Federal de Pelotas
    ## 1057  Ophthalmology&Visual Sciences    PHD 1998 Univ of Michigan at Ann Arbor
    ## 1058            Integrative Biology         PHD 1997 University of Washington
    ## 1059   Management & Human Resources   PHD 2010 Univ of IL at Urbana-Champaign
    ## 1060              Political Science    PHD 2001 Univ of Minnesota-Twin Cities
    ## 1061     Population Health Sciences        PHD 1998 Univ of Wisconsin-Madison
    ## 1062                       Pharmacy                                     OQUAL
    ## 1063                      Geography    PHD 2017 U of California-Santa Barbara
    ## 1064                      Chemistry      PHD 2010 Univ of California Berkeley
    ## 1065         Educational Psychology   PHD 2010 University of Nebraska-Lincoln
    ## 1066                     Statistics       PHD 2015 Carnegie-Mellon University
    ## 1067                    Social Work        MSW 2010 Univ of Wisconsin-Madison
    ## 1068 Lafollette Sch Of Publ Affairs             PHD 2017 Princeton University
    ## 1069  Community & Environ Sociology         PHD 2009 Johns Hopkins University
    ## 1070                    Kinesiology         PHD 2015 St. Catherine University
    ## 1071                      Geography        PHD 2003 Univ of Wisconsin-Madison
    ## 1072                       Genetics              PHD 2000 Stanford University
    ## 1073       Pathobiological Sciences                                  PHD 2015
    ## 1074       Gender And Women Studies        PHD 2014 Univ of Wisconsin-Madison
    ## 1075                    Kinesiology       MS 1986 Washington State University
    ## 1076     Civil & Environmental Engr                                    M.ARCH
    ## 1077                          Dance         BA 2012 Univ of Wisconsin-Madison
    ## 1078  Cell And Regenerative Biology               PHD 2002 Cornell University
    ## 1079     Chemical & Biological Engr         PHD U of California-Santa Barbara
    ## 1080            Engineering Physics          PHD Ludwig Maximilians U Munchen
    ## 1081                      Chemistry              PHD 1986 Columbia University
    ## 1082                     Law School        MA 2001 Univ of Colorado at Denver
    ## 1083      Planning & Landscape Arch        PHD 2001 Univ of Wisconsin-Madison
    ## 1084          Inst Reg Intl Studies         PHD 2011 Arizona State University
    ## 1085                            Art   MFA 1984 Sch Of The Art Inst Of Chicago
    ## 1086                    Mathematics                  PHD 2017 SUNY at Buffalo
    ## 1087 Ms In Biotechnology Degree Prg         MS 2006 Univ of Wisconsin-Madison
    ## 1088                    Social Work            PHD 2017 Washington University
    ## 1089                      Sociology      PHD 1995 Univ of California Berkeley
    ## 1090   Management & Human Resources        PHD 1985 Univ of Wisconsin-Madison
    ## 1091                     Pediatrics       MD 1981 University of South Florida
    ## 1092                     Psychology    PHD 1983 University of Texas at Austin
    ## 1093                Plant Pathology        PHD 2005 Michigan State University
    ## 1094     Asian Languages & Cultures              PHD 2001 Columbia University
    ## 1095         Mechanical Engineering             PHD 1995 Princeton University
    ## 1096     Curriculum And Instruction    PHD 2008 Univ of Michigan at Ann Arbor
    ## 1097                      Geography        PHD 2008 Univ of Wisconsin-Madison
    ## 1098                     Philosophy        PHD 1989 Univ of Wisconsin-Madison
    ## 1099                        Nursing                 PHD 2018 University of MI
    ## 1100                       Pharmacy      PHARMD 1990 University of Washington
    ## 1101       Office Of Sustainability              PHD 1993 Columbia University
    ## 1102                        Physics   PHD 1987 Univ Studi di Roma-La Sapienza
    ## 1103                     Statistics               MS 1989 Stanford University
    ## 1104    Engineering Research Center        PHD 1999 Univ of Wisconsin-Madison
    ## 1105            Integrative Biology     PHD 2001 Louisiana State U & A&M Colg
    ## 1106                        English                  PHD 2010 Yale University
    ## 1107      Planning & Landscape Arch               PHD 1991 Indiana University
    ## 1108                         Botany          PHD 1987 University of Edinburgh
    ## 1109     Civil & Environmental Engr              PHD 2006 Stanford University
    ## 1110                     Psychology                  PHD 2011 Nova University
    ## 1111             Information School            MLIS 2009 Dominican University
    ## 1112             French And Italian      PHD 2011 Univ of California Berkeley
    ## 1113  Biostatistics&Med Informatics       PHD 2012 Carnegie-Mellon University
    ## 1114                         Botany             PHD 1976 Princeton University
    ## 1115    Mead Witter School Of Music   DMA 1999 Univ of IL at Urbana-Champaign
    ## 1116                    Social Work        MSW 2014 Univ Of Minnesota-St Paul
    ## 1117                      Economics             PHD Univ Of NC At Chapel Hill
    ## 1118                     Law School       JD 2004 Chicago-Kent College Of Law
    ## 1119              Computer Sciences       PHD 1994 Carnegie-Mellon University
    ## 1120                     Law School         JD 2007 Univ of Wisconsin-Madison
    ## 1121 Agricultural&Applied Economics         MS 2011 Univ of Wisconsin-Madison
    ## 1122          Counseling Psychology         PHD 1993 Arizona State University
    ## 1123                        History         PHD 2016 Johns Hopkins University
    ## 1124        German, Nordic & Slavic     PHD 2009 Eurasian National University
    ## 1125                       Medicine      PHD 2010 Russian Academy of Sciences
    ## 1126                      Geography    PHD 2005 Univ of Michigan at Ann Arbor
    ## 1127                 Design Studies        MFA 2008 Univ of Wisconsin-Madison
    ## 1128                        Finance         MS 2004 Univ of Wisconsin-Madison
    ## 1129  Ed Leadership&Policy Analysis            PHD 2012 Vanderbilt University
    ## 1130                    Mathematics               PHD 2019 Cornell University
    ## 1131  Classic & Ancient Near E Stds             PHD 2017 Princeton University
    ## 1132                      Sociology           PHD 2001 New College of Florida
    ## 1133          Counseling Psychology       PSYD 2017 Univ of Wisconsin-Madison
    ## 1134       Pathobiological Sciences               PHD 1996 Harvard University
    ## 1135                       Medicine                   MD 2004 Yale University
    ## 1136                       Pharmacy             PHD 2002 University of Kansas
    ## 1137         Spanish And Portuguese      PHD 2009 Univ of California Berkeley
    ## 1138                   Horticulture        PHD 1991 Univ of Wisconsin-Madison
    ## 1139                     Psychology    PHD 1978 Univ of Minnesota-Twin Cities
    ## 1140                      Chemistry          PHD 2007 Northwestern University
    ## 1141       Gender And Women Studies      PHD 2015 Univ of California Berkeley
    ## 1142        Comparative Biosciences   PHD 1984 Univ of IL at Urbana-Champaign
    ## 1143     Curriculum And Instruction        PHD 1985 Univ of Wisconsin-Madison
    ## 1144  Dept Of Med History&Bioethics                 PHD Vanderbilt University
    ## 1145     Department Of Neuroscience    PHD 1995 Univ of Minnesota-Twin Cities
    ## 1146                Volunteer Staff               MD 2007 Columbia University
    ## 1147         Biomedical Engineering    PHD 1999 Univ of Michigan at Ann Arbor
    ## 1148                    Mathematics            PHD 1994 University of Chicago
    ## 1149    Mead Witter School Of Music         MM 2014 Univ of Wisconsin-Madison
    ## 1150     Educational Policy Studies        PHD 2011 Univ of Wisconsin-Madison
    ## 1151                     Psychology    PHD 1996 Univ of Minnesota-Twin Cities
    ## 1152             French And Italian             PHD 1981 Princeton University
    ## 1153                     Geoscience      PHD 1988 Univ of California Berkeley
    ## 1154  Materials Science&Engineering               PHD 2001 Cornell University
    ## 1155                    Mathematics      PHD 2011 Moscow State Univ Lomonosov
    ## 1156                      Marketing   MBA 1997 University of Alaska-Anchorage
    ## 1157                     Philosophy               PHD 1988 Cornell University
    ## 1158 Ms In Biotechnology Degree Prg         MD 2000 Univ of Wisconsin-Madison
    ## 1159                   Bacteriology                 PHD 1980 Brown University
    ## 1160    Mead Witter School Of Music         MM 1989 Manhattan School Of Music
    ## 1161              Computer Sciences        PHD 1987 Univ of Wisconsin-Madison
    ## 1162                         Botany    PHD 1975 Univ of Michigan at Ann Arbor
    ## 1163     Chemical & Biological Engr               PHD 1991 Cornell University
    ## 1164          Counseling Psychology                PHD 2009 Auburn University
    ## 1165 Agricultural&Applied Economics    PHD 2010 U of California-Santa Barbara
    ## 1166                            Art        MFA 1980 SUNY College at New Paltz
    ## 1167 International Studies&Programs         BS 2007 Univ of Wisconsin-Madison
    ## 1168               Medical Sciences        DVM 2017 Univ of Wisconsin-Madison
    ## 1169     Curriculum And Instruction        PHD 1972 Univ of Wisconsin-Madison
    ## 1170                      Sociology       PHD 2009 University of Pennsylvania
    ## 1171                        History        PHD 2017 Univ of Wisconsin-Madison
    ## 1172                   Biochemistry                                  PHD 2008
    ## 1173                     Entomology      PHD 1997 Univ of California Berkeley
    ## 1174     Curriculum And Instruction      PHD 1990 Univ of Colorado at Boulder
    ## 1175  Journalism&Mass Communication              PHD 2013 Columbia University
    ## 1176              Academic Programs         PHD 2018 Florida State University
    ## 1177             Communication Arts             PHD 2003 University of London
    ## 1178                Theatre & Drama   MFA 1985 Univ of IL at Urbana-Champaign
    ## 1179                     Psychology          PHD 2008 University Of Rochester
    ## 1180                     Statistics              MS Univ of Wisconsin-Madison
    ## 1181     Population Health Sciences        PHD 2007 Univ Of NC At Chapel Hill
    ## 1182     Chemical & Biological Engr    PHD 2004 Pennsylvania State University
    ## 1183          Afro-American Studies                  PHD 1996 Duke University
    ## 1184                     Law School       JD 1974 Univ of California Berkeley
    ## 1185                        Nursing       DNS 2017 University of Pennsylvania
    ## 1186                    Social Work        MSW 2010 Univ of Wisconsin-Madison
    ## 1187   Management & Human Resources        PHD 2002 Univ of Wisconsin-Madison
    ## 1188                      Economics    PHD 2012 Univ of Michigan at Ann Arbor
    ## 1189             Accting & Info Sys          PHD 1991 University Of Rochester
    ## 1190  Cell And Regenerative Biology        PHD 1985 Univ of Wisconsin-Madison
    ## 1191             Accting & Info Sys            PHD 2014 University of Georgia
    ## 1192             Accting & Info Sys            MS 2007 Texas A & M University
    ## 1193                            Art                MFA 2004 Alfred University
    ## 1194            Integrative Biology               PHD 1993 Harvard University
    ## 1195                    Mathematics    PHD 2014 University of Texas at Austin
    ## 1196                     Law School      PHD 2006 City University Of New York
    ## 1197           Nutritional Sciences         PHD 1991 East Carolina University
    ## 1198                      Sociology        PHD 2002 Univ of Wisconsin-Madison
    ## 1199     Electrical & Computer Engr                                  PHD 2014
    ## 1200                     Law School                JD 1999 Hofstra University
    ## 1201                    Social Work        MSW 2010 Univ of Wisconsin-Madison
    ## 1202        German, Nordic & Slavic    PHD 1991 U of California-Santa Barbara
    ## 1203               Academic Affairs                    PHD 1996 Texas College
    ## 1204                     Entomology        PHD 2001 North Carolina State Univ
    ## 1205                    Kinesiology         PHD 1993 Johns Hopkins University
    ## 1206                        English        LLM 2005 Univ of Wisconsin-Madison
    ## 1207     Electrical & Computer Engr    PHD 1988 Univ of Maryland College Park
    ## 1208                     Entomology            PHD 2004 Utah State University
    ## 1209                       Pharmacy          PHD Medical College Of Wisconsin
    ## 1210          Counseling Psychology             MA 2014 University of Montana
    ## 1211           Medical Microbiology              PHD 1996 Stanford University
    ## 1212 Biological Systems Engineering   PHD 1985 Univ of IL at Urbana-Champaign
    ## 1213             Communication Arts         BA 1989 Univ of Wisconsin-Madison
    ## 1214                    Mathematics                 PHD 2015 Universitat Bonn
    ## 1215      Animal And Dairy Sciences    PHD 2004 China Agricultural University
    ## 1216                    Mathematics    PHD 2012 Univ of Minnesota-Twin Cities
    ## 1217              Computer Sciences       PHD 2011 Carnegie-Mellon University
    ## 1218                     Law School          JD 2011 University of Pittsburgh
    ## 1219                    Mathematics              PHD 2005 Tel Aviv University
    ## 1220                       Pharmacy         MS 2010 Univ of Wisconsin-Madison
    ## 1221             Emergency Medicine         MD 2012 Univ of Wisconsin-Madison
    ## 1222                      Chemistry         DS 2016 University of New Orleans
    ## 1223                       Agronomy    PHD 2008 Iowa State Univ of Sci & Tech
    ## 1224                        English      PHD 2001 Univ of California Berkeley
    ## 1225               Academic Affairs     PHARMD 2012 Univ of Wisconsin-Madison
    ## 1226  Engr Professional Development                                       MBA
    ## 1227        Comparative Biosciences                                  DVM 2009
    ## 1228  Materials Science&Engineering         MS 1992 Naval Postgraduate School
    ## 1229 Biological Systems Engineering         MS 2011 Univ of Wisconsin-Madison
    ## 1230     Asian Languages & Cultures               PHD 2007 Cornell University
    ## 1231                Theatre & Drama        MFA 2009 Univ of Wisconsin-Madison
    ## 1232      Planning & Landscape Arch        MLA 2011 Univ of Wisconsin-Madison
    ## 1233  Pathology&Laboratory Medicine    MD 1970 Ferdowsi University of Mashhad
    ## 1234                       Pharmacy     PHARMD 2005 Univ of Wisconsin-Madison
    ## 1235                        English    MFA 2011 Univ of Massachusetts Amherst
    ## 1236         Educational Psychology        PHD 2016 Univ of Wisconsin-Madison
    ## 1237     Electrical & Computer Engr          PHD 1998 Northwestern University
    ## 1238                     Law School         JD 1994 Univ of Wisconsin-Madison
    ## 1239         Biomedical Engineering        PHD Hebrew University of Jerusalem
    ## 1240                Theatre & Drama              MFA 2018 Columbia University
    ## 1241      Animal And Dairy Sciences             MS 1985 University of Arizona
    ## 1242                       Medicine        PHD 1994 Michigan State University
    ## 1243               Academic Affairs       PHD 2011 Baylor College Of Medicine
    ## 1244  Journalism&Mass Communication                BA 1981 Indiana University
    ## 1245                        English        PHD 1999 Univ of Wisconsin-Madison
    ## 1246                        History        PHD 2007 Univ Of NC At Chapel Hill
    ## 1247                Medical Physics        PHD 1988 Univ of Wisconsin-Madison
    ## 1248                Family Medicine                DS 2011 Andrews University
    ## 1249            Integrative Biology        PHD 1994 Univ of Wisconsin-Madison
    ## 1250                        Nursing      DNP 2011 Univ of Wisconsin-Milwaukee
    ## 1251        School Of Human Ecology               PHD 2009 Harvard University
    ## 1252              Computer Sciences        PHD 2006 Univ of Wisconsin-Madison
    ## 1253     Curriculum And Instruction          PHD 2005 Northwestern University
    ## 1254  Ed Leadership&Policy Analysis          PHD 2001 Northwestern University
    ## 1255                        Physics        PHD 1969 Univ Catolique de Louvain
    ## 1256                      Chemistry               PHD 1986 Cornell University
    ## 1257     Civil & Environmental Engr                                       PHD
    ## 1258 Uw Comprehensive Cancer Center         MS 2000 Univ of Wisconsin-Madison
    ## 1259  Real Estate & Urgan Land Econ              PHD 2005 Stanford University
    ## 1260                Plant Pathology        PHD 1984 Univ of Wisconsin-Madison
    ## 1261                    Mathematics        PHD 2009 Univ Of Minnesota-St Paul
    ## 1262           Neurological Surgery                  MD 1990 Cairo University
    ## 1263     Civil & Environmental Engr    PHD 1989 Pennsylvania State University
    ## 1264                     Law School                                   JD 2000
    ## 1265                        History               PHD 1999 Harvard University
    ## 1266                      Economics                  PHD 1989 Yale University
    ## 1267                      Economics              PHD 2011 Stanford University
    ## 1268                       Medicine         MD 1993 Univ of Wisconsin-Madison
    ## 1269                      Economics          PHD 1992 University Of Rochester
    ## 1270                        Nursing     MSN 2005 Univ of Wisconsin-Eau Claire
    ## 1271                        Physics    PHD 2000 Univ of Michigan at Ann Arbor
    ## 1272                     Law School        MSW 2015 Univ of Wisconsin-Madison
    ## 1273            Integrative Biology        PHD 2003 Univ of Wisconsin-Madison
    ## 1274        German, Nordic & Slavic              PHD 2016 Columbia University
    ## 1275                     Psychology               PHD 1980 Harvard University
    ## 1276              Surgical Sciences            DVM 1991 University of Georgia
    ## 1277            Integrative Biology      PHD 1987 Univ of California Berkeley
    ## 1278                     Pediatrics         MD 2010 Univ of Wisconsin-Madison
    ## 1279        School Of Human Ecology   MFA 1989 Sch Of The Art Inst Of Chicago
    ## 1280           Nutritional Sciences         PHD 2013 Univ Of NC At Greensboro
    ## 1281               Consumer Science             MSSW 2010 Columbia University
    ## 1282     Civil & Environmental Engr        PHD 1997 Univ Of NC At Chapel Hill
    ## 1283      Planning & Landscape Arch         MS 1983 Univ of Wisconsin-Madison
    ## 1284                          Dance        PHD 2005 Univ of Wisconsin-Madison
    ## 1285        Biology Core Curriculum        PHD 1999 Univ of Wisconsin-Madison
    ## 1286                        English        PHD 1996 Univ of Wisconsin-Madison
    ## 1287         Biomolecular Chemistry       PHD 2006 Massachusetts Inst Of Tech
    ## 1288      Forest & Wildlife Ecology      PHD 2014 Univ of Colorado at Boulder
    ## 1289                   Food Science        PHD 1980 Colorado State University
    ## 1290                   Soil Science            PHD 2001 University of Reading
    ## 1291        Obstetrics & Gynecology         MD 1988 Univ of Missouri-Columbia
    ## 1292  Pathology&Laboratory Medicine     MD 1994 Univ of Michigan at Ann Arbor
    ## 1293        School Of Human Ecology            PHD 2007 University of Wyoming
    ## 1294  Communication Sci & Disorders            PHD 2009 A.T. Still University
    ## 1295                Family Medicine                                       DPT
    ## 1296            Integrative Biology              DS Univ of Wisconsin-Madison
    ## 1297              Surgical Sciences        DVM 1993 Univ of Wisconsin-Madison
    ## 1298        School Of Human Ecology             PHD 2018 Santa Monica College
    ## 1299                        Physics             PHD 1997 Princeton University
    ## 1300     Curriculum And Instruction        PHD 1999 Univ of Wisconsin-Madison
    ## 1301              Computer Sciences        PHD 1998 Univ of Wisconsin-Madison
    ## 1302  Journalism&Mass Communication         MA 1993 Univ of Wisconsin-Madison
    ## 1303    Student Acad Affairs Office         MS 2014 Univ of Wisconsin-Madison
    ## 1304                      Geography         MS 2017 Univ of Wisconsin-Madison
    ## 1305  Operations & Information Mgmt          PHD 1984 Northwestern University
    ## 1306                   Horticulture        PHD 1984 Univ of Wisconsin-Madison
    ## 1307     Curriculum And Instruction    PHD 1997 Univ of Massachusetts Amherst
    ## 1308              Surgical Sciences                                  DVM 2016
    ## 1309                   Anthropology    PHD 1999 Univ of Michigan at Ann Arbor
    ## 1310                        Nursing        DNP 2018 Univ of Wisconsin-Oshkosh
    ## 1311                            Art             MFA Univ of Wisconsin-Madison
    ## 1312  Operations & Information Mgmt                PHD 2015 Auburn University
    ## 1313                          Dance               MFA 2013 Hollins University
    ## 1314                    Kinesiology     EDM 1987 Univ of Wisconsin-Whitewater
    ## 1315                        History    PHD 2009 U of California-Santa Barbara
    ## 1316                       Pharmacy PHARMD 1993 Univ of Minnesota-Twin Cities
    ## 1317                    Social Work      MSW 1999 Univ of California Berkeley
    ## 1318    Student Acad Affairs Office         BA 2000 Univ of Wisconsin-Madison
    ## 1319                      Marketing       PHD 2020 Georgia Inst of Technology
    ## 1320                     Law School         JD 2012 Univ of Wisconsin-Madison
    ## 1321               Medical Sciences        DVM 2017 Univ of Wisconsin-Madison
    ## 1322  Engr Professional Development               MS Johns Hopkins University
    ## 1323            Engineering Physics              PHD 1989 Columbia University
    ## 1324                      Marketing        PHD 1987 Univ of Wisconsin-Madison
    ## 1325                      Marketing        PHD 1994 Univ of Wisconsin-Madison
    ## 1326                    Social Work      MSW 1999 Univ of MD Baltimore County
    ## 1327 Orthopedics And Rehabilitation               PHD 2000 University of Iowa
    ## 1328              Computer Sciences            PHD 2016 Universitat Stuttgart
    ## 1329                  Naval Science    BSE 2014 Univ of Michigan at Ann Arbor
    ## 1330                     Law School         JD 1991 Univ of Wisconsin-Madison
    ## 1331                          Dance             MFA 1991 University of Oregon
    ## 1332                      Astronomy      PHD 2000 Univ of Colorado at Boulder
    ## 1333       Disease Prevention Admin      PHD 2005 Oregon Health Sciences Univ
    ## 1334                       Medicine              MD 1990 University of Tehran
    ## 1335         Mechanical Engineering               PHD 2013 University of Utah
    ## 1336            Engineering Physics        PHD 1987 Univ of Wisconsin-Madison
    ## 1337                    Social Work        MSW 2008 Univ of Wisconsin-Madison
    ## 1338                     Pediatrics         PHD 1990 Johns Hopkins University
    ## 1339 Atmospheric & Oceanic Sciences        PHD 2017 Colorado State University
    ## 1340                      Marketing        PHD 2007 Univ of Wisconsin-Madison
    ## 1341                     Law School      PHD 1993 Univ of California Berkeley
    ## 1342                      Economics        PHD 1982 Univ of Wisconsin-Madison
    ## 1343            Acad Affairs & Prog        PHD 1989 Univ of Wisconsin-Madison
    ## 1344      Language Sciences Program   PHD 2020 University of Hawaii-West Oahu
    ## 1345              Academic Programs        PHD 2014 Univ Of NC At Chapel Hill
    ## 1346  Communication Sci & Disorders               PHD 2003 University of Iowa
    ## 1347                        Nursing              MSN 1996 St Louis University
    ## 1348                     Psychology        PHD 1998 Univ of Wisconsin-Madison
    ## 1349              Surgical Sciences        DVM 1993 Michigan State University
    ## 1350                   Biochemistry    PHD 2003 Univ of Michigan at Ann Arbor
    ## 1351                    Mathematics          PHD 2019 Northeastern University
    ## 1352          Counseling Psychology        PHD 2020 Univ of Wisconsin-Madison
    ## 1353  Journalism&Mass Communication               MA 2004 New York University
    ## 1354                      Chemistry           PHD 2006 Katholieke Univ Leuven
    ## 1355            Engineering Physics        PHD 2009 Univ of Wisconsin-Madison
    ## 1356      Animal And Dairy Sciences            PHD 2008 University of Arizona
    ## 1357         Spanish And Portuguese             PHD 2004 University of Kansas
    ## 1358                Medical Physics        PHD 2016 Univ of Wisconsin-Madison
    ## 1359                      Radiology   PHD 2010 Univ of IL at Urbana-Champaign
    ## 1360                        Physics    PHD 1998 Univ of Maryland College Park
    ## 1361  Operations & Information Mgmt        PHD 2005 Univ of Wisconsin-Madison
    ## 1362                            Art             MFA Univ of Wisconsin-Madison
    ## 1363              Political Science            PHD 1999 University of Chicago
    ## 1364                     Psychiatry        PHD 2006 Univ of Wisconsin-Madison
    ## 1365        Comparative Biosciences               PHD 2004 Harvard University
    ## 1366                   Bacteriology      PHD 2016 Univ of California Berkeley
    ## 1367                        Nursing         MS Concordia University Wisconsin
    ## 1368          Afro-American Studies        PHD 1995 Univ of Wisconsin-Madison
    ## 1369                 Design Studies        MFA 2018 Univ of Wisconsin-Madison
    ## 1370             Emergency Medicine                   MD 2007 Mayo Foundation
    ## 1371    Mead Witter School Of Music     MM 1992 New England Cnsrvtry Of Music
    ## 1372              Computer Sciences       PHD 2001 Univ Autonoma de Barcelona
    ## 1373     Civil & Environmental Engr      PHD 2014 Univ of Illinois at Chicago
    ## 1374                    Social Work        MSW 2015 Univ of Wisconsin-Madison
    ## 1375                       Pharmacy        PHD 1984 Univ of Wisconsin-Madison
    ## 1376         Spanish And Portuguese        PHD 1979 Univ Of Minnesota-St Paul
    ## 1377 Hawk Center For Invst Analysis         MS 1989 Univ of Wisconsin-Madison
    ## 1378                Family Medicine       MPAS 1998 Univ of Nebraska at Omaha
    ## 1379                      Chemistry        PHD 2003 University of Southampton
    ## 1380  Vp Diversity And Climate Prog        EDM 2020 Univ of Wisconsin-Madison
    ## 1381  Ed Leadership&Policy Analysis               PHD 2010 Indiana University
    ## 1382                    Kinesiology       MA 2004 Western Michigan University
    ## 1383  Engr Professional Development                   PHD 2017 Boston College
    ## 1384                            Art      MFA 1997 Univ of Southern California
    ## 1385                        Nursing               MSN 2006 Viterbo University
    ## 1386  Engr Professional Development        EDM 1987 Univ of Wisconsin-Madison
    ## 1387                        History             PHD 1998 Princeton University
    ## 1388                            Art            MFA 1997 Texas Tech University
    ## 1389 Atmospheric & Oceanic Sciences         PHD 1985 University of Washington
    ## 1390     Electrical & Computer Engr             PHD 1981 University of Oxford
    ## 1391       Pathobiological Sciences               PHD 2010 Indiana University
    ## 1392                       Genetics        PHD 2007 Univ of Wisconsin-Madison
    ## 1393             Emergency Medicine     MD 2010 Univ of Minnesota-Twin Cities
    ## 1394     Curriculum And Instruction              PHD 2008 Columbia University
    ## 1395                  Asian Amer St     PHD 2017 Univ of California San Diego
    ## 1396  Engr Professional Development         MS 1982 Univ of Wisconsin-Madison
    ## 1397                      Marketing   PHD 2014 Univ of California Los Angeles
    ## 1398                        Surgery       MD 1983 Thomas Jefferson University
    ## 1399                            Art        PHD 2009 Univ of Wisconsin-Madison
    ## 1400  Vp Diversity And Climate Prog         MS 2013 Univ of Wisconsin-Madison
    ## 1401        Obstetrics & Gynecology         MD 2007 Univ of Wisconsin-Madison
    ## 1402       Pathobiological Sciences               DVM 2004 Cornell University
    ## 1403     Electrical & Computer Engr         MS 1991 Univ of Wisconsin-Madison
    ## 1404                    Social Work        MSW 2014 Univ of Wisconsin-Madison
    ## 1405                      Chemistry     PHD 1997 Eberhard Karls Univ Tubingen
    ## 1406   Wisconsin School Of Business        PHD 2005 Univ of Wisconsin-Madison
    ## 1407                   Biochemistry            PHD 1982 Washington University
    ## 1408                          Dance                MA 2014 University of Iowa
    ## 1409                Plant Pathology                                  PHD 2020
    ## 1410              Academic Programs             PHD 2001 Princeton University
    ## 1411              Surgical Sciences                                  DVM 2015
    ## 1412               Medical Sciences        DVM 2014 Univ of Wisconsin-Madison
    ## 1413          Ex Mba Program Office        PHD 2008 Univ of Wisconsin-Madison
    ## 1414                       Medicine          MD 1995 University of Louisville
    ## 1415                       Pharmacy    PHD 2006 Univ of Michigan at Ann Arbor
    ## 1416   Management & Human Resources    PHD 2015 Univ of Minnesota-Twin Cities
    ## 1417     Civil & Environmental Engr                                        MS
    ## 1418                      Chemistry            PHD 1990 University of Bristol
    ## 1419  Ophthalmology&Visual Sciences    PHD 2010 International Univ in Germany
    ## 1420                 Design Studies        PHD 2009 Univ of Wisconsin-Madison
    ## 1421 Liberal Arts & Applied Studies        EDD 2012 Univ of Wisconsin-Madison
    ## 1422        Comparative Biosciences      PHD 2003 Univ of Illinois at Chicago
    ## 1423       Disease Prevention Admin               PHD 2007 Cornell University
    ## 1424              Academic Programs   PHD 2003 Australian National University
    ## 1425                   Biochemistry       PHD 2006 Massachusetts Inst Of Tech
    ## 1426                         Botany    PHD 1988 Univ of Minnesota-Twin Cities
    ## 1427       Gender And Women Studies        PHD 1998 Univ of Wisconsin-Madison
    ## 1428                      Economics   PHD 2006 Queen's University at Kingston
    ## 1429             Communication Arts             PHD 2001 University of Oregon
    ## 1430      Forest & Wildlife Ecology        PHD 2020 Univ of Wisconsin-Madison
    ## 1431                      Chemistry   PHD 2019 Univ of California Los Angeles
    ## 1432      Planning & Landscape Arch        PHD 1975 Univ of Wisconsin-Madison
    ## 1433             Communication Arts      PHD 2012 Univ of Southern California
    ## 1434          Counseling Psychology       PHD 1995 Virginia Commonwealth Univ
    ## 1435                       Medicine        PHD 2014 Univ of Wisconsin-Madison
    ## 1436                        History            PHD 1999 University of Chicago
    ## 1437                      Neurology              PHD 1986 Columbia University
    ## 1438              Computer Sciences       PHD 2017 University of Pennsylvania
    ## 1439                       Pharmacy            PHD 1994 University of Chicago
    ## 1440  Materials Science&Engineering              PHD 2013 Tsinghua University
    ## 1441                       Pharmacy             PHD North Carolina State Univ
    ## 1442     Electrical & Computer Engr      PHD 1982 Univ of Southern California
    ## 1443                   Soil Science          PHD 2017 Univ of New South Wales
    ## 1444                        English      PHD 2017 City University Of New York
    ## 1445                      Geography          PHD 2011 George Mason University
    ## 1446                    Mathematics                                  PHD 2018
    ## 1447     Department Of Neuroscience                 PHD 2003 Brown University
    ## 1448                      Neurology               PHD 1998 Harvard University
    ## 1449   Management & Human Resources         JD 1998 Univ of Wisconsin-Madison
    ## 1450            Integrative Biology              DS Univ Of Nevada, Las Vegas
    ## 1451         Educational Psychology     PHD 2004 Univ of California San Diego
    ## 1452     Chemical & Biological Engr        PHD 2005 Univ of Wisconsin-Madison
    ## 1453                            Art       MFA 2005 Virginia Commonwealth Univ
    ## 1454     Curriculum And Instruction              PHD 2010 Stanford University
    ## 1455         Biomolecular Chemistry    PHD 2000 U of California San Francisco
    ## 1456                     Law School      PHD 2006 Univ of California Berkeley
    ## 1457                Family Medicine         MD 1989 Univ of Wisconsin-Madison
    ## 1458                 Design Studies         MA 2011 Univ of Wisconsin-Madison
    ## 1459     Asian Languages & Cultures               PHD 1996 Harvard University
    ## 1460     Civil & Environmental Engr        PHD 1988 Univ of Wisconsin-Madison
    ## 1461  Communication Sci & Disorders   PHD 1999 University of Nebraska-Lincoln
    ## 1462             Information School        PHD 2009 Univ of Wisconsin-Madison
    ## 1463         Spanish And Portuguese            PHD 1984 University of Chicago
    ## 1464                       Pharmacy    PHARMD 1981 Univ of Tennessee, Memphis
    ## 1465                     Pediatrics                MD 1988 Harvard University
    ## 1466  Classic & Ancient Near E Stds               PHD 2005 Harvard University
    ## 1467                        English       PHD 2019 Univ of Texas at Arlington
    ## 1468                   Food Science         PHD 2012 Univ of California Davis
    ## 1469                     Psychology      PHD 1972 Univ of California Berkeley
    ## 1470    Mead Witter School Of Music                  PHD 1989 Yale University
    ## 1471             School For Workers        PHD 2010 Univ of California Irvine
    ## 1472                     Law School         JD 1979 Univ of Wisconsin-Madison
    ## 1473                        History            PHD 2011 University of Chicago
    ## 1474                    Mathematics         PHD 2012 Univ of California Davis
    ## 1475                       Genetics              PHD 1997 University of Tokyo
    ## 1476                   Food Science              PHD 1998 University of Tokyo
    ## 1477                       Pharmacy       MSSW 2005 Univ of Wisconsin-Madison
    ## 1478             Information School         MA 2014 Univ of Wisconsin-Madison
    ## 1479                   Food Science               PHD 1988 Cornell University
    ## 1480   Se Asian Summer Studies Inst                                  EDD 1997
    ## 1481       Gender And Women Studies         PHD 2008 University of Copenhagen
    ## 1482             Information School        MLIS 2016 University of Washington
    ## 1483                        English         MA 2005 Univ of Wisconsin-Madison
    ## 1484           Neurological Surgery        MD 1989 University of Pennsylvania
    ## 1485                    Mathematics       PHD 2012 St. Petersburg State Univ.
    ## 1486            Integrative Biology             PHD 1988 Princeton University
    ## 1487                 Human Oncology   PHD 2004 Maharaja Sayajirao U of Baroda
    ## 1488          Counseling Psychology                     EDM DePaul University
    ## 1489          Counseling Psychology               EDM 2012 University of Iowa
    ## 1490        Comparative Biosciences        DVM 2010 Univ of Wisconsin-Madison
    ## 1491               Academic Affairs         MS 1996 Univ of Wisconsin-Madison
    ## 1492  Ed Leadership&Policy Analysis               PHD 2000 University of Iowa
    ## 1493     Department Of Neuroscience                  PHD 1977 Yale University
    ## 1494                       Agronomy      PHD 2002 Univ of California Berkeley
    ## 1495         Mechanical Engineering      PHD 2016 Univ of Wisconsin-Milwaukee
    ## 1496                        Nursing      DNP 2017 Univ of Wisconsin-Milwaukee
    ## 1497               Academic Affairs          MPH 2019 Grand Canyon University
    ## 1498               Medical Sciences                                  DVM 2016
    ## 1499             Communication Arts   PHD 1986 Univ of California Los Angeles
    ## 1500 Lafollette Sch Of Publ Affairs        PHD 2015 Univ of Wisconsin-Madison
    ## 1501     Electrical & Computer Engr       PHD 1978 Massachusetts Inst Of Tech
    ## 1502                       Medicine            MD 1980 University Of Damascus
    ## 1503                        Urology            MD 1989 University of Virginia
    ## 1504        School Of Human Ecology        PHD 1984 Univ of Wisconsin-Madison
    ## 1505             Communication Arts        PHD 2009 Univ of Wisconsin-Madison
    ## 1506  Cell And Regenerative Biology             PHD 1966 University of Oxford
    ## 1507         Educational Psychology      PHD 2010 Cardinal Stritch University
    ## 1508          Ft Mba Program Office                  MA 2013 Lakeland College
    ## 1509             Information School    PHD 2007 Iowa State Univ of Sci & Tech
    ## 1510                      Sociology    PHD 2018 University of Texas at Austin
    ## 1511            Integrative Biology        PHD 2008 Univ of Wisconsin-Madison
    ## 1512     Asian Languages & Cultures        PHD Calif. State Univ. Los Angeles
    ## 1513                Medical Physics          PHD 1999 University of Ljubljana
    ## 1514                  Asian Amer St        PHD 1994 Univ of Wisconsin-Madison
    ## 1515              Computer Sciences       PHD 1996 Carnegie-Mellon University
    ## 1516     Electrical & Computer Engr               PHD 2001 Cornell University
    ## 1517                        Surgery               PHD 1991 University of Iowa
    ## 1518                       Pharmacy                 PHD 2008 Brown University
    ## 1519             Information School         PHD 2016 University of Pittsburgh
    ## 1520             Bba Program Office         MA 2014 Univ of Wisconsin-Madison
    ## 1521                      Chemistry               PHD 2002 Cornell University
    ## 1522     Electrical & Computer Engr      PHD 2015 Univ of California Berkeley
    ## 1523                        Finance        PHD 1978 Univ of Wisconsin-Madison
    ## 1524                       Medicine                MD 1995 Harvard University
    ## 1525          Ev Mba Program Office              MS Univ of Wisconsin-Madison
    ## 1526                        English               MPS 1996 Cornell University
    ## 1527              Academic Programs        PHD 2000 Univ of Wisconsin-Madison
    ## 1528              Surgical Sciences        PHD 2002 Univ of Wisconsin-Madison
    ## 1529            Air Force Aerospace    MS 2012 Embry Riddle Aeronautical Univ
    ## 1530                      Economics         MS 1986 London Sch Econ& Poli Sci
    ## 1531             Communication Arts        PHD 2009 Univ of Wisconsin-Madison
    ## 1532                   Bacteriology        DS 1984 Massachusetts Inst Of Tech
    ## 1533                       Pharmacy        PHD 1992 Univ of Wisconsin-Madison
    ## 1534             Communication Arts    PHD 2008 Pennsylvania State University
    ## 1535    Mead Witter School Of Music    PHD 1997 Univ of Michigan at Ann Arbor
    ## 1536                Medical Physics        PHD 2008 Univ of Wisconsin-Madison
    ## 1537       Gender And Women Studies                  PHD 2019 Yale University
    ## 1538                        English             PHD Univ of Wisconsin-Madison
    ## 1539  Ed Leadership&Policy Analysis              PHD 1995 Columbia University
    ## 1540  Real Estate & Urgan Land Econ    MBA 1993 North Dakota State University
    ## 1541           Nutritional Sciences         MS 1992 Univ of Wisconsin-Madison
    ## 1542           Nutritional Sciences        PHD 2013 Univ of Wisconsin-Madison
    ## 1543               Risk & Insurance        PHD 2008 Univ of Wisconsin-Madison
    ## 1544     Population Health Sciences                PHD 1993 Boston University
    ## 1545        Comparative Biosciences               PHD 1990 University of Iowa
    ## 1546                       Medicine         PHD 1997 Brigham Young University
    ## 1547                        History                  PHD 1993 Yale University
    ## 1548 Lafollette Sch Of Publ Affairs            PHD 2010 University of Chicago
    ## 1549 Agricultural&Applied Economics    PHD 2017 Univ of Michigan at Ann Arbor
    ## 1550             Community Dev Inst     PHD 2014 Fielding Graduate University
    ## 1551                Theatre & Drama              MFA Florida State University
    ## 1552               Consumer Science        MSA 2002 Univ of Wisconsin-Madison
    ## 1553     Asian Languages & Cultures            PHD 2018 University of Chicago
    ## 1554                      Neurology        PHD 2000 Univ of Wisconsin-Madison
    ## 1555                        Nursing             DNP 2018 Marquette University
    ## 1556     Department Of Neuroscience            PHD 1993 University of Chicago
    ## 1557                            Art                 MFA 2005 Columbia College
    ## 1558                            Art            MFA 2008 University of Arizona
    ## 1559              Academic Services      MS 1996 Univ of Wisconsin-Whitewater
    ## 1560                         Botany               PHD 2009 Heidelberg College
    ## 1561                       Medicine        PHD 1991 Univ of Wisconsin-Madison
    ## 1562        Comparative Biosciences       PHD 2001 Case Western Reserve Univ.
    ## 1563  Engr Professional Development        PHD 2017 Univ of Wisconsin-Madison
    ## 1564                        English                 PHD 2015 Brown University
    ## 1565                        Physics    PHD 1982 Univ of Maryland College Park
    ## 1566  Rehab Psychology & Special Ed        EDD 2015 Illinois State University
    ## 1567                          Dance                             BFA Argentina
    ## 1568   Ctr For Brand & Product Mgmt                 MA 1988 DePaul University
    ## 1569                   Horticulture        PHD 1997 North Carolina State Univ
    ## 1570               Academic Affairs        PHD 1994 Seoul National University
    ## 1571                        Surgery           MD 2007 Northwestern University
    ## 1572          Counseling Psychology                 MAED Marquette University
    ## 1573                Plant Pathology          PHD 2007 Kansas State University
    ## 1574                          Dance         MS 2006 Univ of Wisconsin-Madison
    ## 1575                       Agronomy        PHD 1990 Univ Of Minnesota-St Paul
    ## 1576                       Agronomy        PHD 1992 Univ Of Minnesota-St Paul
    ## 1577                       Medicine         MD 2012 Univ of Wisconsin-Madison
    ## 1578                      Geography        PHD 1988 Univ of Missouri-Columbia
    ## 1579                       Medicine       PHD 1993 Massachusetts Inst Of Tech
    ## 1580           Medical Microbiology              PHD 2012 McMaster University
    ## 1581                       Oncology           PHD 1997 University of Virginia
    ## 1582               Academic Affairs                                  MPH 1997
    ## 1583                     Psychiatry             DO 2013 Midwestern University
    ## 1584                     Psychiatry       MD 1976 Thomas Jefferson University
    ## 1585               Consumer Science       MA 1979 Univ of Wisconsin-Milwaukee
    ## 1586        School Of Human Ecology        MFA 2000 Univ of Wisconsin-Madison
    ## 1587         Educational Psychology               EDD 2015 Harvard University
    ## 1588     Civil & Environmental Engr          PHD 2012 Northwestern University
    ## 1589  Engr Professional Development                MSA 1994 Purdue University
    ## 1590                       Medicine            PHD 1987 University of Chicago
    ## 1591     Population Health Sciences      PHD 1978 Univ of California Berkeley
    ## 1592                        Nursing   DNP 2015 Concordia University Wisconsin
    ## 1593                     Statistics       PHD 2015 University of Pennsylvania
    ## 1594  Cell And Regenerative Biology        PHD 2010 Seoul National University
    ## 1595 Engineering Student Developmnt      MS 2012 Univ of Wisconsin-Whitewater
    ## 1596                        History             PHD 1995 Princeton University
    ## 1597             Information School           EDD 2006 University of Delaware
    ## 1598         Educational Psychology   PHD 1987 Univ of California Los Angeles
    ## 1599                       Pharmacy          PHARMD Univ of Wisconsin-Madison
    ## 1600              Political Science        PHD 2005 Univ of Wisconsin-Madison
    ## 1601          Counseling Psychology                  MAED Salem State College
    ## 1602      Forest & Wildlife Ecology   PHD 1981 Univ of California Los Angeles
    ## 1603                        Physics           PHD 1994 Fachhochschule Munchen
    ## 1604    Mead Witter School Of Music         MM 1977 Univ of Wisconsin-Madison
    ## 1605        German, Nordic & Slavic        PHD 2015 Univ of Wisconsin-Madison
    ## 1606 Biological Systems Engineering    PHD 1997 Pennsylvania State University
    ## 1607  Engr Professional Development                                  PHD 1997
    ## 1608    Mead Witter School Of Music         DM 2020 Univ of Wisconsin-Madison
    ## 1609                     Law School              JD 1983 Marquette University
    ## 1610                   Bacteriology    PHD 1986 Iowa State Univ of Sci & Tech
    ## 1611                     Law School                JD 2004 University of Iowa
    ## 1612                     Pediatrics             MD 2010 University of Chicago
    ## 1613               Consumer Science        MBA 2010 Univ of Wisconsin-Madison
    ## 1614     Electrical & Computer Engr               PHD 2013 Harvard University
    ## 1615  Communication Sci & Disorders          PHD 2007 Northwestern University
    ## 1616              Academic Programs        EDM 2013 Univ Of Missouri-St Louis
    ## 1617       Pathobiological Sciences              PHD 1983 Hokkaido University
    ## 1618  Materials Science&Engineering    PHD 2014 U of California-Santa Barbara
    ## 1619      Animal And Dairy Sciences     MS 1993 Iowa State Univ of Sci & Tech
    ## 1620     Civil & Environmental Engr    MA 1980 Univ of IL at Urbana-Champaign
    ## 1621                    Social Work       MSSW 2002 Univ of Wisconsin-Madison
    ## 1622                        Nursing                  DNP 2016 Rush University
    ## 1623         Biomolecular Chemistry      PHD 1997 Univ of California Berkeley
    ## 1624              Political Science          PHD 2012 University Of Rochester
    ## 1625                         Botany      PHD 2008 Univ of Colorado at Boulder
    ## 1626        School Of Human Ecology    PHD 2016 Univ of Minnesota-Twin Cities
    ## 1627                    Dermatology                  PHD 2011 Mayo Foundation
    ## 1628               Medical Sciences        DVM 2016 Univ of Wisconsin-Madison
    ## 1629                     Statistics        PHD 2012 Univ Of NC At Chapel Hill
    ## 1630                     Statistics      PHD 2003 Univ of California Berkeley
    ## 1631  Dept Of Med History&Bioethics               PHD 2008 Cornell University
    ## 1632          Counseling Psychology                MA 2016 Middlebury College
    ## 1633           Medical Microbiology               PHD 1990 Cornell University
    ## 1634  Dept Of Med History&Bioethics        PHD 2001 Rutgers State Univ-Newark
    ## 1635  Ed Leadership&Policy Analysis              PHD 1993 Stanford University
    ## 1636                     Law School              JD 2009 Marquette University
    ## 1637                        English          PHD 1977 Northwestern University
    ## 1638               Medical Sciences   DVM 2002 Univ of IL at Urbana-Champaign
    ## 1639  Communication Sci & Disorders      MA 1989 Northern Illinois University
    ## 1640 Liberal Arts & Applied Studies             PHD Univ of Wisconsin-Madison
    ## 1641                     Geoscience        PHD 1999 Univ Of NC At Chapel Hill
    ## 1642                      Economics                     BA 1977 Smith College
    ## 1643                     Law School         JD 1991 Univ of Wisconsin-Madison
    ## 1644         Educational Psychology        PHD 2006 Univ of Wisconsin-Madison
    ## 1645      Planning & Landscape Arch            MLA 1987 University of Arizona
    ## 1646                    Mathematics                 PHD 2015 Universitat Bonn
    ## 1647     Educational Policy Studies              PHD 2004 Stanford University
    ## 1648  Biostatistics&Med Informatics             PHD 1998 Marquette University
    ## 1649                      Economics          PHD 1973 Northwestern University
    ## 1650                        History               PHD 2018 Harvard University
    ## 1651                        Nursing     DNP 2013 Univ of Wisconsin-Eau Claire
    ## 1652                       Oncology                   MD 1979 Yale University
    ## 1653   Wisconsin School Of Business        PHD 2009 Univ of Wisconsin-Madison
    ## 1654                   Anthropology      PHD 1983 Univ of California Berkeley
    ## 1655                    Mathematics    PHD 2006 University of Texas at Austin
    ## 1656                     Law School         JD 1981 Univ of Wisconsin-Madison
    ## 1657                        English               MFA 1986 University of Iowa
    ## 1658     Asian Languages & Cultures               PHD 1997 Harvard University
    ## 1659        School Of Human Ecology        PHD 2017 Claremont Mckenna College
    ## 1660                     Statistics         MS 2004 Univ of Wisconsin-Madison
    ## 1661       Law, Society And Justice         PHD 2001 Johns Hopkins University
    ## 1662  Real Estate & Urgan Land Econ   PHD 2020 Univ of IL at Urbana-Champaign
    ## 1663    South Asian Sum Lang Instit                                       PHD
    ## 1664  Operations & Information Mgmt            PHD 2012 Kent State University
    ## 1665      Animal And Dairy Sciences   PHD 1994 Hebrew University of Jerusalem
    ## 1666     Asian Languages & Cultures             PHD 1997 University of Mysore
    ## 1667         Educational Psychology     EDS 2016 Univ of Wisconsin-Whitewater
    ## 1668                Family Medicine         MD 1997 Univ of Wisconsin-Madison
    ## 1669               Academic Affairs         MS 1984 Univ of Wisconsin-Madison
    ## 1670                    Social Work       MSSW 2007 Univ of Wisconsin-Madison
    ## 1671                       Medicine      MD 2005 Medical College Of Wisconsin
    ## 1672                        Nursing        DNP 2016 Univ of Wisconsin-Madison
    ## 1673         Biomolecular Chemistry   PHD 1987 Univ of IL at Urbana-Champaign
    ## 1674         Educational Psychology        PHD 2011 University of Connecticut
    ## 1675                    Mathematics                 PHD 2011 Brown University
    ## 1676                        History              PHD 2007 Columbia University
    ## 1677     Asian Languages & Cultures   PHD 2016 Univ of California Los Angeles
    ## 1678         Educational Psychology   PHD 2001 Univ of IL at Urbana-Champaign
    ## 1679             Information School    PHD 1998 University of Texas at Austin
    ## 1680  Biostatistics&Med Informatics        PHD 1985 Univ of Wisconsin-Madison
    ## 1681                        History    PHD 2011 Univ of Michigan at Ann Arbor
    ## 1682                   Anthropology      PHD 2010 Univ of Illinois at Chicago
    ## 1683  Operations & Information Mgmt       PHD 2001 Georgia Inst of Technology
    ## 1684              Computer Sciences         PHD 2020 University of Washington
    ## 1685     Curriculum And Instruction         PHD 2014 Florida State University
    ## 1686  Journalism&Mass Communication   PHD 2004 Univ of IL at Urbana-Champaign
    ## 1687     Electrical & Computer Engr        PHD 2013 Seoul National University
    ## 1688                   Biochemistry      PHD 1978 Univ of Colorado at Boulder
    ## 1689             Accting & Info Sys        PHD 1989 Univ of Wisconsin-Madison
    ## 1690                       Medicine        PHD 2003 Univ Of NC At Chapel Hill
    ## 1691                 Human Oncology        PHD 2003 Univ Of NC At Chapel Hill
    ## 1692                       Medicine         MD 2001 Univ of Wisconsin-Madison
    ## 1693                        Nursing        PHD 2010 Univ of Wisconsin-Madison
    ## 1694  Ed Leadership&Policy Analysis        PHD 1994 Univ of Wisconsin-Madison
    ## 1695          Ex Mba Program Office         MA 2017 Univ of Wisconsin-Madison
    ## 1696         Biomedical Engineering            PHD Georgia Inst of Technology
    ## 1697                        Nursing            PHD 1996 University of Arizona
    ## 1698                        History     PHD 2012 Univ of California San Diego
    ## 1699     Electrical & Computer Engr        PHD 2017 Univ of Wisconsin-Madison
    ## 1700                   Biochemistry                  PHD 2012 Scripps College
    ## 1701     Curriculum And Instruction        PHD 2017 Univ of Wisconsin-Madison
    ## 1702     Curriculum And Instruction        PHD 2018 Univ of Wisconsin-Madison
    ## 1703                  Asian Studies    PHD 2016 University of Texas at Austin
    ## 1704        School Of Human Ecology    PHD 2007 Univ of Massachusetts Amherst
    ## 1705      Animal And Dairy Sciences        PHD 1987 Univ of Wisconsin-Madison
    ## 1706                      Economics    PHD 2016 Univ of Minnesota-Twin Cities
    ## 1707         Biomolecular Chemistry        PHD 2014 Univ of Wisconsin-Madison
    ## 1708 Admin:Student Academic Affairs        PHD 2008 Univ of Wisconsin-Madison
    ## 1709                      Radiology     MD 2010 Univ of Alabama at Birmingham
    ## 1710     Curriculum And Instruction        PHD 2009 Univ of Wisconsin-Madison
    ## 1711                        History                      PHD 1991 Netherlands
    ## 1712                     Pediatrics                 MD 1978 Boston University
    ## 1713                      Radiology                   MD 1985 Duke University
    ## 1714         Educational Psychology    PHD 2013 Univ of Minnesota-Twin Cities
    ## 1715                     Law School         JD 2005 Univ of Wisconsin-Madison
    ## 1716     Chemical & Biological Engr   PHD 1990 Univ of IL at Urbana-Champaign
    ## 1717        German, Nordic & Slavic               PHD 2007 Indiana University
    ## 1718                     Law School        SJD 1997 Univ of Wisconsin-Madison
    ## 1719     Electrical & Computer Engr         PHD 2004 Arizona State University
    ## 1720                      Radiology                 BS 1992 Purdue University
    ## 1721  Ophthalmology&Visual Sciences         MD 2003 Univ of Wisconsin-Madison
    ## 1722           Medical Microbiology            PHD 1994 Washington University
    ## 1723                Volunteer Staff         MD 2011 Univ of Wisconsin-Madison
    ## 1724                     Law School         JD 2000 Univ of Wisconsin-Madison
    ## 1725                        Nursing         MS 2007 Univ of Wisconsin-Madison
    ## 1726                Plant Pathology        PHD 2012 Univ of Wisconsin-Madison
    ## 1727                        History          PHD 2004 Northwestern University
    ## 1728                        English         MA 1988 Univ of Wisconsin-Madison
    ## 1729                     Psychiatry               PHD 2006 University of Iowa
    ## 1730    Mead Witter School Of Music                MM 2009 Indiana University
    ## 1731         Mechanical Engineering        PHD 2012 Univ of Wisconsin-Madison
    ## 1732 Lafollette Sch Of Publ Affairs              MA 2001 Concordia University
    ## 1733                        Physics               PHD 2015 Harvard University
    ## 1734                        Nursing   MSN 2016 Chamberlain College of Nursing
    ## 1735                    Kinesiology        PHD 1990 Univ of Wisconsin-Madison
    ## 1736                    Social Work                   PHD 2016 Boston College
    ## 1737                       Medicine            PHD 2012 Ball State University
    ## 1738                     Psychology    PHD 1988 Univ of Maryland College Park
    ## 1739                       Pharmacy         MS 2017 Univ of Wisconsin-Madison
    ## 1740     Electrical & Computer Engr          PHD California Institute of Tech
    ## 1741                          Dance                 MA 1983 Drexel University
    ## 1742                      Radiology        PHD 1991 Univ of Wisconsin-Madison
    ## 1743                     Law School                                   JD 1981
    ## 1744                      Wiscience         MS 2008 Univ of Wisconsin-Madison
    ## 1745                      Neurology                  PHD 2007 Duke University
    ## 1746                      Astronomy        PHD 2010 Univ of Wisconsin-Madison
    ## 1747  Materials Science&Engineering       PHD 1977 Massachusetts Inst Of Tech
    ## 1748              Computer Sciences         PHD 2015 University of Washington
    ## 1749        Biology Core Curriculum             PHD Univ of Wisconsin-Madison
    ## 1750               Medical Sciences                                  DVM 2015
    ## 1751     Curriculum And Instruction    PHD 1988 Univ of Minnesota-Twin Cities
    ## 1752               Academic Affairs        PHD 1984 Univ of Wisconsin-Madison
    ## 1753     Electrical & Computer Engr         MS 2002 Univ of Wisconsin-Madison
    ## 1754                     Law School         JD 2011 Univ of Wisconsin-Madison
    ## 1755                 Anesthesiology         MD 1988 Univ of Wisconsin-Madison
    ## 1756                    Kinesiology     EDM 1976 Northern Illinois University
    ## 1757     Curriculum And Instruction        PHD 2020 Univ of Wisconsin-Madison
    ## 1758     Curriculum And Instruction         MS 2001 Univ of Wisconsin-Madison
    ## 1759         Biomedical Engineering          PHD 2005 Northwestern University
    ## 1760  Dept Of Med History&Bioethics              PHD 2013 Stanford University
    ## 1761     Electrical & Computer Engr       PHD 2018 Georgia Inst of Technology
    ## 1762  Communication Sci & Disorders                 AUD 2008 Salus University
    ## 1763        German, Nordic & Slavic      PHD 2011 Univ of California Berkeley
    ## 1764                      Marketing        MBA 2011 Univ of Wisconsin-Madison
    ## 1765  Communication Sci & Disorders                MA 1999 Indiana University
    ## 1766      Forest & Wildlife Ecology        PHD 1992 Univ of Wisconsin-Madison
    ## 1767                        Nursing                  MSN 2016 Herzing College
    ## 1768         Mechanical Engineering       PHD 1996 Case Western Reserve Univ.
    ## 1769                   Horticulture              PHD 1993 Stanford University
    ## 1770                        Nursing      PHD 1991 Univ of Wisconsin-Milwaukee
    ## 1771                       Agronomy        PHD 1997 Univ of Wisconsin-Madison
    ## 1772     Civil & Environmental Engr     BS 1979 Univ of Wisconsin-Platteville
    ## 1773           Nutritional Sciences    PHD 2017 Univ of Minnesota-Twin Cities
    ## 1774                    Social Work       MSSW 2005 Univ of Wisconsin-Madison
    ## 1775              Computer Sciences         MS 1994 Univ of Wisconsin-Madison
    ## 1776                     Pediatrics         MS 2013 Univ of Wisconsin-Madison
    ## 1777          Counseling Psychology           MS Univ of Tennessee, Knoxville
    ## 1778                    Kinesiology       MS 1987 Univ of Wisconsin-La Crosse
    ## 1779                        English               MFA 1987 University of Iowa
    ## 1780 Lafollette Sch Of Publ Affairs             MPA Univ of Wisconsin-Madison
    ## 1781        Comparative Biosciences    DVM 1996 Tamil Nadu Vet & Ani Sci Univ
    ## 1782                        Nursing        PHD 2019 Univ of Wisconsin-Madison
    ## 1783                   Bacteriology        PHD 1984 Univ of Wisconsin-Madison
    ## 1784                 Design Studies                BA 1979 Mount Mary College
    ## 1785   Management & Human Resources        PHD 1994 Univ of Wisconsin-Madison
    ## 1786                       Pharmacy            PHD 2010 University of Florida
    ## 1787                 Design Studies        MS 2008 Georgia Inst of Technology
    ## 1788                        Nursing        PHD 1999 Univ of Wisconsin-Madison
    ## 1789                     Psychiatry      MD 2008 Highland Park Community Coll
    ## 1790                    Mathematics   PHD 2020 Univ of California Los Angeles
    ## 1791                       Pharmacy               PHD 1991 University of Utah
    ## 1792                    Mathematics        PHD 2012 Michigan State University
    ## 1793              Political Science            PHD 1996 University of Chicago
    ## 1794           Nutritional Sciences        PHD 2005 Univ of Wisconsin-Madison
    ## 1795  Engr Professional Development         MS 1996 Univ of Wisconsin-Madison
    ## 1796 Ms In Biotechnology Degree Prg          MBA Northern Illinois University
    ## 1797                   Soil Science        PHD 2001 Univ Of Minnesota-St Paul
    ## 1798               Military Science    BAS 2014 Univ of Wisconsin-Platteville
    ## 1799                      Radiology        PHD 2007 Univ of Wisconsin-Madison
    ## 1800  Materials Science&Engineering        PHD 1968 Univ of Wisconsin-Madison
    ## 1801                        English   PHD 2015 Univ of IL at Urbana-Champaign
    ## 1802      Planning & Landscape Arch               PHD 1991 Cornell University
    ## 1803  Engr Professional Development        PHD 2004 Univ of Wisconsin-Madison
    ## 1804           Nutritional Sciences        PHD 1994 Univ of Wisconsin-Madison
    ## 1805                        English       MS 1987 Univ of Wisconsin-Milwaukee
    ## 1806            Engineering Physics      PHD 1975 Rensselaer Polytechnic Inst
    ## 1807                       Oncology        PHD 1985 Univ of Wisconsin-Madison
    ## 1808                       Medicine               PHD 2008 Harvard University
    ## 1809                      Chemistry        PHD 2006 Univ of Wisconsin-Madison
    ## 1810                Volunteer Staff             MD 2010 Vanderbilt University
    ## 1811  Real Estate & Urgan Land Econ        BBA 1972 Univ of Wisconsin-Madison
    ## 1812                   Biochemistry    PHD 1983 Univ of Michigan at Ann Arbor
    ## 1813                      Chemistry            PHD 1983 University of Chicago
    ## 1814                       Medicine       MD 2006 Univ of Illinois at Chicago
    ## 1815         General Administration        EDD 2012 Univ of Wisconsin-Madison
    ## 1816                            Art                BFA 2013 Alfred University
    ## 1817                Theatre & Drama             MFA Rutgers State Univ-Newark
    ## 1818                Plant Pathology         PHD 2007 Univ of California Davis
    ## 1819                    Social Work       MSSW 1998 Univ of Wisconsin-Madison
    ## 1820                        History         PHD 2007 Johns Hopkins University
    ## 1821                        Finance         PHD 2003 University of Washington
    ## 1822             Accting & Info Sys         PHD 2005 University of Washington
    ## 1823 Engineering Student Developmnt     MS 2015 Minnesota State Univ, Mankato
    ## 1824      Animal And Dairy Sciences        PHD 2014 Univ of Wisconsin-Madison
    ## 1825                         Botany      PHD 1994 Univ of California Berkeley
    ## 1826              Academic Programs        PHD 2017 Univ of Wisconsin-Madison
    ## 1827             Information School                   MS 2009 Bentley College
    ## 1828                    Social Work       MSSW 1996 Univ of Wisconsin-Madison
    ## 1829                    Kinesiology      PHD 1996 Univ of Southern California
    ## 1830  Ophthalmology&Visual Sciences         MD 2014 Univ of Wisconsin-Madison
    ## 1831       Pathobiological Sciences    DVM 1987 Iowa State Univ of Sci & Tech
    ## 1832        German, Nordic & Slavic        PHD 2012 Univ of Wisconsin-Madison
    ## 1833   Wisconsin School Of Business        PHD 2014 Univ of Wisconsin-Madison
    ## 1834                    Social Work       MSSW 1989 Univ of Wisconsin-Madison
    ## 1835                      Astronomy        PHD 1989 Univ of Wisconsin-Madison
    ## 1836                       Genetics               PHD 1983 University of Utah
    ## 1837                       Pharmacy      PHD 1992 Univ of California Berkeley
    ## 1838    Mead Witter School Of Music                   MM 2013 Yale University
    ## 1839                        Nursing          PHD 1987 University Of Rochester
    ## 1840                       Medicine         MD 2011 Univ of Wisconsin-Madison
    ## 1841                        Physics        PHD 1978 Univ of Wisconsin-Madison
    ## 1842    Comp Lit & Folklore Studies      PHD 1984 Univ of California Berkeley
    ## 1843                      Astronomy          PHD 1995 University of Cambridge
    ## 1844                        Surgery                 MD 2005 Boston University
    ## 1845                        Nursing    MPH 2016 Univ of Massachusetts Amherst
    ## 1846 Atmospheric & Oceanic Sciences        PHD 2001 Colorado State University
    ## 1847  Dept Of Med History&Bioethics        PHD 1987 Univ of Wisconsin-Madison
    ## 1848      Planning & Landscape Arch           PHD 2016 Texas A & M University
    ## 1849    Mead Witter School Of Music       MM 2006 Univ of Southern California
    ## 1850            Integrative Biology     PHD 1997 Univ of California San Diego
    ## 1851     Asian Languages & Cultures                  MA 2004 Edgewood College
    ## 1852                    Kinesiology        PHD 2009 Univ of Wisconsin-Madison
    ## 1853                    Mathematics    PHD 2020 Univ of Michigan at Ann Arbor
    ## 1854                            Art    MFA 2006 Rhode Island School of Design
    ## 1855      Industrial & Systems Engr   PHD 1992 Univ of IL at Urbana-Champaign
    ## 1856                Family Medicine              MD 1996 University of Kansas
    ## 1857     Electrical & Computer Engr           PHD Univ of California Berkeley
    ## 1858       Pathobiological Sciences        DVM 2017 Univ of Wisconsin-Madison
    ## 1859  Communication Sci & Disorders        AUD 2013 Univ of Wisconsin-Madison
    ## 1860     Educational Policy Studies       PHD 1991 University of Pennsylvania
    ## 1861          Counseling Psychology      EDM 2014 Univ of Wisconsin-La Crosse
    ## 1862  Cell And Regenerative Biology        PHD 1989 Univ of Wisconsin-Madison
    ## 1863                            Art                  AS 2011 Cabrillo College
    ## 1864                        Finance         MS 1983 Univ of Wisconsin-Madison
    ## 1865              Computer Sciences        PHD 2018 Univ of Wisconsin-Madison
    ## 1866                       Pharmacy        PHD 2013 Univ of Wisconsin-Madison
    ## 1867              Political Science              PHD 2020 New York University
    ## 1868                   Anthropology            MA 2006 University of Oklahoma
    ## 1869  Rehab Psychology & Special Ed            PHD 2008 University of Florida
    ## 1870       Gender And Women Studies        PHD 2012 Univ of Wisconsin-Madison
    ## 1871     Curriculum And Instruction         MA 2014 Univ of Wisconsin-Madison
    ## 1872                    Mathematics            PHD 1986 University of Chicago
    ## 1873       Pathobiological Sciences        DVM 2003 Univ of Wisconsin-Madison
    ## 1874                      Economics          PHD 2002 Northwestern University
    ## 1875              Surgical Sciences                 DVM 2016 Tufts University
    ## 1876      Animal And Dairy Sciences        PHD 2009 Univ of Wisconsin-Madison
    ## 1877                   Anthropology      PHD 1981 Univ of California Berkeley
    ## 1878       Pathobiological Sciences                                  DVM 2011
    ## 1879     Electrical & Computer Engr   PHD 1993 Univ of IL at Urbana-Champaign
    ## 1880                    Mathematics                                  PHD 2018
    ## 1881     Electrical & Computer Engr              PHD 2011 Stanford University
    ## 1882                        Physics    PHD 2009 Univ of Minnesota-Twin Cities
    ## 1883 Human Development&Family Study    PHD 2013 Univ of Minnesota-Twin Cities
    ## 1884                     Law School         JD 1974 Univ of Wisconsin-Madison
    ## 1885               Risk & Insurance         PHD 2005 Georgia State University
    ## 1886                     Statistics         PHD 2017 Johns Hopkins University
    ## 1887                        Finance       PHD 2011 University of Pennsylvania
    ## 1888       Gender And Women Studies                 PHS University of Florida
    ## 1889 Ms In Biotechnology Degree Prg        PHD 1994 Michigan State University
    ## 1890         Biomolecular Chemistry      PHD 2006 Univ of California Berkeley
    ## 1891          Ex Mba Program Office         JD 1999 Univ of Wisconsin-Madison
    ## 1892              Computer Sciences    PHD 2004 VA Polytechnic Inst & State U
    ## 1893                          Dance    MA 1989 Univ of California Los Angeles
    ## 1894                     Psychology   PHD 2013 Univ of California Los Angeles
    ## 1895      Industrial & Systems Engr    PHD 2000 Univ of Michigan at Ann Arbor
    ## 1896                Medical Physics        PHD 2013 Univ of Wisconsin-Madison
    ## 1897                       Pharmacy   PHD 2000 Univ of IL at Urbana-Champaign
    ## 1898   Management & Human Resources                  PHD 2008 Duke University
    ## 1899    Life Sciences Communication        PHD 2015 Univ of Wisconsin-Madison
    ## 1900                    Mathematics        PHD 2013 Univ of Wisconsin-Madison
    ## 1901              Computer Sciences               PHD 2017 Cornell University
    ## 1902 Orthopedics And Rehabilitation      PHD 2004 Thomas Jefferson University
    ## 1903        German, Nordic & Slavic            PHD 2009 Ohio State University
    ## 1904      Language Sciences Program       PHD 1990 Massachusetts Inst Of Tech
    ## 1905  Biostatistics&Med Informatics       PHD 2017 Georgia Inst of Technology
    ## 1906                    Art History            PHD 2011 University of Chicago
    ## 1907              Computer Sciences       PHD 2014 Georgia Inst of Technology
    ## 1908           Medical Microbiology     PHD 2013 Univ of California San Diego
    ## 1909                        Surgery                     MD 1996 Touro College
    ## 1910             Accting & Info Sys       MACC 2020 Univ of Wisconsin-Madison
    ## 1911                      Sociology    PHD 2013 Pennsylvania State University
    ## 1912     Civil & Environmental Engr         PHD 2000 Colorado School of Mines
    ## 1913     Asian Languages & Cultures               PHD 2003 Indiana University
    ## 1914                      Sociology               PHD 2007 Harvard University
    ## 1915                   Biochemistry      PHD 2014 National Univ. of Singapore
    ## 1916                       Pharmacy        PHARMD 2016 University of Oklahoma
    ## 1917  Engr Professional Development        PHD 1988 Univ of Wisconsin-Madison
    ## 1918     Population Health Sciences        PHD 2008 Univ of Wisconsin-Madison
    ## 1919          Counseling Psychology        PHD 2017 Univ of Wisconsin-Madison
    ## 1920      Industrial & Systems Engr       PHD 1998 Georgia Inst of Technology
    ## 1921            Engineering Physics                                       PHD
    ## 1922                     Entomology   PHD 1984 Univ of IL at Urbana-Champaign
    ## 1923       Gender And Women Studies            PHD 2009 University of Chicago
    ## 1924                    Mathematics                PHD 2011 Purdue University
    ## 1925       Office Of Sustainability        PHD 2020 Univ of Wisconsin-Madison
    ## 1926             Accting & Info Sys        PHD 1985 Univ of Wisconsin-Madison
    ## 1927               Academic Affairs     PHARMD 2001 Univ of Wisconsin-Madison
    ## 1928                     Geoscience        PHD 2017 Univ of Wisconsin-Madison
    ## 1929     Electrical & Computer Engr       PHD 1997 Carnegie-Mellon University
    ## 1930        Comparative Biosciences        PHD 2008 Univ of Wisconsin-Madison
    ## 1931                Theatre & Drama                  MFA 2009 Yale University
    ## 1932  Communication Sci & Disorders    PHD 1991 Univ of Massachusetts Amherst
    ## 1933        School Of Human Ecology        PHD 2013 Univ of Wisconsin-Madison
    ## 1934                        Surgery    PHD 1993 SUNY Health Sci Cntr-Syracuse
    ## 1935                       Medicine       MD 1997 Thomas Jefferson University
    ## 1936      Industrial & Systems Engr       PHD 2013 Georgia Inst of Technology
    ## 1937                      Marketing            PHD 2006 Ohio State University
    ## 1938     Educational Policy Studies       PHD 2019 University of Pennsylvania
    ## 1939                           #N/A               PHD 2001 Harvard University
    ## 1940             French And Italian        PHD 1990 University of Connecticut
    ## 1941   Se Asian Summer Studies Inst        PHD 2010 Univ of Wisconsin-Madison
    ## 1942  Ctr For Integrated Agric Syst        PHD 2012 Univ of Wisconsin-Madison
    ## 1943  Cell And Regenerative Biology       PHD 2010 Univ degli Studi di Milano
    ## 1944              Political Science     PHD 2016 Univ of California San Diego
    ## 1945                       Medicine       MD 2000 Univ of Illinois at Chicago
    ## 1946                       Oncology        PHD 1988 Univ Of NC At Chapel Hill
    ## 1947              Surgical Sciences        DVM 2015 Colorado State University
    ## 1948                       Genetics        PHD 2005 Colorado State University
    ## 1949  Real Estate & Urgan Land Econ             JD 2003 Washington University
    ## 1950                     Statistics      PHD 2014 Univ of California Berkeley
    ## 1951                     Statistics      PHD 1982 Univ of California Berkeley
    ## 1952     Civil & Environmental Engr              PHD 2006 Stanford University
    ## 1953                    Kinesiology    PHD 1993 Univ Of Maryland At Baltimore
    ## 1954 Human Development&Family Study         PHD 2020 Florida State University
    ## 1955                 Anesthesiology         MD 2009 Univ of Wisconsin-Madison
    ## 1956  Journalism&Mass Communication                 MBA Pepperdine University
    ## 1957  Operations & Information Mgmt     PHD 2017 Hong Kong Univ of Sci & Tech
    ## 1958                Volunteer Staff      MD 1990 Medical College Of Wisconsin
    ## 1959                       Pharmacy        PHD 2013 Univ of Wisconsin-Madison
    ## 1960             Communication Arts               PHD 2011 Indiana University
    ## 1961             Communication Arts      PHD 2012 Univ of Southern California
    ## 1962                   Food Science          PHD 2006 Universidad Veracruzana
    ## 1963                        Nursing        PHD 2017 Univ of Wisconsin-Madison
    ## 1964        Comparative Biosciences        PHD 1992 Univ of Wisconsin-Madison
    ## 1965                        Nursing      MSN 2012 Maryville Univ Of St. Louis
    ## 1966                        Nursing      DNP 2012 Univ of Wisconsin-Milwaukee
    ## 1967          Counseling Psychology                                 MSED 2014
    ## 1968          Counseling Psychology         PHD 2001 Arizona State University
    ## 1969        German, Nordic & Slavic               PHD 1988 Cornell University
    ## 1970     Curriculum And Instruction      PHD 2015 Univ of California Berkeley
    ## 1971  Rehab Psychology & Special Ed             PHD 2018 University of Kansas
    ## 1972                     Geoscience        PHD 2012 Univ of Wisconsin-Madison
    ## 1973                    Amer Ind St    MFA 2009 Rhode Island School of Design
    ## 1974                      Geography     PHD 2005 U of California Ext-Berkeley
    ## 1975  Biostatistics&Med Informatics                  PHD 2017 Yale University
    ## 1976                       Medicine         MD 2003 Univ of Wisconsin-Madison
    ## 1977                Family Medicine                   MD 2013 Yale University
    ## 1978     Educational Policy Studies        PHD 2016 Univ of Wisconsin-Madison
    ## 1979                   Food Science                   PHD 1992 Ireland (Eire)
    ## 1980                       Medicine    MD 1985 Univ of Dublin-Trinity College
    ## 1981 Biological Systems Engineering     PHD 2013 Mississippi State University
    ## 1982     Electrical & Computer Engr        PHD 2011 Univ of Wisconsin-Madison
    ## 1983                   Anthropology        PHD 2018 Univ of Wisconsin-Madison
    ## 1984         Biomedical Engineering                                       PHD
    ## 1985      Industrial & Systems Engr       PHD 2007 Georgia Inst of Technology
    ## 1986           Grainger Ctr For Scm        MBA 2001 Univ of Wisconsin-Madison
    ## 1987                    Mathematics        PHD 2007 Univ of California Irvine
    ## 1988              Surgical Sciences        DVM 2007 Univ of Wisconsin-Madison
    ## 1989                     Psychology       PHD 2007 Carnegie-Mellon University
    ## 1990      Planning & Landscape Arch                  PHD 2015 SUNY at Buffalo
    ## 1991      Forest & Wildlife Ecology          PHD 1987 Oregon State University
    ## 1992                      Neurology     MD 1993 Univ of Kansas Medical Center
    ## 1993             Accting & Info Sys        PHD 2014 Michigan State University
    ## 1994     Chemical & Biological Engr     PHD 1999 California Institute of Tech
    ## 1995            Integrative Biology        PHD 1984 Univ of Wisconsin-Madison
    ## 1996     Electrical & Computer Engr       PHD 2019 Massachusetts Inst Of Tech
    ## 1997     Electrical & Computer Engr    PHD 2001 Univ of Michigan at Ann Arbor
    ## 1998          Counseling Psychology            MFA 2005 University of Montana
    ## 1999      Language Sciences Program      PHD 1987 Univ of California Berkeley
    ## 2000                     Psychology   PHD 1986 Univ of California Los Angeles
    ## 2001                            Art        MFA 2017 Univ of Wisconsin-Madison
    ## 2002                Plant Pathology        PHD 1983 Michigan State University
    ## 2003     Curriculum And Instruction      PHD 2018 Univ of Illinois at Chicago
    ## 2004 Ms In Biotechnology Degree Prg   PHD 2016 Technische Universitat Munchen
    ## 2005                       Is Major     PHD 2002 Univ of Missouri-Kansas City
    ## 2006                     Philosophy             PHD 2011 Princeton University
    ## 2007                          Dance         BS 2014 Univ of Wisconsin-Madison
    ## 2008                     Law School         JD 2014 Univ of Wisconsin-Madison
    ## 2009         General Administration        PHD 2017 Univ of Wisconsin-Madison
    ## 2010       African Cultural Studies     PHD 1991 Univ of California San Diego
    ## 2011                         Botany        PHD 2006 Michigan State University
    ## 2012                       Pharmacy    PHARMD 2017 Univ of Colorado at Denver
    ## 2013                      Neurology          MBBS 1987 Guntur Medical College
    ## 2014                      Economics                  PHD 2016 Yale University
    ## 2015                    Social Work          PHD 2002 Northwestern University
    ## 2016 Civil Society And Comm Studies         MS 1992 Univ of Wisconsin-Madison
    ## 2017  Ed Leadership&Policy Analysis    PHD 2011 Univ of Michigan at Ann Arbor
    ## 2018  Cell And Regenerative Biology          PHD 2012 Southwestern University
    ## 2019                     Law School         JD 1995 Univ of Wisconsin-Madison
    ## 2020                   Bacteriology            PHD 2015 Washington University
    ## 2021                       Oncology            PHD 2015 Washington University
    ## 2022                       Medicine         MD 1967 Univ of Wisconsin-Madison
    ## 2023          Counseling Psychology                  MA 2012 Edgewood College
    ## 2024     Population Health Sciences         PHD 2005 Johns Hopkins University
    ## 2025                    Mathematics       MA 1991 Univ of California Berkeley
    ## 2026     Electrical & Computer Engr             PHD Univ of Wisconsin-Madison
    ## 2027     Curriculum And Instruction      PHD 2015 Univ of Wisconsin-Milwaukee
    ## 2028          Ft Mba Program Office                MS 2016 Harvard University
    ## 2029   Wisconsin School Of Business        PHD 2009 Univ of Wisconsin-Madison
    ## 2030           Medical Microbiology             PHD 2005 Princeton University
    ## 2031        German, Nordic & Slavic              PHD 2001 Stanford University
    ## 2032  Communication Sci & Disorders                  MS 1994 McDaniel College
    ## 2033      Industrial & Systems Engr         MS 1998 Univ of Wisconsin-Madison
    ## 2034              Surgical Sciences              DVM 2006 Universitat Leipzig
    ## 2035  Biostatistics&Med Informatics        PHD 2016 Univ Of NC At Chapel Hill
    ## 2036       African Cultural Studies        PHD 2020 Univ of Wisconsin-Madison
    ## 2037     Chemical & Biological Engr       PHD 2004 Carnegie-Mellon University
    ## 2038                      Astronomy               PHD 1999 Indiana University
    ## 2039                     Geoscience          PHD 2011 Oregon State University
    ## 2040      Planning & Landscape Arch        PHD 1992 Oklahoma State University
    ## 2041             Communication Arts        PHD 1994 Univ of Wisconsin-Madison
    ## 2042  Ophthalmology&Visual Sciences        PHD 1987 Univ of Wisconsin-Madison
    ## 2043                       Pharmacy     PHARMD 2009 Univ of Wisconsin-Madison
    ## 2044                    Mathematics    PHD 1991 Univ of Minnesota-Twin Cities
    ## 2045                      Geography      PHD 2006 Univ of California Berkeley
    ## 2046         Educational Psychology        PHD 2003 Univ of Wisconsin-Madison
    ## 2047               Medical Sciences                  PHD 1990 Mayo Foundation
    ## 2048                       Pharmacy              PHD 1998 Stanford University
    ## 2049                     Psychology         PHD 1990 Arizona State University
    ## 2050 Atmospheric & Oceanic Sciences        PHD 2011 Colorado State University
    ## 2051               Medical Sciences      DVM 2005 Universidad de Buenos Aires
    ## 2052              Political Science        PHD 1983 Univ of Wisconsin-Madison
    ## 2053                        Finance       MS 2004 Univ of Wisconsin-La Crosse
    ## 2054                     Entomology         MS 2020 Univ of Wisconsin-Madison
    ## 2055                    Art History                  PHD 1998 Yale University
    ## 2056   Wisconsin School Of Business     PHD 2009 Univ of California Riverside
    ## 2057                    Mathematics             PHD 2010 Princeton University
    ## 2058                      Chemistry       PHD 2015 Massachusetts Inst Of Tech
    ## 2059                    Art History   PHD 1993 Clg of William & Mary-Virginia
    ## 2060                       Pharmacy        PHD 2006 Univ of Wisconsin-Madison
    ## 2061               Student Services         MS 2004 Univ of Wisconsin-Madison
    ## 2062 Ms In Biotechnology Degree Prg         MA 2009 Univ of Wisconsin-Madison
    ## 2063          Counseling Psychology        EDD 2009 Univ of Wisconsin-Madison
    ## 2064 Atmospheric & Oceanic Sciences         PHD 1992 University of Washington
    ## 2065            Integrative Biology         MS 2007 Univ of Wisconsin-Madison
    ## 2066              Political Science               PHD 1989 Harvard University
    ## 2067                   Biochemistry               PHD 1974 Harvard University
    ## 2068     Electrical & Computer Engr        PHD 2016 Univ of Wisconsin-Madison
    ## 2069               Medical Sciences                                  PHD 2016
    ## 2070     Bolz Center For Arts Admin        MBA 2005 Univ of Wisconsin-Madison
    ## 2071       Pathobiological Sciences        PHD 1995 Univ Of Minnesota-St Paul
    ## 2072                    Kinesiology          PHD 2001 Simon Fraser University
    ## 2073                      Geography        PHD 1995 Univ of Wisconsin-Madison
    ## 2074                     Philosophy            PHD 2008 University of Arizona
    ## 2075                      Sociology    PHD 2006 Univ of Minnesota-Twin Cities
    ## 2076                       Genetics     PHD 1985 Fac Des Sci Agro DE Gembloux
    ## 2077         Biomedical Engineering                  PHD 2001 Rice University
    ## 2078                            Art        PHD 2013 Univ of Wisconsin-Madison
    ## 2079                      Astronomy      PHD 1983 Univ of California Berkeley
    ## 2080             Accting & Info Sys   PHD 1984 University of British Columbia
    ## 2081         Educational Psychology            PHD 2010 Vanderbilt University
    ## 2082                    Social Work        MSW 2014 Univ of Wisconsin-Madison
    ## 2083          Counseling Psychology      EDM 2018 Univ of Wisconsin-La Crosse
    ## 2084            Integrative Biology        PHD 2014 Univ of Wisconsin-Madison
    ## 2085                  Naval Science    MS 2015 Univ of California Los Angeles
    ## 2086                            Art        MFA 2017 Univ of Wisconsin-Madison
    ## 2087     Chemical & Biological Engr    PHD 1994 Univ of Michigan at Ann Arbor
    ## 2088     Electrical & Computer Engr   PHD 1987 Univ of IL at Urbana-Champaign
    ## 2089                    Mathematics       PHD 2005 University of Pennsylvania
    ## 2090              Political Science                  PHD 1988 Yale University
    ## 2091       Law, Society And Justice       JD 1991 Chicago-Kent College Of Law
    ## 2092             Accting & Info Sys            PHD 1997 University of Arizona
    ## 2093                      Sociology    PHD 1979 U of California-Santa Barbara
    ## 2094              Surgical Sciences        PHD 1994 Univ of Wisconsin-Madison
    ## 2095                        Physics        PHD 1971 Univ of Wisconsin-Madison
    ## 2096                      Chemistry        PHD 1991 Univ of Wisconsin-Madison
    ## 2097             Information School       MA 1998 Univ of Wisconsin-Milwaukee
    ## 2098  Journalism&Mass Communication    PHD 1989 Univ of Minnesota-Twin Cities
    ## 2099                          Dance        MFA 1989 Univ of Wisconsin-Madison
    ## 2100      Planning & Landscape Arch      PHD 2009 Univ of California Berkeley
    ## 2101                        English        MFA 2010 Univ of Wisconsin-Madison
    ## 2102                     Law School                JD 2003 University of Iowa
    ## 2103 Lafollette Sch Of Publ Affairs          MA 2018 Johns Hopkins University
    ## 2104   Office Of Undergrad Advising      MS 1991 Southern IL Univ.-Carbondale
    ## 2105                Volunteer Staff      PHD 2011 Univ of Southern California
    ## 2106         Biomedical Engineering               PHD 2009 Harvard University
    ## 2107  Operations & Information Mgmt                PHD 1993 Purdue University
    ## 2108                  Africa Center        PHD 2016 Univ of Wisconsin-Madison
    ## 2109                        History                  PHD 1977 Yale University
    ## 2110                  Asian Studies          PHD 2005 Northwestern University
    ## 2111                       Medicine        MD 2010 Case Western Reserve Univ.
    ## 2112                     Pediatrics       MD 2001 Thomas Jefferson University
    ## 2113                         Botany               PHD 2004 University of Utah
    ## 2114    Mead Witter School Of Music               MM University of Washington
    ## 2115                    Kinesiology          PHD 1988 Northwestern University
    ## 2116                     Law School       JD 2000 Univ of California Berkeley
    ## 2117                        Physics      PHD 2002 Univ of California Berkeley
    ## 2118                        History              PHD 1988 Columbia University
    ## 2119  Ed Leadership&Policy Analysis         JD 2020 Univ of Wisconsin-Madison
    ## 2120     Curriculum And Instruction            PHD 2018 University of Chicago
    ## 2121 Ms In Biotechnology Degree Prg                    MBA University of Iowa
    ## 2122  Ophthalmology&Visual Sciences                    PHD University of Iowa
    ## 2123                   Anthropology                                  PHD 2011
    ## 2124  Journalism&Mass Communication             PHD 2017 Princeton University
    ## 2125  Engr Professional Development    PHD 2000 University of Texas at Austin
    ## 2126                        Nursing        DNP 2012 Univ of Wisconsin-Madison
    ## 2127        School Of Human Ecology         EDD 2010 Univ of Minnesota-Duluth
    ## 2128                      Economics   PHD 2005 Univ of California Los Angeles
    ## 2129  Classic & Ancient Near E Stds          PHD 1978 University of Cambridge
    ## 2130     Curriculum And Instruction      PHD 2011 Univ of California Berkeley
    ## 2131             Communication Arts         PHD 2008 Arizona State University
    ## 2132                       Medicine            MD 1983 Wayne State University
    ## 2133              Surgical Sciences             PHD 2000 University of London
    ## 2134                 Administration         BA 2011 Univ of Wisconsin-Madison
    ## 2135     Civil & Environmental Engr      PHD 2002 Univ of California Berkeley
    ## 2136                      Chemistry   PHD 1985 Univ of California Los Angeles
    ## 2137       Gender And Women Studies                   PHD New York University
    ## 2138                      Radiology        PHD 2007 Univ of Wisconsin-Madison
    ## 2139                        Nursing      DNP 2018 Univ of Illinois at Chicago
    ## 2140                     Law School         JD 1993 Univ of Wisconsin-Madison
    ## 2141                       Medicine            PHD 1992 University of Chicago
    ## 2142  Ed Leadership&Policy Analysis          PHD 2017 Northwestern University
    ## 2143  Ed Leadership&Policy Analysis        PHD 1994 Univ of Wisconsin-Madison
    ## 2144                       Medicine         MD 2002 Univ of Wisconsin-Madison
    ## 2145                       Pharmacy     PHD 1996 California Institute of Tech
    ## 2146         Spanish And Portuguese     PHD 1990 Univ of California San Diego
    ## 2147              Academic Programs        PHD 2015 Univ of Wisconsin-Madison
    ## 2148           Neurological Surgery       MD 1999 Univ of Illinois at Chicago
    ## 2149           Medical Microbiology               PHD 2004 Harvard University
    ## 2150                    Social Work        MSW 2007 Univ of Wisconsin-Madison
    ## 2151    Life Sciences Communication        PHD 1977 Univ of Wisconsin-Madison
    ## 2152                      Geography     MS 2011 Minnesota State Univ, Mankato
    ## 2153                        Finance             PHD 1987 University of London
    ## 2154        German, Nordic & Slavic        PHD 1999 Univ of Wisconsin-Madison
    ## 2155  Biostatistics&Med Informatics              PHD 2002 Columbia University
    ## 2156                     Statistics                                   MS 2011
    ## 2157             French And Italian            PHD 1994 University of Toronto
    ## 2158       Gender And Women Studies         PHD 2014 University of Washington
    ## 2159         Spanish And Portuguese                PHD 2006 Boston University
    ## 2160                    Mathematics                                       PHD
    ## 2161                       Medicine    PHD 2008 Univ of Michigan at Ann Arbor
    ## 2162                       Oncology              PHD 1975 Stanford University
    ## 2163                     Philosophy          PHD 2011 University of San Diego
    ## 2164                    Social Work        MSW 2007 Univ of Wisconsin-Madison
    ## 2165   Management & Human Resources              PHD University of Pittsburgh
    ## 2166                    Social Work        PHD 1990 Univ of Wisconsin-Madison
    ## 2167                    Mathematics        PHD 1988 Univ of Wisconsin-Madison
    ## 2168         Educational Psychology           PSYD 2018 University of Arizona
    ## 2169                   Biochemistry        PHD 2007 Univ of Wisconsin-Madison
    ## 2170                Medical Physics     PHD 1996 Medical College Of Wisconsin
    ## 2171                 Design Studies             MS 1987 University Of Houston
    ## 2172                       Pharmacy            PHD 2005 University of Arizona
    ## 2173                     Geoscience          PHD 2003 Northwestern University
    ## 2174                     Law School      JD 2000 Hastings Clg of Law, U of CA
    ## 2175          Cals Academic Affairs  MHEA 2002 Univ of IL at Urbana-Champaign
    ## 2176 Lafollette Sch Of Publ Affairs            MPP 1995 University of Chicago
    ## 2177                        History              PHD 1998 Stanford University
    ## 2178      Industrial & Systems Engr   PHD 2012 Univ Studi di Roma-La Sapienza
    ## 2179             Bba Program Office         MS 2017 Univ of Wisconsin-Madison
    ## 2180              Academic Programs        PHD 1976 Univ of Wisconsin-Madison
    ## 2181        German, Nordic & Slavic      PHD 2013 Univ of California Berkeley
    ## 2182        German, Nordic & Slavic        PHD 1996 Univ of Wisconsin-Madison
    ## 2183             French And Italian      PHD 1988 Universite Paris X Nanterre
    ## 2184         Mechanical Engineering         MS 1999 Univ of Wisconsin-Madison
    ## 2185     Electrical & Computer Engr     PHD 1981 California Institute of Tech
    ## 2186                      Chemistry        PHD 2017 Univ of Wisconsin-Madison
    ## 2187     Electrical & Computer Engr         PHD 2007 Arizona State University
    ## 2188      Animal And Dairy Sciences        PHD 1976 Univ of Wisconsin-Madison
    ## 2189              Computer Sciences      PHD 1984 Univ of California Berkeley
    ## 2190                            Art        MFA 1995 Univ of Wisconsin-Madison
    ## 2191                    Social Work    MSW 1996 Univ of Michigan at Ann Arbor
    ## 2192         Mechanical Engineering       PHD 2005 Massachusetts Inst Of Tech
    ## 2193     Chemical & Biological Engr       PHD 1995 Carnegie-Mellon University
    ## 2194  Engr Professional Development        MS 1984 Carnegie-Mellon University
    ## 2195                    Mathematics               PHD 2002 Cornell University
    ## 2196              Academic Programs         BS 1986 Univ of Wisconsin-Madison
    ## 2197              Surgical Sciences        DVM 1983 Michigan State University
    ## 2198  Ed Leadership&Policy Analysis               PHD 2005 University of Utah
    ## 2199                Theatre & Drama       MFA 2013 Carnegie-Mellon University
    ## 2200 Lafollette Sch Of Publ Affairs               PHD 2017 Cornell University
    ## 2201         Mechanical Engineering      PHD 2001 Univ of California Berkeley
    ## 2202             Communication Arts      PHD 2020 Univ of Southern California
    ## 2203                Family Medicine     MD 2012 Univ of Massachusetts Med Sch
    ## 2204      Industrial & Systems Engr           PHD Univ of California Berkeley
    ## 2205                      Geography          PHD 2017 Northwestern University
    ## 2206     Asian Languages & Cultures        PHD 2017 Univ of Wisconsin-Madison
    ## 2207                     Law School             JD 1987 Vanderbilt University
    ## 2208         Educational Psychology        PHD 2016 Univ of Wisconsin-Madison
    ## 2209                     Law School         JD 2003 Univ of Wisconsin-Madison
    ## 2210                       Medicine     PHD 2002 Univ of Missouri-Kansas City
    ## 2211                     Law School         JD 2010 Univ of Wisconsin-Madison
    ## 2212                            Art    MFA 2008 Univ of Maryland College Park
    ## 2213 Agricultural&Applied Economics    PHD 1999 Iowa State Univ of Sci & Tech
    ## 2214             Information School                  MLS 2002 SUNY at Buffalo
    ## 2215                        History        PHD 1988 Univ of Wisconsin-Madison
    ## 2216                       Oncology      PHD 1990 Univ of California Berkeley
    ## 2217                  Asian Amer St              JD 1989 Marquette University
    ## 2218      Forest & Wildlife Ecology        PHD 1985 Univ of Wisconsin-Madison
    ## 2219              Political Science        PHD 2015 Univ of Wisconsin-Madison
    ## 2220        German, Nordic & Slavic    PHD 1992 Al Ludwig U-Freiburg Breisgau
    ## 2221     Educational Policy Studies      PHD 2012 Univ of California Berkeley
    ## 2222                       Medicine            MD 1992 University of Khartoum
    ## 2223                        Physics                PHD 2011 Shiraz University
    ## 2224                     Pediatrics               PHD 2012 University of Iowa
    ## 2225    Mead Witter School Of Music               PHD 2014 Harvard University
    ## 2226  Rehab Psychology & Special Ed        PHD 2014 Univ of Wisconsin-Madison
    ## 2227                      Economics                  PHD 2016 Yale University
    ## 2228               Medical Sciences    PHD 1985 Univ of Minnesota-Twin Cities
    ## 2229            Integrative Biology       MS 2004 Univ of Wisconsin-Milwaukee
    ## 2230                     Law School              JD 1988 University of Oregon
    ## 2231                        English        MFA 2018 Univ of Wisconsin-Madison
    ## 2232             Accting & Info Sys       MACC 2020 Univ of Wisconsin-Madison
    ## 2233                        Nursing      PHD 2013 Univ of Wisconsin-Milwaukee
    ## 2234 Atmospheric & Oceanic Sciences        MPA 2002 Univ of Wisconsin-Madison
    ## 2235     Department Of Neuroscience              PHD 2010 University Of Miami
    ## 2236                    Social Work        MSW 2012 Univ of Wisconsin-Madison
    ## 2237                      Geography           PHD 2006 University of Kentucky
    ## 2238      Planning & Landscape Arch          PHD 1993 Northwestern University
    ## 2239                      Marketing              PHD 1998 Columbia University
    ## 2240              Surgical Sciences               DVM 2006 Cornell University
    ## 2241      Planning & Landscape Arch        PHD 2004 Univ of Wisconsin-Madison
    ## 2242                     Pediatrics      MD 2000 George Washington University
    ## 2243                        Surgery        MD 2010 University of Pennsylvania
    ## 2244  Materials Science&Engineering      PHD 1998 Univ of California Berkeley
    ## 2245 Atmospheric & Oceanic Sciences       PHD 1994 Massachusetts Inst Of Tech
    ## 2246     Asian Languages & Cultures        PHD 1996 Univ of Wisconsin-Madison
    ## 2247                     Law School                JD 1979 Hofstra University
    ## 2248             Communication Arts                PHD 2010 McGill University
    ## 2249  Ed Leadership&Policy Analysis         JD 2006 Univ of Wisconsin-Madison
    ## 2250                 Human Oncology               PHD 2009 Harvard University
    ## 2251          Afro-American Studies           PHD Univ of Illinois at Chicago
    ## 2252     Electrical & Computer Engr          PHD 2003 Northwestern University
    ## 2253                 Human Oncology    PHD 1983 Univ of Michigan at Ann Arbor
    ## 2254                    Social Work   PHD 2003 Univ of California Los Angeles
    ## 2255         Biomolecular Chemistry                MD 1968 Harvard University
    ## 2256        School Of Human Ecology                  PHD 1999 Yale University
    ## 2257                       Pharmacy        PHD 1995 Univ of Wisconsin-Madison
    ## 2258       African Cultural Studies                PHD 2013 Purdue University
    ## 2259                        History         PHD 2019 University of Pittsburgh
    ## 2260              Surgical Sciences                                  PHD 2009
    ## 2261                        Nursing        PHD 2008 Univ of Wisconsin-Madison
    ## 2262  Rehab Psychology & Special Ed         PHD 2019 University of Washington
    ## 2263  Communication Sci & Disorders        PHD 2017 Univ of Wisconsin-Madison
    ## 2264              Surgical Sciences            PHD 1990 University of Bristol
    ## 2265               Risk & Insurance       PHD 2014 University of Pennsylvania
    ## 2266 Agricultural&Applied Economics               PHD 2015 Cornell University
    ## 2267                      Economics             PHD 2018 Princeton University
    ## 2268     Population Health Sciences           PHD 1985 University of Virginia
    ## 2269    Mead Witter School Of Music  MMED 2013 Univ of IL at Urbana-Champaign
    ## 2270 Liberal Arts & Applied Studies        PHD 2014 Univ of Wisconsin-Madison
    ## 2271                        English               PHD 1994 University of Iowa
    ## 2272                        Physics     PHD 2012 Univ Paris Sorbonne Paris IV
    ## 2273                      Economics    PHD 1989 Univ of Minnesota-Twin Cities
    ## 2274              Surgical Sciences        DVM 2007 Univ of Missouri-Columbia
    ## 2275       Law, Society And Justice                   PHD 2016 Ireland (Eire)
    ## 2276     Curriculum And Instruction                 MTECH 2002 Lesley College
    ## 2277            Engineering Physics         MS 1992 Univ of Wisconsin-Madison
    ## 2278  Engr Professional Development         ME 2010 Univ of Wisconsin-Madison
    ## 2279     Chemical & Biological Engr       PHD 1989 Massachusetts Inst Of Tech
    ## 2280         Biomedical Engineering    PHD 2002 Univ of Michigan at Ann Arbor
    ## 2281                    Social Work        MSW 2008 Univ of Wisconsin-Madison
    ## 2282               Consumer Science    EDD 2006 Univ of Minnesota-Twin Cities
    ## 2283                        History            PHD 2007 University of Chicago
    ## 2284       African Cultural Studies         MA 1981 Univ of Wisconsin-Madison
    ## 2285              Computer Sciences       PHD 2009 Carnegie-Mellon University
    ## 2286         Lat Amer Carib Iber St       PHD 2007 Pittsburg State University
    ## 2287      Planning & Landscape Arch           PHD 2003 Heriot-Watt University
    ## 2288     Population Health Sciences            PHD 2016 University of Chicago
    ## 2289 Ctr For Rus East Eur Cent Asia                        MA 2002 Kazan Univ
    ## 2290                     Psychiatry         MD 2011 Univ of Wisconsin-Madison
    ## 2291      Forest & Wildlife Ecology         MS 2002 Univ of Wisconsin-Madison
    ## 2292                     Pediatrics         MD 2009 Univ of Wisconsin-Madison
    ## 2293                     Philosophy              PHD 1986 Columbia University
    ## 2294  Engr Professional Development                                       PHD
    ## 2295                        Urology           MD 1988 University Of Rochester
    ## 2296     Asian Languages & Cultures               PHD 2011 University of Iowa
    ## 2297                   Religious St        PHD 2018 Univ of Wisconsin-Madison
    ## 2298                     Geoscience        PHD 2020 Univ of Wisconsin-Madison
    ## 2299                            Art         MA 2005 Universidade de Sao Paulo
    ## 2300         Educational Psychology      PHD 1991 Univ of Colorado at Boulder
    ## 2301                      Chemistry               PHD 1985 Harvard University
    ## 2302                      Geography            PHD 1997 University of Florida
    ## 2303                     Pediatrics    MD 2005 Univ of IL at Urbana-Champaign
    ## 2304          Counseling Psychology     MA 1998 State U of New York at Albany
    ## 2305 Ctr For Rus East Eur Cent Asia   PHD 1992 Kazakh State U of World Langs.
    ## 2306                    Social Work        MSW 2013 Univ of Wisconsin-Madison
    ## 2307         Mechanical Engineering               PHD 1998 University of Iowa
    ## 2308         Mechanical Engineering       PHD 1997 Massachusetts Inst Of Tech
    ## 2309          Academic Partnerships            PHD 1981 University of Chicago
    ## 2310  Classic & Ancient Near E Stds    PHD 2008 University of Texas at Austin
    ## 2311     Educational Policy Studies                 PHD 1998 Brown University
    ## 2312  Ed Leadership&Policy Analysis        PHD 2017 Univ of Wisconsin-Madison
    ## 2313    Mead Witter School Of Music              DMA 2007 SUNY At Stony Brook
    ## 2314 Lafollette Sch Of Publ Affairs        PHD 2013 Univ of Wisconsin-Madison
    ## 2315                Family Medicine                  DPT 2007 Duke University
    ## 2316    Life Sciences Communication              BA 1989 Marquette University
    ## 2317 Biological Systems Engineering         MS 1995 Univ of Wisconsin-Madison
    ## 2318                    Art History                  PHD 2013 Yale University
    ## 2319     Civil & Environmental Engr         MS 1976 Univ of Wisconsin-Madison
    ## 2320  Dept Of Med History&Bioethics               PHD 2011 Cornell University
    ## 2321       Gender And Women Studies        PHD 2010 Univ of Wisconsin-Madison
    ## 2322   Management & Human Resources                  MS 2017 Edgewood College
    ## 2323 Lafollette Sch Of Publ Affairs      PHD 2007 Univ of California Berkeley
    ## 2324                   Anthropology            PHD 1994 University of Chicago
    ## 2325                        English         MS 2012 Univ of Wisconsin-Madison
    ## 2326                       Medicine             PHD Univ of Wisconsin-Madison
    ## 2327                        Nursing   MSN 2014 Concordia University Wisconsin
    ## 2328  Ophthalmology&Visual Sciences        PHD 2004 University of New Orleans
    ## 2329         Spanish And Portuguese        PHD 2008 Univ of Wisconsin-Madison
    ## 2330                        History             PHD 1998 Princeton University
    ## 2331                      Marketing   PHD 1972 Univ of IL at Urbana-Champaign
    ## 2332               Medical Sciences        DVM 2003 Univ of Wisconsin-Madison
    ## 2333    Life Sciences Communication              PHD 2016 American University
    ## 2334            Integrative Biology      PHD 2010 Univ of Colorado at Boulder
    ## 2335                        Nursing        DNP 2012 Univ of Wisconsin-Madison
    ## 2336  Biostatistics&Med Informatics         PHD 1991 University of Washington
    ## 2337           Nutritional Sciences         PHD 1986 Univ of California Davis
    ## 2338                        English            PHD 1998 Univ de Strasbourg II
    ## 2339                    Social Work      MSW 1999 Washington State University
    ## 2340              Computer Sciences        PHD 2005 University of Connecticut
    ## 2341                        English    MFA 2012 Univ of Michigan at Ann Arbor
    ## 2342             Information School               PHD 2016 Indiana University
    ## 2343               Medical Sciences         DVM 2008 Univ of California Davis
    ## 2344     Curriculum And Instruction        EDD 2015 Univ Of NC At Chapel Hill
    ## 2345  Ophthalmology&Visual Sciences            PHD 1987 University of Calgary
    ## 2346          Counseling Psychology              MS Univ of Wisconsin-Madison
    ## 2347                     Psychology    PHD 1987 Univ of Michigan at Ann Arbor
    ## 2348                   Horticulture        PHD 1982 Univ of Wisconsin-Madison
    ## 2349                     Law School               SJD 2015 Harvard University
    ## 2350            Engineering Physics        PHD 2010 Univ of Wisconsin-Madison
    ## 2351         Biomedical Engineering        PHD 2009 Univ of Wisconsin-Madison
    ## 2352                       Is Major         MA 2006 Univ of Wisconsin-Madison
    ## 2353        School Of Human Ecology            PHD 1999 Vanderbilt University
    ## 2354  Communication Sci & Disorders               PHD 2010 Harvard University
    ## 2355                      Sociology   PHD 2007 Univ of California Los Angeles
    ## 2356     Civil & Environmental Engr   PHD 1995 Univ of IL at Urbana-Champaign
    ## 2357                        Nursing        DNP 2015 Univ of Wisconsin-Madison
    ## 2358                   Religious St               THD 1994 Harvard University
    ## 2359                        English         MA 2000 Univ of Wisconsin-Madison
    ## 2360                        Nursing        DNP 2020 Univ of Wisconsin-Madison
    ## 2361            Engineering Physics     PHD 2013 California Institute of Tech
    ## 2362     Electrical & Computer Engr        PHD 1995 Univ of Wisconsin-Madison
    ## 2363     Civil & Environmental Engr           PHD 1999 Texas A & M University
    ## 2364                   Biochemistry         PHD 1985 Johns Hopkins University
    ## 2365                        English         MA 2006 Univ of Wisconsin-Madison
    ## 2366                        History       PHD 1986 University of Pennsylvania
    ## 2367               Consumer Science                 BBA 1979 Drake University
    ## 2368            Integrative Biology          MS 1982 University of Cincinnati
    ## 2369         Mechanical Engineering        PHD 2001 Univ of Wisconsin-Madison
    ## 2370                        Nursing         PHD 1985 University of Washington
    ## 2371         Mechanical Engineering         MS 2005 Univ of Wisconsin-Madison
    ## 2372             Accting & Info Sys        PHD 2017 Univ of Wisconsin-Madison
    ## 2373                        Nursing               PHD 2019 Capella University
    ## 2374  Ed Leadership&Policy Analysis        PHD 2010 Univ of Wisconsin-Madison
    ## 2375                     Pediatrics             MD 2006 Ohio State University
    ## 2376                       Medicine             MD 2000 Georgetown University
    ## 2377  Pathology&Laboratory Medicine        PHD 2001 Univ of Wisconsin-Madison
    ## 2378  Pathology&Laboratory Medicine        PHD 2004 Univ of Wisconsin-Madison
    ## 2379                   Bacteriology         BA 2016 Univ of Wisconsin-Madison
    ## 2380 Atmospheric & Oceanic Sciences        PHD 2019 Univ of Wisconsin-Madison
    ## 2381                        Surgery               MD 1987 New York University
    ## 2382    Mead Witter School Of Music    DMA 2019 Univ of Michigan at Ann Arbor
    ## 2383               Medical Sciences            DVM 1981 Ohio State University
    ## 2384     Electrical & Computer Engr            PHD Carnegie-Mellon University
    ## 2385                      Marketing    PHD 1982 University of Texas at Austin
    ## 2386                      Sociology               PHD 2018 Harvard University
    ## 2387             Information School        PHD 2010 Univ Of NC At Chapel Hill
    ## 2388      Planning & Landscape Arch         JD 1986 Univ of Wisconsin-Madison
    ## 2389                     Law School               SJD 2001 Harvard University
    ## 2390                       Medicine    PHD 2009 Univ of Alabama at Birmingham
    ## 2391                     Law School            JD 1996 University Of Richmond
    ## 2392                      Geography            PHD 1996 University of Bristol
    ## 2393                     Law School                   JD 2014 Yale University
    ## 2394     Civil & Environmental Engr         MS 1978 Univ of Wisconsin-Madison
    ## 2395               Consumer Science     MSSW 1991 Univ of Wisconsin-Milwaukee
    ## 2396                      Sociology        PHD 1977 Univ Of NC At Chapel Hill
    ## 2397     Population Health Sciences        PHD 1990 Univ Of NC At Chapel Hill
    ## 2398               Medical Sciences             PHD 2014 University of Guelph
    ## 2399               Academic Affairs               PHD 1992 Cornell University
    ## 2400                        English   PHD 2010 Univ of IL at Urbana-Champaign
    ## 2401                Volunteer Staff         MD 1982 Univ of Wisconsin-Madison
    ## 2402                    Social Work     PHD 2009 Louisiana State U & A&M Colg
    ## 2403     Curriculum And Instruction        PHD 2005 Michigan State University
    ## 2404          Cals Academic Affairs         BS 2005 Univ Of Minnesota-St Paul
    ## 2405        Weinert Center For Entr               MBA 1992 Harvard University
    ## 2406                        Physics                  PHD 1984 Rice University
    ## 2407        Obstetrics & Gynecology        PHD 2007 Univ of Wisconsin-Madison
    ## 2408                   Horticulture         MS 2004 Univ of Wisconsin-Madison
    ## 2409                        Finance                   PHD Stanford University
    ## 2410                        Surgery         MD 2002 Univ of Wisconsin-Madison
    ## 2411      Animal And Dairy Sciences    MS 1997 University of Nebraska-Lincoln
    ## 2412                     Law School         JD 1993 Univ of Wisconsin-Madison
    ## 2413            Integrative Biology    PHD 2004 Iowa State Univ of Sci & Tech
    ## 2414                        English              PHD 2002 Columbia University
    ## 2415  Communication Sci & Disorders     MA 1983 University Of Central Florida
    ## 2416       Pathobiological Sciences        PHD 1996 Univ of Wisconsin-Madison
    ## 2417        German, Nordic & Slavic    PHD 2005 Russian State U of Humanities
    ## 2418                     Law School              PHD 1990 Stanford University
    ## 2419         Mechanical Engineering   PHD 1987 Univ of IL at Urbana-Champaign
    ## 2420                         Botany       PHD 1996 Univ. Nacional de La Plata
    ## 2421                        Nursing                 DNP 2016 Edgewood College
    ## 2422  Engr Professional Development         MS 1995 North Carolina State Univ
    ## 2423                     Pediatrics     PHD 1995 Eberhard Karls Univ Tubingen
    ## 2424                        Nursing          MSN 2016 Grand Canyon University
    ## 2425     Population Health Sciences         PHD 2015 Georgia State University
    ## 2426  Operations & Information Mgmt        PHD 2000 Univ of Wisconsin-Madison
    ## 2427     Curriculum And Instruction        PHD 2018 Univ of Wisconsin-Madison
    ## 2428              Political Science            PHD 2008 Washington University
    ## 2429  Ed Leadership&Policy Analysis        EDD 2007 Univ of Wisconsin-Madison
    ## 2430      Forest & Wildlife Ecology                PHD 2004 Boston University
    ## 2431                      Economics      PHD 2009 Univ of Colorado at Boulder
    ## 2432                    Social Work                   PHD Columbia University
    ## 2433     Curriculum And Instruction   PHD 2005 Univ of California Los Angeles
    ## 2434                            Art         MFA 2017 Univ of California Davis
    ## 2435  Biostatistics&Med Informatics   PHD 1993 Univ of IL at Urbana-Champaign
    ## 2436                    Social Work        MSW 2006 Univ of Wisconsin-Madison
    ## 2437                   Biochemistry     PHD 2005 Univ of California San Diego
    ## 2438                        Finance        PHD 2000 Univ of Wisconsin-Madison
    ## 2439   Grainger Institute For Engr.     MS 1997 Univ of Michigan at Ann Arbor
    ## 2440     Chemical & Biological Engr       PHD 1998 Massachusetts Inst Of Tech
    ## 2441                        Physics            PHD 2009 Ohio State University
    ## 2442                   Biochemistry        PHD 1975 Univ of Wisconsin-Madison
    ## 2443                            Art                    MFA University of Iowa
    ## 2444  Journalism&Mass Communication    PHD 2014 U of California-Santa Barbara
    ## 2445                        Finance              MBA 2004 Columbia University
    ## 2446             Information School              PHD 1990 Syracuse University
    ## 2447                   Horticulture        PHD 1976 Univ Of Minnesota-St Paul
    ## 2448         Mechanical Engineering                 PHD 2010 Brown University
    ## 2449               Medical Sciences       PHD 2010 University of Pennsylvania
    ## 2450 Biological Systems Engineering              PHD 1999 Hokkaido University
    ## 2451                        Physics        PHD 1991 Univ of Wisconsin-Madison
    ## 2452             Communication Arts        PHD 1990 Univ of Wisconsin-Madison
    ## 2453  Classic & Ancient Near E Stds      PHD 2011 Univ of California Berkeley
    ## 2454               Military Science         BA 2008 Univ of Wisconsin-Oshkosh
    ## 2455                       Medicine         MD 2000 Univ of Wisconsin-Madison
    ## 2456     Electrical & Computer Engr    PHD 2014 University of Texas at Austin
    ## 2457           Biotechnology Center              PHD 1985 Columbia University
    ## 2458        School Of Human Ecology         PHD 2005 University of Notre Dame
    ## 2459                      Sociology   PHD 2016 New School for General Studies
    ## 2460                Family Medicine       MPAS 2015 Univ of Wisconsin-Madison
    ## 2461  Operations & Information Mgmt        MBA 2009 Univ of Wisconsin-Madison
    ## 2462     Civil & Environmental Engr      PHD 1985 Univ of Newcastle upon Tyne
    ## 2463 Agricultural&Applied Economics    PHD 2009 U of California-Santa Barbara
    ## 2464                        Physics             PHD 2014 Princeton University
    ## 2465                   Food Science    PHD 1983 Univ of Massachusetts Amherst
    ## 2466           Nutritional Sciences    PHD 2008 Univ of Alabama at Birmingham
    ## 2467     Civil & Environmental Engr    PHD 2000 Univ of Michigan at Ann Arbor
    ## 2468  Communication Sci & Disorders      PHD 2014 Univ of Southern California
    ## 2469      Animal And Dairy Sciences               PHD 1983 Cornell University
    ## 2470                     Entomology            PHD 1987 University of Georgia
    ## 2471        Obstetrics & Gynecology          PHD 1998 Old Dominion University
    ## 2472                       Pharmacy                 PHD University of Florida
    ## 2473              Computer Sciences        PHD 1998 Univ of Wisconsin-Madison
    ## 2474                     Statistics            PHD 2017 University of Chicago
    ## 2475    Mead Witter School Of Music         BS 2000 Univ of Wisconsin-Madison
    ## 2476                     Pediatrics              PHD 1999 University of Delhi
    ## 2477                    Kinesiology         EDM 1983 Johns Hopkins University
    ## 2478              Academic Programs          MD 1994 Johns Hopkins University
    ## 2479                    Mathematics             PHD 2000 Princeton University
    ## 2480                      Economics         PHD 2015 Johns Hopkins University
    ## 2481  Ed Leadership&Policy Analysis             EDD 2007 Roosevelt University
    ## 2482      Forest & Wildlife Ecology            PHD 2010 University of Wyoming
    ## 2483      Planning & Landscape Arch        PHD 2004 Rutgers State Univ-Newark
    ## 2484                   Bacteriology        PHD 1989 Univ of Wisconsin-Madison
    ## 2485                        Nursing    MS 2013 Concordia University Wisconsin
    ## 2486                        Nursing        PHD 2011 Univ of Wisconsin-Madison
    ## 2487                       Genetics            PHD 2003 University of Arizona
    ## 2488                      Chemistry        PHD 2006 Univ of Wisconsin-Madison
    ## 2489                 Anesthesiology           PHD 1985 University of Virginia
    ## 2490                    Social Work        MSW 2003 Univ of Wisconsin-Madison
    ## 2491                        Nursing        PHD 2016 Univ of Wisconsin-Madison
    ## 2492            Air Force Aerospace           PHD 2013 Texas A & M University
    ## 2493                      Marketing    PHD 1999 Univ of Minnesota-Twin Cities
    ## 2494                   Soil Science   PHD 2001 Univ of California Los Angeles
    ## 2495                      Sociology               PHD 2000 University of Iowa
    ## 2496                     Pediatrics         MD 2011 Univ of Wisconsin-Madison
    ## 2497  Ed Leadership&Policy Analysis     EDD 2018 George Washington University
    ## 2498               Medical Sciences               PHD 1998 Cornell University
    ## 2499      Forest & Wildlife Ecology      PHD 2004 Univ of California Berkeley
    ## 2500                       Medicine      PHD 2010 Universidad de La Republica
    ## 2501                       Genetics       PHD 1994 Massachusetts Inst Of Tech
    ## 2502         Spanish And Portuguese      PHD 2005 Univ of California Berkeley
    ## 2503             Accting & Info Sys              JD 2003 Villanova University
    ## 2504               Medical Sciences        DVM 2011 Univ of Wisconsin-Madison
    ## 2505      Animal And Dairy Sciences        PHD 2014 Univ of Wisconsin-Madison
    ## 2506                     Law School    PHD 2006 East China Univ of Poli & Law
    ## 2507  Communication Sci & Disorders   PHD 2014 University of Nebraska-Lincoln
    ## 2508                   Biochemistry           PHD 2005 Texas A & M University
    ## 2509     Population Health Sciences        PHD 1999 Univ of Wisconsin-Madison
    ## 2510                       Medicine    MD 1999 Queen's University at Kingston
    ## 2511  Materials Science&Engineering       PHD 1973 Carnegie-Mellon University
    ## 2512                        English         MA 2000 Univ of Wisconsin-Madison
    ## 2513                       Genetics      PHD 1996 University of New Hampshire
    ## 2514    Mead Witter School Of Music                   MM 1990 Julliard School
    ## 2515  Communication Sci & Disorders    MS 2000 Univ of Wisconsin-StevensPoint
    ## 2516          Counseling Psychology        EDD 2019 Univ of Wisconsin-Madison
    ## 2517               Risk & Insurance         BS 1988 Univ of Wisconsin-Oshkosh
    ## 2518  Pathology&Laboratory Medicine        PHD 1981 Rutgers State Univ-Newark
    ## 2519                       Pharmacy        PHD 2012 Univ of Wisconsin-Madison
    ## 2520                     Geoscience            PHD 2003 University of Chicago
    ## 2521                     Pediatrics         MD 2004 Univ of Wisconsin-Madison
    ## 2522                     Law School         JD 1991 University of the Pacific
    ## 2523                            Art        PHD 1993 Univ of Wisconsin-Madison
    ## 2524                Theatre & Drama        PHD 2016 Univ of Wisconsin-Madison
    ## 2525 Atmospheric & Oceanic Sciences        PHD 2017 Univ of Wisconsin-Madison
    ## 2526                     Pediatrics         MD 1986 Univ of Wisconsin-Madison
    ## 2527 Atmospheric & Oceanic Sciences         PHD 1990 University of Washington
    ## 2528              Political Science            PHD 2000 Ohio State University
    ## 2529        Biology Core Curriculum        PHD 2009 Univ of Wisconsin-Madison
    ## 2530         Mechanical Engineering                PHD 2002 Purdue University
    ## 2531     Chemical & Biological Engr      PHD 2005 Univ of California Berkeley
    ## 2532                     Psychology        PHD 2019 Univ of Wisconsin-Madison
    ## 2533         Mechanical Engineering             PHD 1984 University of Oregon
    ## 2534 Agricultural&Applied Economics    PHD 1997 Iowa State Univ of Sci & Tech
    ## 2535          Counseling Psychology        EDM 2019 Univ of Wisconsin-Madison
    ## 2536       Gender And Women Studies                   MA 2013 Simmons College
    ## 2537                Volunteer Staff         MD 2014 Univ of Wisconsin-Madison
    ## 2538                    Art History      PHD 1992 Univ of California Berkeley
    ## 2539                     Law School         JD 2010 Univ of Wisconsin-Madison
    ## 2540             French And Italian   PHD 1999 Univ of California Los Angeles
    ## 2541                       Agronomy    PHD 2008 Iowa State Univ of Sci & Tech
    ## 2542               Medical Sciences   DVM 2016 Univ of IL at Urbana-Champaign
    ## 2543                   Anthropology        PHD 1999 Univ of Wisconsin-Madison
    ## 2544                        Finance         MS 1987 Univ of Wisconsin-Madison
    ## 2545                    Kinesiology    PHD 2010 Univ of Minnesota-Twin Cities
    ## 2546      Forest & Wildlife Ecology        PHD 2000 Univ of Wisconsin-Madison
    ## 2547  Journalism&Mass Communication         MA 1992 Univ of Wisconsin-Madison
    ## 2548 Atmospheric & Oceanic Sciences        PHD 1988 Univ of Wisconsin-Madison
    ## 2549                     Law School         JD 1992 Univ of Wisconsin-Madison
    ## 2550                   Biochemistry            PHD 1979 University of Arizona
    ## 2551                      Sociology              PHD 1962 Stanford University
    ## 2552     Population Health Sciences    MD 2001 Nrtheastrn OH Univs Clg Of Med
    ## 2553  Biostatistics&Med Informatics        PHD 2016 Univ of Wisconsin-Madison
    ## 2554                            Art             MFA Univ of Wisconsin-Madison
    ## 2555     Civil & Environmental Engr    PHD 1992 University of Texas at Austin
    ## 2556                        Nursing              MS 1979 Marquette University
    ## 2557       Pathobiological Sciences    DVM 1993 Iowa State Univ of Sci & Tech
    ## 2558  Real Estate & Urgan Land Econ         MS 1990 Univ of Wisconsin-Madison
    ## 2559                    Social Work       MSSW 1995 Univ of Wisconsin-Madison
    ## 2560         Information Technology         MS 1983 Univ of Wisconsin-Madison
    ## 2561                     Psychiatry         MD 2004 Univ Of NC At Chapel Hill
    ## 2562                        Finance             PHD Univ of Wisconsin-Madison
    ## 2563                        English         MFA 2003 Florida State University
    ## 2564                        History               PHD 1981 Cornell University
    ## 2565  Engr Professional Development        PHD 2006 Univ of Wisconsin-Madison
    ## 2566                     Law School                JD 2018 Quinnipiac College
    ## 2567        School Of Human Ecology              PHD 1995 Syracuse University
    ## 2568                            Art   BFA 2014 Bowling Green State University
    ## 2569                        Nursing             PHD 2010 Marquette University
    ## 2570                     Psychology          PHD 1997 University Of Rochester
    ## 2571                      Marketing               PHD 2010 Cornell University
    ## 2572                    Mathematics     PHD 1995 California Institute of Tech
    ## 2573    Mead Witter School Of Music         DMA University of Texas at Austin
    ## 2574  Cell And Regenerative Biology    PHD 2003 IN Univ-Purdue U-Indianapolis
    ## 2575        School Of Human Ecology     PHD 2010 Univ of California San Diego
    ## 2576                       Genetics               PHD 2006 Cornell University
    ## 2577                        Surgery                 PHD 2004 Brown University
    ## 2578     Curriculum And Instruction              EDD 1970 New York University
    ## 2579     Department Of Neuroscience        PHD 1996 Univ of Wisconsin-Madison
    ## 2580                       Pharmacy     PHARMD 2006 Univ of Wisconsin-Madison
    ## 2581                      Economics       PHD 1996 Massachusetts Inst Of Tech
    ## 2582                       Pharmacy     PHARMD 2014 Univ of Wisconsin-Madison
    ## 2583   Management & Human Resources       PHD 2005 University of Pennsylvania
    ## 2584     Educational Policy Studies      PHD 2009 Univ of California Berkeley
    ## 2585                     Psychology       PHD 1997 Massachusetts Inst Of Tech
    ## 2586  Ophthalmology&Visual Sciences                MD 2001 University of Iowa
    ## 2587     Civil & Environmental Engr         PHD 1976 Johns Hopkins University
    ## 2588                        English     MA 1997 Univ of Minnesota-Twin Cities
    ## 2589               Medical Sciences        PHD 2012 Univ of Wisconsin-Madison
    ## 2590              Political Science               PHD 2009 Harvard University
    ## 2591                     Law School               JD 2007 Stanford University
    ## 2592               Medical Sciences        DVM 2017 Univ of Wisconsin-Madison
    ## 2593     Civil & Environmental Engr    PHD 2013 Univ of Michigan at Ann Arbor
    ## 2594                      Radiology              PHD 2001 Stanford University
    ## 2595             Communication Arts    PHD 2016 Univ of Minnesota-Twin Cities
    ## 2596               Academic Affairs                  MS 2010 Edgewood College
    ## 2597      Forest & Wildlife Ecology      PHD 2015 Univ of Colorado at Boulder
    ## 2598  Engr Professional Development         MS 2003 Univ of Wisconsin-Madison
    ## 2599                    Social Work        MSW 2008 Univ of Wisconsin-Madison
    ## 2600  Engr Professional Development     MS 1997 Rose-Hulman Inst of Technolgy
    ## 2601                         Botany                  PHD 2001 Duke University
    ## 2602               Medical Sciences       DVM 2011 University of Pennsylvania
    ## 2603                       Genetics                  PHD 1994 Yale University
    ## 2604                   Biochemistry         PHD 2009 University of Washington
    ## 2605 Agricultural&Applied Economics         PHD 1991 Univ of California Davis
    ## 2606                    Art History               PHD 2009 Harvard University
    ## 2607                            Art             MFA Univ of Wisconsin-Madison
    ## 2608         Biomedical Engineering        PHD 2010 Univ of Wisconsin-Madison
    ## 2609         Biomedical Engineering        PHD 2009 Univ of Wisconsin-Madison
    ## 2610                       Medicine         PHD 1993 Univ Cat del Sacro Cuore
    ## 2611     Civil & Environmental Engr                                       PHD
    ## 2612         Spanish And Portuguese        PHD 2007 Univ of Wisconsin-Madison
    ## 2613             Emergency Medicine      MD 2005 Loyola University of Chicago
    ## 2614                       Medicine          PHD 2012 Northwestern University
    ## 2615                Plant Pathology        PHD 2017 Univ of Wisconsin-Madison
    ## 2616                    Kinesiology         MS 2014 Univ of Wisconsin-Madison
    ## 2617         Educational Psychology             PHD 1996 University of Sussex
    ## 2618    Mead Witter School Of Music          MM 1973 Indiana State University
    ## 2619                        English           PHD 1998 University of Delaware
    ## 2620         Educational Psychology          PHD 2013 Northwestern University
    ## 2621                       Pharmacy                 PHD Washington University
    ## 2622         Mechanical Engineering         PHD Univ of Michigan at Ann Arbor
    ## 2623     Civil & Environmental Engr                                       PHD
    ## 2624     Civil & Environmental Engr             MA 1978 University of Florida
    ## 2625                Family Medicine        PHD 2012 Univ of Wisconsin-Madison
    ## 2626    Mead Witter School Of Music           MM 2017 Northwestern University
    ## 2627          Counseling Psychology             MA 2015 Ball State University
    ## 2628                     Geoscience     PHD 2018 California Institute of Tech
    ## 2629  Communication Sci & Disorders                MA 1983 University of Iowa
    ## 2630                      Economics              PHD 2007 Stanford University
    ## 2631          Counseling Psychology         PHD 1989 University of Notre Dame
    ## 2632                        Finance    PHD 2000 Univ of Minnesota-Twin Cities
    ## 2633                     Law School               SJD 2004 Harvard University
    ## 2634  Real Estate & Urgan Land Econ         MS 2004 Univ of Wisconsin-Madison
    ## 2635               Medical Sciences        DVM 2015 Univ Of Minnesota-St Paul
    ## 2636         Educational Psychology        PHD 1998 Univ of Wisconsin-Madison
    ## 2637      Forest & Wildlife Ecology        PHD 1998 Univ of Wisconsin-Madison
    ## 2638      Industrial & Systems Engr    PHD 1986 Univ of Michigan at Ann Arbor
    ## 2639 Engineering Student Developmnt             BA 1990 Upper Iowa University
    ## 2640       Pathobiological Sciences        DVM 2017 Michigan State University
    ## 2641  Pathology&Laboratory Medicine                MD 1989 University of Iowa
    ## 2642 Ctr For Rus East Eur Cent Asia           MSED 2015 Kent State University
    ## 2643                        English           PHD 1999 University of Delaware
    ## 2644        School Of Human Ecology             MD 1991 Washington University
    ## 2645                Plant Pathology    PHD 2007 Iowa State Univ of Sci & Tech
    ## 2646                     Pediatrics     MD 1997 SUNY Health Sci Cntr-Brooklyn
    ## 2647                   Biochemistry      PHD 2009 Washington State University
    ## 2648     Electrical & Computer Engr    PHD 1989 Univ of Michigan at Ann Arbor
    ## 2649     Curriculum And Instruction        EDM 2016 Univ of Wisconsin-Madison
    ## 2650                        History    PHD 2015 U of California-Santa Barbara
    ## 2651          Counseling Psychology        PHD 2019 Univ of Wisconsin-Madison
    ## 2652                Family Medicine             PHD Univ of Wisconsin-Madison
    ## 2653                          Dance              MFA 2011 New York University
    ## 2654     Civil & Environmental Engr      PHD 1993 Univ of Illinois at Chicago
    ## 2655    South Asian Sum Lang Instit                                        BS
    ## 2656                Medical Physics        PHD 1993 Univ of Wisconsin-Madison
    ## 2657  Pathology&Laboratory Medicine    PHD 1994 Univ of Minnesota-Twin Cities
    ## 2658 Lafollette Sch Of Publ Affairs             MA 1989 IOWA STATE UNIVERSITY
    ## 2659                   Food Science          PHD 1995 Oregon State University
    ## 2660                        English         MA 2005 Univ of Wisconsin-Madison
    ## 2661         Spanish And Portuguese         PHD 2007 Univ of California Davis
    ## 2662                     Statistics        PHD 2017 Michigan State University
    ## 2663                     Statistics      PHD 2012 Univ of California Berkeley
    ## 2664              Surgical Sciences           DVM 2015 Texas A & M University
    ## 2665                        History              PHD 2003 Brandeis University
    ## 2666                         Botany        PHD 1988 Univ of Wisconsin-Madison
    ## 2667         Educational Psychology       PHD 2013 Carnegie-Mellon University
    ## 2668                       Medicine     MD 1996 University of Western Ontario
    ## 2669                   Biochemistry             PHD 1975 University of Durham
    ## 2670                     Psychiatry         MD 2006 Univ of Wisconsin-Madison
    ## 2671                        Physics       PHD 1999 Massachusetts Inst Of Tech
    ## 2672                        Physics               PHD 2004 Indiana University
    ## 2673      Animal And Dairy Sciences        PHD 2014 Universidade de Sao Paulo
    ## 2674          Counseling Psychology                PHD 2004 Boston University
    ## 2675                      Chemistry     PHD 1967 Univ of California San Diego
    ## 2676                    Amer Ind St         BA 1999 Univ of Wisconsin-Madison
    ## 2677                        Surgery     MD 2006 Univ Of Maryland At Baltimore
    ## 2678     Chemical & Biological Engr     PHD 2005 Univ of California San Diego
    ## 2679      Animal And Dairy Sciences               PHD 1983 Cornell University
    ## 2680                      Radiology         PHD 1999 Johns Hopkins University
    ## 2681     Educational Policy Studies        PHD 1980 Univ of Wisconsin-Madison
    ## 2682                Theatre & Drama         MFA University of Texas at Austin
    ## 2683         Mechanical Engineering        PHD 1992 Univ of Wisconsin-Madison
    ## 2684 Biological Systems Engineering               PHD 1987 Cornell University
    ## 2685                        Nursing   DNP 2014 Concordia University Wisconsin
    ## 2686                     Psychology             PHD 1996 University of Kansas
    ## 2687                     Pediatrics         MS 1980 Univ of Wisconsin-Madison
    ## 2688              Computer Sciences    PHD 2015 Univ of Maryland College Park
    ## 2689                          Dance            MFA 2011 Ohio State University
    ## 2690     Population Health Sciences         MD 1981 Univ of Wisconsin-Madison
    ## 2691                    Mathematics       PHD 2020 Carnegie-Mellon University
    ## 2692     Civil & Environmental Engr           PHD Univ of California Berkeley
    ## 2693              Computer Sciences     PHD 2014 Univ Denis Diderot Paris VII
    ## 2694              Political Science               PHD 2012 Harvard University
    ## 2695                       Agronomy         PHD 2002 Univ of California Davis
    ## 2696              Computer Sciences               PHD 1982 Cornell University
    ## 2697           Neurological Surgery        MD 1991 University of Pennsylvania
    ## 2698                   Bacteriology               PHD 2006 University of Iowa
    ## 2699       Pathobiological Sciences            PHD 1999 University of Florida
    ## 2700        German, Nordic & Slavic             PHD 1998 University of Oxford
    ## 2701       Pathobiological Sciences        PHD 2006 Univ of Wisconsin-Madison
    ## 2702             Information School     PHD 2020 Rutgers St Unv-New Brunswick
    ## 2703  Materials Science&Engineering         PHD 2016 Florida State University
    ## 2704                     Pediatrics         MD 2000 Univ of Wisconsin-Madison
    ## 2705                       Medicine      MD 2004 Univ of Nebraska Medical Ctr
    ## 2706    Mead Witter School Of Music        PHD 2004 Univ of Wisconsin-Madison
    ## 2707                            Art             MFA Univ of Wisconsin-Madison
    ## 2708      Animal And Dairy Sciences     PHD 2000 Univ of Massachusetts Boston
    ## 2709     Bolz Center For Arts Admin        MFA 2015 Univ of Wisconsin-Madison
    ## 2710                       Pharmacy                                  PHD 2010
    ## 2711                     Law School               JD 1979 Columbia University
    ## 2712                      Economics         MA 1990 Univ of Wisconsin-Madison
    ## 2713      Animal And Dairy Sciences        PHD 1989 Univ of Wisconsin-Madison
    ## 2714                        Urology        PHD 2000 Univ of Missouri-Columbia
    ## 2715      Forest & Wildlife Ecology          PHD 2000 Oregon State University
    ## 2716  Real Estate & Urgan Land Econ        PHD 1991 Univ of Wisconsin-Madison
    ## 2717  Journalism&Mass Communication    PHD 2007 U of California-Santa Barbara
    ## 2718             Information School      PHD 1980 Univ of California Berkeley
    ## 2719     Asian Languages & Cultures                  PHD 2005 Yale University
    ## 2720                   Religious St        PHD 2002 Univ Of NC At Chapel Hill
    ## 2721                   Biochemistry       PHD 1999 Massachusetts Inst Of Tech
    ## 2722              Surgical Sciences        DMV 2018 Univ of Wisconsin-Madison
    ## 2723               Academic Affairs     MMS 2006 Univ of Nebraska Medical Ctr
    ## 2724                Family Medicine          MD 2000 Johns Hopkins University
    ## 2725              Political Science         PHD 2006 University of Pittsburgh
    ## 2726                            Art         MFA University of Texas at Austin
    ## 2727                Volunteer Staff         MFA 1995 University of Pittsburgh
    ## 2728  Community & Environ Sociology    PHD 2018 U of California-Santa Barbara
    ## 2729                Plant Pathology        PHD 2014 Univ of Wisconsin-Madison
    ## 2730      Forest & Wildlife Ecology      PHD 2008 Univ of California Berkeley
    ## 2731            Integrative Biology   PHD 1997 Bowling Green State University
    ## 2732     Electrical & Computer Engr   PHD 2016 Eidgenossische Tec Hoch Zurich
    ## 2733                        Finance   PHD 2014 Univ Commerciale Luigi Bocconi
    ## 2734        School Of Human Ecology        PHD 2007 Univ of Missouri-Columbia
    ## 2735              Academic Programs                 PHD 1996 Clark University
    ## 2736                    Social Work    PHD 1996 Univ of Michigan at Ann Arbor
    ## 2737               Medical Sciences         DVM 2005 Univ of California Davis
    ## 2738                        History             PHD 1990 Rhode Island College
    ## 2739                        Nursing        PHD 2012 Univ of Wisconsin-Madison
    ## 2740                      Wiscience        PHD 2010 Univ of Wisconsin-Madison
    ## 2741     Department Of Neuroscience            PHD 1986 Washington University
    ## 2742                      Geography        PHD 2004 Univ of Wisconsin-Madison
    ## 2743      Industrial & Systems Engr        PHD 1971 Univ of Wisconsin-Madison
    ## 2744  Journalism&Mass Communication                PHD 2006 Temple University
    ## 2745                    Mathematics      PHD 2007 Univ of California Berkeley
    ## 2746                        History             PHD 2016 University of Oxford
    ## 2747                     Pediatrics      MD 1983 Univ Of OK Health Sci Center
    ## 2748                   Religious St              PHD 2018 Columbia University
    ## 2749                     Geoscience    PHD 1990 Univ of MD-University College
    ## 2750               Academic Affairs       PHD 2013 Massachusetts Inst Of Tech
    ## 2751     Educational Policy Studies              PHD 2016 Columbia University
    ## 2752                    Mathematics      PHD 2014 Univ of California Berkeley
    ## 2753         Spanish And Portuguese      PHD 2006 Univ of Colorado at Boulder
    ## 2754         Mechanical Engineering         MS 2001 Univ of Wisconsin-Madison
    ## 2755         Biomedical Engineering            PHD 2006 University of Arizona
    ## 2756                      Sociology             PHD 1984 Princeton University
    ## 2757     Curriculum And Instruction     MEPD 2015 Univ of Wisconsin-La Crosse
    ## 2758                     Psychology       PHD 2000 Carnegie-Mellon University
    ## 2759                     Statistics      PHD 2011 Univ of California Berkeley
    ## 2760  Journalism&Mass Communication        PHD 2005 Univ of Wisconsin-Madison
    ## 2761         Mechanical Engineering        PHD 2008 Univ of Wisconsin-Madison
    ## 2762                   Bacteriology        PHD 1996 Univ of Wisconsin-Madison
    ## 2763     Curriculum And Instruction              PHD 2014 Stanford University
    ## 2764          Counseling Psychology    EDM 2017 Grand Valley State University
    ## 2765     Electrical & Computer Engr    PHD 2017 Univ of Maryland College Park
    ## 2766                   Biochemistry     PHD 2012 California Institute of Tech
    ## 2767                        Nursing                  MS 2008 Regis University
    ## 2768              Computer Sciences              PHD 1987 Tel Aviv University
    ## 2769                   Bacteriology        PHD 1995 Univ of Wisconsin-Madison
    ## 2770    Mead Witter School Of Music         MA 2010 SUNY Empire State College
    ## 2771      Animal And Dairy Sciences     MS 2013 VA Polytechnic Inst & State U
    ## 2772                        Surgery        MD 2008 Univ of Colorado at Denver
    ## 2773                    Mathematics      PHD 1988 Univ of California Berkeley
    ## 2774     Department Of Neuroscience             PHD 1997 University of London
    ## 2775        German, Nordic & Slavic         PHD 2018 University of Washington
    ## 2776     Chemical & Biological Engr    PHD 1984 Univ of Minnesota-Twin Cities
    ## 2777                    Social Work            PHD 2014 University of Chicago
    ## 2778      Animal And Dairy Sciences        PHD 1999 Universidade de Sao Paulo
    ## 2779             Information School            EDD 1999 University Of Houston
    ## 2780                Medical Physics        PHD 2014 Univ of Wisconsin-Madison
    ## 2781                       Pharmacy             PHARMD 2004 Butler University
    ## 2782  Pathology&Laboratory Medicine             MD 2003 Texas Tech University
    ## 2783                       Pharmacy        PHD 1996 Michigan State University
    ## 2784     Department Of Neuroscience            PHD 2009 University of Chicago
    ## 2785                            Art      MFA 1985 San Francisco Art Institute
    ## 2786               Risk & Insurance    PHD 1993 Univ of Michigan at Ann Arbor
    ## 2787              Ctr For Jewish St                 PHD 2008 Brown University
    ## 2788     Ctr For Relig&Global Citiz      PHD 2012 Ruprecht Karls U Heidelberg
    ## 2789                     Psychiatry        PHD 2008 Univ of Wisconsin-Madison
    ## 2790  Rehab Psychology & Special Ed        PHD 1993 Univ of Wisconsin-Madison
    ## 2791            Integrative Biology                  PHD 2017 Duke University
    ## 2792                       Oncology             MD 1969 Washington University
    ## 2793                      Economics                  PHD 2006 Yale University
    ## 2794 Orthopedics And Rehabilitation         PHD 2016 Univ of California Davis
    ## 2795                      Geography    PHD 2011 Pennsylvania State University
    ## 2796         Mechanical Engineering              PHD 2007 Stanford University
    ## 2797    Mead Witter School Of Music            PHD 2008 University Of Houston
    ## 2798                       Pharmacy     PHARMD 2007 Univ of Wisconsin-Madison
    ## 2799                Plant Pathology     PHD 1979 Pennsylvania State U-Hershey
    ## 2800 Atmospheric & Oceanic Sciences         PHD 2016 University of Washington
    ## 2801    Mead Witter School Of Music    MA 1978 U Rochester, Eastman Sch Music
    ## 2802                    Social Work       PHD 2009 University of Pennsylvania
    ## 2803  Biostatistics&Med Informatics         PHD 2009 University Of New Mexico
    ## 2804       African Cultural Studies      PHD 2014 Univ of California Berkeley
    ## 2805                   Soil Science                PHD 2006 Purdue University
    ## 2806             Information School        PHD 2006 Univ of Wisconsin-Madison
    ## 2807                            Art         MFA 1984 Arizona State University
    ## 2808                    Social Work    MSW 1991 Univ of Michigan at Ann Arbor
    ## 2809     Curriculum And Instruction        PHD 1999 Univ of Wisconsin-Madison
    ## 2810         Mechanical Engineering    PHD 2011 Univ of Michigan at Ann Arbor
    ## 2811         Mechanical Engineering                                  PHD 2013
    ## 2812  Ctr Study Upper Midwest Cultr        PHD 2014 Univ of Wisconsin-Madison
    ## 2813                      Economics    PHD 2004 Univ of Minnesota-Twin Cities
    ## 2814                       Medicine   PHD 2004 Australian National University
    ## 2815             French And Italian            PHD 1991 University of Toronto
    ## 2816 Biological Systems Engineering       PHD 1998 Georgia Inst of Technology
    ## 2817  Rehab Psychology & Special Ed   PHD 2011 Univ of IL at Urbana-Champaign
    ## 2818     Curriculum And Instruction    PHD 2006 Univ of Maryland College Park
    ## 2819     Civil & Environmental Engr                PHD 1988 Purdue University
    ## 2820                          Dance         BM 2004 Univ of Wisconsin-Madison
    ## 2821          Counseling Psychology                                  EDM 2018
    ## 2822 Agricultural&Applied Economics              PHD 1987 Stanford University
    ## 2823                     Psychology    PHD 1978 Pennsylvania State University
    ## 2824               Medical Sciences               DVM 1990 Uppsala University
    ## 2825                        Physics              PHD 1988 Stanford University
    ## 2826                     Psychology   PHD 2005 Australian National University
    ## 2827  Materials Science&Engineering            PHD 1980 Ohio State University
    ## 2828          Inst Reg Intl Studies         MA 2019 Univ of Wisconsin-Madison
    ## 2829                       Medicine        PHD 2009 Univ of Wisconsin-Madison
    ## 2830                        Physics      PHD 1994 Univ of Colorado at Boulder
    ## 2831                     Psychology          PHD 1997 University Of Rochester
    ## 2832              Surgical Sciences             DVM 2008 University of Guelph
    ## 2833                 Design Studies         MS 2001 Univ of Wisconsin-Madison
    ## 2834         Biomedical Engineering      PHD 2007 Univ of California Berkeley
    ## 2835              Computer Sciences   PHD 2016 Univ of California Los Angeles
    ## 2836                        Nursing   DNP 2013 Concordia University Wisconsin
    ## 2837  Pathology&Laboratory Medicine    PHD 1978 Univ of Michigan at Ann Arbor
    ## 2838       Pathobiological Sciences                                  PHD 2008
    ## 2839      Language Sciences Program    PHD 1984 University of Texas at Austin
    ## 2840             Information School        MLS 2005 Univ of Wisconsin-Madison
    ## 2841  Ed Leadership&Policy Analysis        PHD 2012 Univ of Wisconsin-Madison
    ## 2842        Comparative Biosciences          PHD 2006 Northwestern University
    ## 2843     Population Health Sciences         PHD 2013 University of Pittsburgh
    ## 2844              Surgical Sciences        PHD 2011 Univ of Wisconsin-Madison
    ## 2845         Spanish And Portuguese    PHD 2000 U of California-Santa Barbara
    ## 2846                       Medicine     MD 2000 Univ of Minnesota-Twin Cities
    ## 2847         Mechanical Engineering              PHD 2001 Stanford University
    ## 2848       Pathobiological Sciences       PHD 1993 University of Pennsylvania
    ## 2849                        Finance        BBA 1991 Univ of Wisconsin-Madison
    ## 2850         Biomedical Engineering                                        MA
    ## 2851  Pathology&Laboratory Medicine         PHD 1979 Eotvos Lorand University
    ## 2852          Cals Academic Affairs        PHD 2012 Univ of Wisconsin-Madison
    ## 2853              Computer Sciences    PHD 2006 University of Texas at Austin
    ## 2854                     Statistics              PHD 2018 Stanford University
    ## 2855     Electrical & Computer Engr            PHD 2017 University of Toronto
    ## 2856    Mead Witter School Of Music    DMA 2011 Univ of Michigan at Ann Arbor
    ## 2857     Civil & Environmental Engr                                  PHD 2017
    ## 2858         Spanish And Portuguese            PHD 1988 Vanderbilt University
    ## 2859   Management & Human Resources     PHD 2011 Univ of California San Diego
    ## 2860                        Physics        PHD 1988 Univ of Wisconsin-Madison
    ## 2861     Electrical & Computer Engr        PHD 1999 Univ of Wisconsin-Madison
    ## 2862        School Of Human Ecology    PHD 1986 VA Polytechnic Inst & State U
    ## 2863        School Of Human Ecology            PHD 2014 Irvine Valley College
    ## 2864          Counseling Psychology           MS Univ of Wisconsin-Whitewater
    ## 2865           Medical Microbiology    PHD 2006 Univ of Michigan at Ann Arbor
    ## 2866               Medical Sciences         DVM 2016 University of Queensland
    ## 2867                        English     MA 2009 Univ of Minnesota-Twin Cities
    ## 2868                Animal Sciences   PHD 1979 Univ of IL at Urbana-Champaign
    ## 2869              Surgical Sciences        DVM 1992 Univ of Wisconsin-Madison
    ## 2870       Gender And Women Studies               PHD 2014 Indiana University
    ## 2871                        Nursing    DNP 2010 Minnesota State Univ, Mankato
    ## 2872                     Law School              JD 2008 Marquette University
    ## 2873                        Nursing                 MSN 2015 Edgewood College
    ## 2874                        Nursing            MSN 2011 University of Phoenix
    ## 2875     Civil & Environmental Engr     PHD 1998 California Institute of Tech
    ## 2876                     Psychiatry    PHD 2014 State U of New York at Albany
    ## 2877 Agricultural&Applied Economics      PHD 2005 Univ of California Berkeley
    ## 2878                     Philosophy                  PHD 2011 Yale University
    ## 2879                      Geography         MS 2018 Univ of Wisconsin-Madison
    ## 2880                            Art      MFA 1982 San Francisco Art Institute
    ## 2881                       Pharmacy         BS 1982 Univ of Wisconsin-Madison
    ## 2882    Life Sciences Communication        PHD 1999 Univ of Wisconsin-Madison
    ## 2883                    Dermatology            MD 2001 Universitat Dusseldorf
    ## 2884  Engr Professional Development        PHD 1987 Univ of Wisconsin-Madison
    ## 2885                     Psychology      PHD 2011 Univ of California Berkeley
    ## 2886       Pathobiological Sciences        DVM 1992 Univ of Wisconsin-Madison
    ## 2887                      Chemistry        PHD 2006 Univ of Wisconsin-Madison
    ## 2888                        Physics        PHD 1987 Univ of Wisconsin-Madison
    ## 2889             Emergency Medicine          MD 2010 Johns Hopkins University
    ## 2890        German, Nordic & Slavic         PHD 1980 University of Copenhagen
    ## 2891 Agricultural&Applied Economics         MA 2016 Univ of Wisconsin-Madison
    ## 2892 Lafollette Sch Of Publ Affairs                                   BS 1985
    ## 2893               Risk & Insurance               PHD 1984 Indiana University
    ## 2894                    Social Work        MSW 2008 Univ of Wisconsin-Madison
    ## 2895 Lafollette Sch Of Publ Affairs   PHD 2015 New School for General Studies
    ## 2896                       Pharmacy    PHD 2018 Univ of Minnesota-Twin Cities
    ## 2897            Engineering Physics              PHD 2006 Germany, Fed Rep Of
    ## 2898  Classic & Ancient Near E Stds            PHD 2006 Fachhochschule Aachen
    ## 2899              Academic Programs                PHD 2005 Boston University
    ## 2900                        Surgery      MD 2004 Loyola University of Chicago
    ## 2901  Communication Sci & Disorders         MS 2000 Univ of Wisconsin-Madison
    ## 2902                     Law School                JD 1963 Harvard University
    ## 2903                      Chemistry        PHD 2006 Michigan State University
    ## 2904         Educational Psychology   PHD 2018 Univ of California Los Angeles
    ## 2905          Counseling Psychology      EDM 2016 Univ of Wisconsin-La Crosse
    ## 2906                     Entomology      PHD 2009 Univ of California Berkeley
    ## 2907                    Kinesiology        PHD 2001 Univ of Missouri-Columbia
    ## 2908     Chemical & Biological Engr                                       PHD
    ## 2909                       Genetics        PHD 2001 Univ of California Irvine
    ## 2910              Surgical Sciences        DVM 2006 Univ of Wisconsin-Madison
    ## 2911                        Finance                                        MS
    ## 2912                   Anthropology    PHD 1997 Pennsylvania State University
    ## 2913                    Social Work    PHD 2003 Univ of Michigan at Ann Arbor
    ## 2914               Academic Affairs                                  DPT 2010
    ## 2915      Planning & Landscape Arch               MLA 2011 Harvard University
    ## 2916           Nutritional Sciences               MS 2010 New York University
    ## 2917            Air Force Aerospace               MS Slippery Rock Univ Of PA
    ## 2918        German, Nordic & Slavic        PHD 1999 Univ of Wisconsin-Madison
    ## 2919                    Social Work        MSW 2008 Univ of Wisconsin-Madison
    ## 2920              Academic Programs         MS 2012 Univ of Wisconsin-Madison
    ## 2921             Communication Arts      MS 2011 Univ of Wisconsin-Whitewater
    ## 2922   Administration-Dean'S Office        DVM 2015 Univ of Wisconsin-Madison
    ## 2923               Medical Sciences        DVM 2008 Univ of Wisconsin-Madison
    ## 2924                     Law School         JD 2001 Univ of Wisconsin-Madison
    ## 2925                      Sociology   PHD 2006 Univ of California Los Angeles
    ## 2926                     Law School                   JD 1986 Yale University
    ## 2927                      Chemistry              PHD 1985 Columbia University
    ## 2928                        Nursing       MSN 2009 University of Pennsylvania
    ## 2929                    Kinesiology       BS 2011 Univ of Wisconsin-La Crosse
    ## 2930  Real Estate & Urgan Land Econ         MS 1989 Univ of Wisconsin-Madison
    ## 2931                        Surgery                MD 1995 Harvard University
    ## 2932              Political Science         PHD 2013 Univ of California Davis
    ## 2933              Academic Programs         MS 2006 Univ of Wisconsin-Madison
    ## 2934              Political Science               PHD 1999 Cornell University
    ## 2935     Curriculum And Instruction              PHD 1998 Stanford University
    ## 2936    Mead Witter School Of Music      PHD 1993 Univ of California Berkeley
    ## 2937  Journalism&Mass Communication               MFA 2007 Bennington College
    ## 2938                     Pediatrics         MD 2005 Univ of Wisconsin-Madison
    ## 2939                     Law School         MS 1999 Univ of Wisconsin-Madison
    ## 2940                    Mathematics        PHD 1985 Tech Hochschule Darmstadt
    ## 2941    Life Sciences Communication      BS 1974 Northern Illinois University
    ## 2942 Ms In Biotechnology Degree Prg    MBA 2003 Univ of Minnesota-Twin Cities
    ## 2943          Counseling Psychology              MS Univ of Wisconsin-Oshkosh
    ## 2944                       Medicine           MD 1992 Northwestern University
    ## 2945  Communication Sci & Disorders         MS 2005 Univ of Wisconsin-Madison
    ## 2946                     Psychology              PHD 1980 Columbia University
    ## 2947                      Sociology      PHD 1990 Univ of California Berkeley
    ## 2948                     Law School                JD 2007 Harvard University
    ## 2949                        Nursing              MS 2001 Marquette University
    ## 2950                        Nursing            MSN 2007 University of Phoenix
    ## 2951                     Pediatrics            MD 2010 University of Virginia
    ## 2952                      Chemistry        PHD 2001 Univ of Wisconsin-Madison
    ## 2953             Information School               PHD 2011 Cornell University
    ## 2954         Mechanical Engineering        PHD 2000 Univ of Wisconsin-Madison
    ## 2955                   Biochemistry                  PHD 2001 Yale University
    ## 2956                        Finance       PHD 2015 University of Pennsylvania
    ## 2957                    Mathematics    PHD 1991 Univ of Minnesota-Twin Cities
    ## 2958                       Pharmacy               PHD 2017 Harvard University
    ## 2959                      Economics          PHD 2000 University Of Rochester
    ## 2960   Management & Human Resources        PHD 2000 London Sch Econ& Poli Sci
    ## 2961                       Medicine        PHD 2003 Univ of Wisconsin-Madison
    ## 2962                    Dermatology               PHD 1985 Osmania University
    ## 2963     Electrical & Computer Engr               PHD 1987 Cornell University
    ## 2964     Population Health Sciences         PHD 2003 Johns Hopkins University
    ## 2965     Electrical & Computer Engr    PHD 2015 Univ of Minnesota-Twin Cities
    ## 2966                          Dance                    MFA 2009 Mills College
    ## 2967                       Pharmacy     PHARMD 2002 Univ of Wisconsin-Madison
    ## 2968                     Philosophy            PHD 1992 University of Arizona
    ## 2969         Educational Psychology    PHD 1998 Harvard Univ Extension School
    ## 2970  Journalism&Mass Communication        PHD 1998 Univ Of Minnesota-St Paul
    ## 2971  Journalism&Mass Communication               PHD 1987 Indiana University
    ## 2972             Emergency Medicine           MD 1996 University Of Rochester
    ## 2973       Gender And Women Studies            PHD 2013 University Of Houston
    ## 2974                        Finance                  PHD 2009 Duke University
    ## 2975                    Mathematics               PHD 2017 Harvard University
    ## 2976      Animal And Dairy Sciences        PHD 2006 Univ of Wisconsin-Madison
    ## 2977                        History      MA 2006 Univ of Tennessee, Knoxville
    ## 2978                     Statistics        PHD 1987 Univ of Wisconsin-Madison
    ## 2979             Information School         MA 1991 Univ of Wisconsin-Madison
    ## 2980                     Philosophy       PHD 1992 University of Pennsylvania
    ## 2981  Engr Professional Development         MA 2003 Univ of Wisconsin-Madison
    ## 2982         Mechanical Engineering               PHD 1991 Cornell University
    ## 2983                     Law School             PHD 2006 Princeton University
    ## 2984       Pathobiological Sciences             DVM 2012 University of Guelph
    ## 2985            Integrative Biology               PHD 2012 Harvard University
    ## 2986                       Genetics            PHD 2014 University of Toronto
    ## 2987          Afro-American Studies    PHD 2004 Univ of Michigan at Ann Arbor
    ## 2988    Life Sciences Communication        PHD 2000 Univ of Wisconsin-Madison
    ## 2989       Pathobiological Sciences        DVM 2007 Michigan State University
    ## 2990              Surgical Sciences            DVM 2011 University of Glasgow
    ## 2991                    Mathematics        PHD 2012 Natl Tech Univ of Ukraine
    ## 2992                     Law School               JD 1985 University Of Miami
    ## 2993        German, Nordic & Slavic             PHD Univ of Wisconsin-Madison
    ## 2994                       Medicine         MD 1985 Univ of Missouri-Columbia
    ## 2995               Medical Sciences        DVM 2016 Univ of Wisconsin-Madison
    ## 2996         Biomolecular Chemistry        PHD 1989 Univ of Wisconsin-Madison
    ## 2997  Ophthalmology&Visual Sciences        PHD 1989 Univ of Nebraska at Omaha
    ## 2998                       Medicine                   PHD Columbia University
    ## 2999              Political Science      PHD 2005 Univ of California Berkeley
    ## 3000                    Social Work        MSW 2016 Univ of Wisconsin-Madison
    ## 3001                    Mathematics             PHD 2013 Princeton University
    ## 3002                       Medicine    MD 1973 Hebrew University of Jerusalem
    ## 3003 Ms In Biotechnology Degree Prg            PHD 1998 Washington University
    ## 3004                 Design Studies   MFA 2006 California State U- Long Beach
    ## 3005                       Oncology                  PHD 2006 Yale University
    ## 3006                        English               PHD 2000 Cornell University
    ## 3007        German, Nordic & Slavic              PHD 1998 Stanford University
    ## 3008 Agricultural&Applied Economics      PHD 2005 Univ of California Berkeley
    ## 3009      Industrial & Systems Engr               PHD 1992 Harvard University
    ## 3010               Risk & Insurance        PHD 2009 Univ of Wisconsin-Madison
    ## 3011                      Economics                  PHD 2010 Yale University
    ## 3012                    Kinesiology        PHD 2015 Univ of Wisconsin-Madison
    ## 3013      Language Sciences Program        PHD 2009 Univ of Wisconsin-Madison
    ## 3014   Management & Human Resources       PHD 2014 University of Pennsylvania
    ## 3015        School Of Human Ecology      PHD 2007 Univ of Wisconsin-Milwaukee
    ## 3016 Biological Systems Engineering        PHD 1985 Univ of Wisconsin-Madison
    ## 3017        School Of Human Ecology   PHD 2020 Univ of IL at Urbana-Champaign
    ## 3018                        Physics               PHD 1998 Cornell University
    ## 3019                       Pharmacy               PHD 2009 University of Iowa
    ## 3020                        History      PHD 2001 Univ of California Berkeley
    ## 3021     Electrical & Computer Engr       PHD 1961 Carnegie-Mellon University
    ## 3022         Educational Psychology        PHD 2009 Univ of Wisconsin-Madison
    ## 3023                        English    MFA 1998 Univ of Michigan at Ann Arbor
    ## 3024             Communication Arts            PHD 2019 University of Chicago
    ## 3025                       Oncology        PHD 1984 Univ of Wisconsin-Madison
    ## 3026  Real Estate & Urgan Land Econ             JD 2007 Washington University
    ## 3027     Chemical & Biological Engr   PHD 1999 Univ of IL at Urbana-Champaign
    ## 3028 Biological Systems Engineering                PHD 1988 Purdue University
    ## 3029                     Psychology               PHD 2006 Harvard University
    ## 3030                      Chemistry      PHD 1983 Univ of Colorado at Boulder
    ## 3031                     Law School               JD 1985 Columbia University
    ## 3032                     Philosophy               PHD 1986 Cornell University
    ## 3033  Operations & Information Mgmt        PHD 2005 Univ Of NC At Chapel Hill
    ## 3034              Computer Sciences              PHD 2007 Stanford University
    ## 3035               Consumer Science         MS 1995 Univ of Wisconsin-Madison
    ## 3036      Industrial & Systems Engr        PHD 2018 Univ of Wisconsin-Madison
    ## 3037      Planning & Landscape Arch      PHD 1996 Michigan Technological Univ
    ## 3038          Counseling Psychology               MA 1993 Bucknell University
    ## 3039                Plant Pathology      PHD 2002 Washington State University
    ## 3040                   Biochemistry               PHD 2014 University of Utah
    ## 3041              Political Science            PHD 2012 University of Chicago
    ## 3042                   Horticulture        PHD 1977 Univ of Wisconsin-Madison
    ## 3043                            Art   MFA 1989 Sch Of The Art Inst Of Chicago
    ## 3044      Planning & Landscape Arch   PHD 2014 Univ of California Los Angeles
    ## 3045              Computer Sciences   PHD 2018 Univ of IL at Urbana-Champaign
    ## 3046                      Geography         MS 2018 Univ of Wisconsin-Madison
    ## 3047      Animal And Dairy Sciences    PHD 2002 Iowa State Univ of Sci & Tech
    ## 3048             Communication Arts              PHD 1996 New York University
    ## 3049                     Geoscience            PHD 1990 University of Wyoming
    ## 3050                     Pediatrics                MD 2002 Yeshiva University
    ## 3051  Biostatistics&Med Informatics                  PHD 2007 SUNY at Buffalo
    ## 3052     Department Of Neuroscience    PHD 2011 International Univ in Germany
    ## 3053         Biomedical Engineering                  PHD 2007 Duke University
    ## 3054  Engr Professional Development            MFA 2007 Ohio State University
    ## 3055                          Dance            MFA 2001 University of Arizona
    ## 3056                       Genetics        PHD 2000 Univ of Wisconsin-Madison
    ## 3057              Computer Sciences        PHD 2000 Univ of Wisconsin-Madison
    ## 3058                    Social Work            PHD 1999 University of Chicago
    ## 3059              Surgical Sciences        DVM 1993 Univ of Wisconsin-Madison
    ## 3060  Pathology&Laboratory Medicine        PHD 1987 Natl Tech Univ of Ukraine
    ## 3061                        Finance         PHD 2011 Florida State University
    ## 3062  Rehab Psychology & Special Ed        PHD 2005 Univ of Wisconsin-Madison
    ## 3063 Lafollette Sch Of Publ Affairs        PHD 1975 Univ of Wisconsin-Madison
    ## 3064                            Art                  MFA 2009 Yale University
    ## 3065      Industrial & Systems Engr             PHD Univ of Wisconsin-Madison
    ## 3066             Information School    MA 2012 Univ of California Los Angeles
    ## 3067                     Law School         JD 1983 Univ of Wisconsin-Madison
    ## 3068             Information School         PHD 2002 University of Pittsburgh
    ## 3069                        Nursing        MSN 2015 Univ of Wisconsin-Oshkosh
    ## 3070                Plant Pathology        PHD 2007 North Carolina State Univ
    ## 3071             Acad&Prg-Noncredit      MD 1979 Univ Of IL At Medical Center
    ## 3072                    Social Work      MSSW 1991 Univ of Texas at Arlington
    ## 3073  Engr Professional Development          MS 2012 Colorado School of Mines
    ## 3074                       Medicine         MD 1999 Univ of Wisconsin-Madison
    ## 3075             Communication Arts        PHD 1995 Univ of Wisconsin-Madison
    ## 3076                      Economics            PHD 1996 University of Chicago
    ## 3077                      Geography      PHD 2019 Univ of California Berkeley
    ## 3078                     Pediatrics            PHD 1997 University of Chicago
    ## 3079              Surgical Sciences      DVM 1989 Washington State University
    ## 3080                    Mathematics       PHD 1988 Massachusetts Inst Of Tech
    ## 3081                      Chemistry              PHD 1981 Stanford University
    ## 3082                      Economics            PHD 1991 University of Chicago
    ## 3083             Information School               MS 2010 Syracuse University
    ## 3084       Disease Prevention Admin    BS 1986 Univ of Wisconsin-StevensPoint
    ## 3085                   Food Science     MS 2009 Univ of Minnesota-Twin Cities
    ## 3086                    Mathematics    PHD 2016 Univ of Maryland College Park
    ## 3087               Medical Sciences        DVM 2016 Univ of Missouri-Columbia
    ## 3088                        Nursing           PHD 2014 U of Northern Colorado
    ## 3089 Division Of Continuing Studies             PHD 1996 Marquette University
    ## 3090                    Social Work        MSW 2012 Univ of Wisconsin-Madison
    ## 3091              Surgical Sciences            DVM 2004 Ohio State University
    ## 3092              Surgical Sciences        DVM 2016 Univ of Wisconsin-Madison
    ## 3093                            Art        MFA 2015 Univ of Wisconsin-Madison
    ## 3094                Family Medicine          PHD 1988 Medical College Of Ohio
    ## 3095                     Philosophy               PHD 1974 Harvard University
    ## 3096                    Mathematics           PHD 2020 Texas A & M University
    ## 3097                      Economics      PHD 2017 Univ of California Berkeley
    ## 3098              Computer Sciences   PHD 1985 Univ of IL at Urbana-Champaign
    ## 3099                   Soil Science               PHD 2006 Cornell University
    ## 3100                        Nursing       PHD 2000 Univ of Colorado at Denver
    ## 3101                Plant Pathology        PHD 2015 Univ of Wisconsin-Madison
    ## 3102        German, Nordic & Slavic        PHD 2007 Univ of Wisconsin-Madison
    ## 3103                     Pediatrics        PHD 1975 Univ of Wisconsin-Madison
    ## 3104     Civil & Environmental Engr              PHD 2012 Stanford University
    ## 3105              Ctr For Jewish St    MA 2002 Hebrew University of Jerusalem
    ## 3106                      Economics       PHD 1999 Massachusetts Inst Of Tech
    ## 3107                       Pharmacy               PHARMD 1975 SUNY at Buffalo
    ## 3108                    Mathematics              PHD 2008 University of Leeds
    ## 3109              Surgical Sciences           DVM 2002 Texas A & M University
    ## 3110                      Geography     MA 2012 University of Texas at Austin
    ## 3111                     Philosophy          PHD 2009 Northwestern University
    ## 3112            Engineering Physics        PHD 1995 Univ of Wisconsin-Madison
    ## 3113                    Mathematics              PHD 2008 New York University
    ## 3114                         Botany    PHD 1990 Pennsylvania State University
    ## 3115                    Art History                  PHD 2017 Yale University
    ## 3116               Academic Affairs             MTS 2002 Ave Maria University
    ## 3117                Medical Physics        PHD 2003 Univ of Wisconsin-Madison
    ## 3118                     Law School             JD 1992 University Of Houston
    ## 3119                        Physics      PHD 2014 Univ of Colorado at Boulder
    ## 3120                Theatre & Drama          MFA Univ of Arkansas-Little Rock
    ## 3121            Engineering Physics        PHD 2011 Univ of Wisconsin-Madison
    ## 3122  Ed Leadership&Policy Analysis        PHD 2007 Univ of Wisconsin-Madison
    ## 3123            Engineering Physics        PHD 1989 Univ of Wisconsin-Madison
    ## 3124  Cell And Regenerative Biology   PHD 2006 Univ of California Los Angeles
    ## 3125              Surgical Sciences                                  DVM 2016
    ## 3126         Spanish And Portuguese            PHD 2005 Georgetown University
    ## 3127                      Chemistry     PHD 1997 California Institute of Tech
    ## 3128   Management & Human Resources   PHD 1996 University of Nebraska-Lincoln
    ## 3129     Curriculum And Instruction                MA 1977 Harvard University
    ## 3130                   Anthropology            PHD 1996 University of Chicago
    ## 3131                    Kinesiology                PHD 2015 Boston University
    ## 3132        Obstetrics & Gynecology            PHD 2003 Vanderbilt University
    ## 3133                      Astronomy   PHD 2000 Univ of Western Sydney, Nepean
    ## 3134    Life Sciences Communication         MS 2000 Univ of Wisconsin-Madison
    ## 3135            Integrative Biology         PHD 1993 Arizona State University
    ## 3136                        History        PHD 2018 Univ of Wisconsin-Madison
    ## 3137    Comp Lit & Folklore Studies     PHD 1990 Univ Paris Sorbonne Paris IV
    ## 3138                        History                                  PHD 2017
    ## 3139                Theatre & Drama        MFA 2003 Univ of Wisconsin-Madison
    ## 3140                    Mathematics              PHD 2008 New York University
    ## 3141                        Nursing    PHD 2009 VA Polytechnic Inst & State U
    ## 3142                     Entomology      PHD 2009 Washington State University
    ## 3143                     Philosophy    PHD 2006 U of California-Santa Barbara
    ## 3144      Planning & Landscape Arch  B.ARCH 1981 Louisiana State U & A&M Colg
    ## 3145                Family Medicine        PHD 2016 Univ of Wisconsin-Madison
    ## 3146                      Radiology             MD 2004 Washington University
    ## 3147               Medical Sciences        DVM 2003 Univ of Wisconsin-Madison
    ## 3148  Communication Sci & Disorders             PHD 2009 University of Kansas
    ## 3149        German, Nordic & Slavic               PHD 2016 Harvard University
    ## 3150     Educational Policy Studies                PHD 2014 Tulane University
    ## 3151  Engr Professional Development        PHD 1974 Univ of Wisconsin-Madison
    ## 3152 Agricultural&Applied Economics      PHD 2017 Univ of California Berkeley
    ## 3153                     Law School         JD 2010 Univ of Wisconsin-Madison
    ## 3154                          Dance       BFA 1995 Texas Christian University
    ## 3155          Counseling Psychology              PHD 2016 American University
    ## 3156        Obstetrics & Gynecology             MD 1992 Ohio State University
    ## 3157 Agricultural&Applied Economics                PHD 1993 Purdue University
    ## 3158        Comparative Biosciences                                  PHD 2014
    ## 3159    Life Sciences Communication                  BA 1974 Drake University
    ## 3160                     Law School               JD 2005 American University
    ## 3161     Curriculum And Instruction        PHD 2006 Univ of Wisconsin-Madison
    ## 3162  Community & Environ Sociology    PHD 1988 Univ of Minnesota-Twin Cities
    ## 3163          Counseling Psychology          MS 2002 University of Louisville
    ## 3164                       Agronomy    PHD 1988 Univ of Minnesota-Twin Cities
    ## 3165                        History             PHD 2017 Princeton University
    ## 3166  Materials Science&Engineering               PHD 1984 Cornell University
    ## 3167                            Art      BFA 1982 Univ of Wisconsin-Milwaukee
    ## 3168                            Art             MFA Univ of Wisconsin-Madison
    ## 3169                    Mathematics      PHD 2009 Univ of California Berkeley
    ## 3170    Mead Witter School Of Music   PHD 1983 U Rochester, Eastman Sch Music
    ## 3171                      Chemistry      PHD 2016 Florida Inst. Of Technology
    ## 3172                     Psychiatry     MD 1988 Univ Of TX Med Branch-Galvest
    ## 3173 Biological Systems Engineering                  PHD 2006 Duke University
    ## 3174        German, Nordic & Slavic    MA 2008 Lviv National Univ Ivan Franko
    ## 3175     Electrical & Computer Engr                                        ME
    ## 3176                    Kinesiology        PHD 1994 Univ of Wisconsin-Madison
    ## 3177              Political Science      PHD 2004 Univ of California Berkeley
    ## 3178                    Mathematics             PHD 2007 Princeton University
    ## 3179  Dept Of Med History&Bioethics       PHD 1999 Massachusetts Inst Of Tech
    ## 3180                   Anthropology               PHD 1986 Harvard University
    ## 3181                       Medicine            PHD 1995 Washington University
    ## 3182     Educational Policy Studies        PHD 2018 Univ of Wisconsin-Madison
    ## 3183                        Nursing                  MSN 2004 Phoenix College
    ## 3184 Ms In Biotechnology Degree Prg        PHD 2000 Univ of Wisconsin-Madison
    ## 3185  Engr Professional Development                                       PHD
    ## 3186                    Social Work        PHD 2015 Univ of Wisconsin-Madison
    ## 3187                        Urology    MD 2005 Mt Sinai School of Med of CUNY
    ## 3188                        History    PHD 2020 Univ of Minnesota-Twin Cities
    ## 3189         Biomedical Engineering        PHD 2011 Univ of Wisconsin-Madison
    ## 3190                   Bacteriology              PHD 2008 Syracuse University
    ## 3191                       Oncology              PHD 1973 Columbia University
    ## 3192                    Mathematics                                  PHD 2009
    ## 3193                      Economics    PHD 2017 Univ of Michigan at Ann Arbor
    ## 3194         Biomedical Engineering             PHD 2006 Marquette University
    ## 3195           Nutritional Sciences        PHD 1980 Univ of Wisconsin-Madison
    ## 3196       Disease Prevention Admin        PHD 2012 Univ of Wisconsin-Madison
    ## 3197     Asian Languages & Cultures        PHD 1996 Univ of Wisconsin-Madison
    ## 3198 Init For Studies In Trnfm Entr        MBA 2003 Univ of Wisconsin-Madison
    ## 3199         Mechanical Engineering               PHD 1998 Cornell University
    ## 3200           Nutritional Sciences                 MPH 2009 Tufts University
    ## 3201             Acad&Prg-Noncredit                MA 2012 Middlebury College
    ## 3202                      Sociology        PHD 2009 Univ of Wisconsin-Madison
    ## 3203                   Biochemistry        PHD 1976 Michigan State University
    ## 3204                      Neurology           PHD 1985 University of Virginia
    ## 3205                       Oncology    PHD 2010 Nat Inst for Academic Degrees
    ## 3206        Comparative Biosciences              PHD 1999 University of Tokyo
    ## 3207        Comparative Biosciences            PHD 1992 Vanderbilt University
    ## 3208             Emergency Medicine             MD 1980 University of Chicago
    ## 3209    Mead Witter School Of Music                  PHD 1988 Yale University
    ## 3210                        English        PHD 2015 Univ of Wisconsin-Madison
    ## 3211     Chemical & Biological Engr       PHD 1983 Carnegie-Mellon University
    ## 3212               Risk & Insurance        MBA 1981 Univ of Wisconsin-Madison
    ## 3213               Medical Sciences            DVM 2002 University of Georgia
    ## 3214                   Religious St                 PHD 1999 Emory University
    ## 3215 Ms In Biotechnology Degree Prg                                     OQUAL
    ## 3216                        History   PHD 1999 Grad Sch & Univ Center Of Cuny
    ## 3217              Computer Sciences         PHD 2005 University of Washington
    ## 3218              Computer Sciences        PHD 2019 Univ of Wisconsin-Madison
    ## 3219               Risk & Insurance      PHD 2006 Univ of California Berkeley
    ## 3220  Classic & Ancient Near E Stds         PHD 2019 University of Notre Dame
    ## 3221                         Botany            PHD 1983 Washington University
    ## 3222  Materials Science&Engineering     PHD 2002 Univ of Tennessee, Knoxville
    ## 3223                      Economics            PHD 1995 University of Chicago
    ## 3224              Political Science              PHD 2010 Stanford University
    ## 3225                     Law School                   JD 2007 Yale University
    ## 3226                     Law School                 PHD 1997 Tufts University
    ## 3227              Surgical Sciences        DVM 2004 Universidade de Sao Paulo
    ## 3228                    Social Work        MSW 2012 Univ of Wisconsin-Madison
    ## 3229       Pathobiological Sciences      PHD 1998 Univ of MD Baltimore County
    ## 3230             Accting & Info Sys         JD 1978 Univ of Wisconsin-Madison
    ## 3231  Cell And Regenerative Biology            PHD 2009 University of Toronto
    ## 3232                       Pharmacy              PHD 2005 Stanford University
    ## 3233  Biostatistics&Med Informatics        PHD 2014 Univ Of NC At Chapel Hill
    ## 3234                 Design Studies                                    M.ARCH
    ## 3235                      Marketing                  PHD 2008 Duke University
    ## 3236              Computer Sciences       PHD 2020 Georgia Inst of Technology
    ## 3237  Rehab Psychology & Special Ed        PHD 2001 Univ of Wisconsin-Madison
    ## 3238           Nutritional Sciences    PHD 1993 Iowa State Univ of Sci & Tech
    ## 3239                        English        MAT 1995 Univ of Wisconsin-Madison
    ## 3240      Industrial & Systems Engr        PHD 2012 Univ of Wisconsin-Madison
    ## 3241  Communication Sci & Disorders      AUD 2006 Central Michigan University
    ## 3242    Mead Witter School Of Music     MA 1999 New England Cnsrvtry Of Music
    ## 3243                     Law School         JD 2009 Univ of Wisconsin-Madison
    ## 3244        German, Nordic & Slavic               PHD 1987 Cornell University
    ## 3245  Classic & Ancient Near E Stds      PHD 2012 Univ of Southern California
    ## 3246                       Pharmacy         PHD 2002 University of Washington
    ## 3247     Curriculum And Instruction    MS 2012 Concordia University Wisconsin
    ## 3248                        Nursing            PHD 2015 University of Florida
    ## 3249    Mead Witter School Of Music     MM 2000 Univ of Michigan at Ann Arbor
    ## 3250       Pathobiological Sciences     DVM 2002 Instituto Unificado Paulista
    ## 3251         Spanish And Portuguese        PHD 2005 Univ of Wisconsin-Madison
    ## 3252                       Pharmacy     PHARMD 2004 Univ Of NC At Chapel Hill
    ## 3253                Family Medicine        PHD 1993 Univ of Wisconsin-Madison
    ## 3254                       Medicine    MD 1992 Univ Med si Farm-Carol Davilla
    ## 3255                     Pediatrics         PHD 1966 Yokohama City University
    ## 3256   Management & Human Resources    PHD 2002 U of California-Santa Barbara
    ## 3257                        Physics    PHD 1981 University of Texas at Austin
    ## 3258                    Mathematics   PHD 1982 Univ of IL at Urbana-Champaign
    ## 3259                      Wiscience        PHD 2014 Univ of Wisconsin-Madison
    ## 3260                        History              PHD 1999 Columbia University
    ## 3261              Surgical Sciences                                  DVM 2005
    ## 3262             Information School    PHD 2017 Univ of Minnesota-Twin Cities
    ## 3263                Family Medicine         DS 2010 ROCKY MOUNTAIN UNIVERSITY
    ## 3264                   Food Science         MS 1988 Univ of Wisconsin-Madison
    ## 3265                      Wiscience         PHD 2013 Univ of California Davis
    ## 3266         Mechanical Engineering    PHD 1992 Univ of Michigan at Ann Arbor
    ## 3267             French And Italian        PHD 2011 Univ of Wisconsin-Madison
    ## 3268                     Psychiatry      MD 2010 Rutgers St Unv-New Brunswick
    ## 3269            Engineering Physics     PHD 2015 California Institute of Tech
    ## 3270                        Surgery        PHD 2001 Univ of Wisconsin-Madison
    ## 3271                   Food Science             PHD Univ of Wisconsin-Madison
    ## 3272                    Mathematics    PHD 1998 University of Texas at Austin
    ## 3273    Mead Witter School Of Music                  PHD 1974 Yale University
    ## 3274  Materials Science&Engineering        PHD 1992 Univ of Wisconsin-Madison
    ## 3275            Integrative Biology        PHD 1992 Michigan State University
    ## 3276        School Of Human Ecology    PHD 2013 Univ of Michigan at Ann Arbor
    ## 3277                   Bacteriology        PHD 1999 Univ of Wisconsin-Madison
    ## 3278             Accting & Info Sys        PHD 2013 Michigan State University
    ## 3279                      Geography     MS 2012 Univ of Minnesota-Twin Cities
    ## 3280 Biological Systems Engineering        PHD 2001 Univ Of Minnesota-St Paul
    ## 3281                      Marketing     PHD 1992 Univ of Tennessee, Knoxville
    ## 3282         Mechanical Engineering    PHD 2018 Univ of Michigan at Ann Arbor
    ## 3283                    Kinesiology            MS Univ of Wisconsin-Milwaukee
    ## 3284       African Cultural Studies        PHD 2004 Univ of Wisconsin-Madison
    ## 3285          Counseling Psychology              PHD 2008 University of Akron
    ## 3286             Emergency Medicine     MD 2011 SUNY Health Sci Cntr-Syracuse
    ## 3287  Cell And Regenerative Biology       PHD 1988 University of Pennsylvania
    ## 3288      Planning & Landscape Arch        PHD 2008 North Carolina State Univ
    ## 3289                     Geoscience       PHD 1981 Massachusetts Inst Of Tech
    ## 3290              Surgical Sciences                                  DVM 2014
    ## 3291           Nutritional Sciences        PHD 1985 Univ Of NC At Chapel Hill
    ## 3292                        Physics        PHD 2004 Univ of Wisconsin-Madison
    ## 3293                 Human Oncology          PHD 1995 Northwestern University
    ## 3294              Academic Programs     PHD 2012 Univ of California San Diego
    ## 3295     Asian Languages & Cultures                 PHD 2017 Emory University
    ## 3296                     Geoscience        PHD 1994 Univ Of Minnesota-St Paul
    ## 3297  Rehab Psychology & Special Ed        PHD 2014 Univ of Wisconsin-Madison
    ## 3298                       Genetics                  PHD 2001 Duke University
    ## 3299                        Physics             PHD 1985 Princeton University
    ## 3300          Counseling Psychology         BS 2014 Univ of Wisconsin-Madison
    ## 3301                    Kinesiology                EDD 2012 Walden University
    ## 3302                        English         MA 1988 Univ of Wisconsin-Madison
    ## 3303                     Law School         JD 1989 Univ of Wisconsin-Madison
    ## 3304     Civil & Environmental Engr        PHD 2006 Univ of Wisconsin-Madison
    ## 3305   Wisconsin School Of Business                                       PHD
    ## 3306 Ctr For Rus East Eur Cent Asia        PHD 1999 Univ of Wisconsin-Madison
    ## 3307                     Philosophy      PHD 2008 Univ of California Berkeley
    ## 3308               Medical Sciences       DVM 2012 University of Saskatchewan
    ## 3309                     Law School      JD 1979 University of Texas, Houston
    ## 3310     Curriculum And Instruction             PHD 1997 University of Ottawa
    ## 3311             French And Italian               PHD 2009 Indiana University
    ## 3312              Surgical Sciences      DVM 2016 St George's Univ Sch of Med
    ## 3313               Academic Affairs         BS 1995 Univ of Wisconsin-Madison
    ## 3314             Communication Arts               PHD 2010 Cornell University
    ## 3315               Academic Affairs       MS 2008 Eastern Illinois University
    ## 3316         Biomedical Engineering       PHD 1973 University of Pennsylvania
    ## 3317  Operations & Information Mgmt                  PHD 2012 Duke University
    ## 3318          Counseling Psychology         MS 2013 Univ of Wisconsin-Madison
    ## 3319                     Psychiatry         PHD 1989 Univ degli Studi di Pisa
    ## 3320             Information School        MLS 2013 Univ of Wisconsin-Madison
    ## 3321      Forest & Wildlife Ecology        PHD 1997 Univ Of NC At Chapel Hill
    ## 3322                      Astronomy             PHD 1997 University of London
    ## 3323                       Agronomy               PHD 1982 Cornell University
    ## 3324                    Mathematics      PHD 2012 Univ of California Berkeley
    ## 3325                    Kinesiology       PHD 2011 Univ of Alabama-Tuscaloosa
    ## 3326               Academic Affairs        PHD 2017 Univ of Wisconsin-Madison
    ## 3327 Lafollette Sch Of Publ Affairs              PHD 2020 Stanford University
    ## 3328                      Astronomy         PHD 2003 Johns Hopkins University
    ## 3329               Medical Sciences               PHD 1997 Cornell University
    ## 3330                         Botany         MS 2006 Univ of Wisconsin-Madison
    ## 3331              Academic Programs               PHD 1997 Harvard University
    ## 3332                    Social Work        MSW 2014 Univ of Wisconsin-Madison
    ## 3333   Management & Human Resources               PHD 1998 Cornell University
    ## 3334  Rehab Psychology & Special Ed        EDD 2004 Univ of Wisconsin-Madison
    ## 3335   Management & Human Resources           PHD 2008 Texas A & M University
    ## 3336                    Kinesiology        PHD 2017 Univ of Wisconsin-Madison
    ## 3337          Counseling Psychology                    MAED DePaul University
    ## 3338 Atmospheric & Oceanic Sciences        PHD 1986 Colorado State University
    ## 3339              Political Science          PHD 1990 Northwestern University
    ## 3340                        English          PHD 1996 Northwestern University
    ## 3341                     Entomology      PHD 2012 Univ of Colorado at Boulder
    ## 3342                     Law School                 JD 2003 DePaul University
    ## 3343         Mechanical Engineering   PHD 2000 Univ of IL at Urbana-Champaign
    ## 3344         General Administration                 MAT 2008 Edgewood College
    ## 3345                            Art        MFA 1999 Univ of Wisconsin-Madison
    ## 3346              Ctr For Jewish St               JD 1963 New York Law School
    ## 3347                      Marketing         MS 2000 Univ of Wisconsin-Madison
    ## 3348        German, Nordic & Slavic        PHD 2009 Univ of Wisconsin-Madison
    ## 3349   Se Asian Summer Studies Inst                           PHD 2013 France
    ## 3350              Surgical Sciences           DVM 1998 University of Montreal
    ## 3351                     Law School         JD 2008 Univ of Wisconsin-Madison
    ## 3352          Counseling Psychology        EDM 2018 Univ of Wisconsin-Madison
    ## 3353     Educational Policy Studies           PHD Univ of California Berkeley
    ## 3354                     Law School         JD 2020 Univ of Wisconsin-Madison
    ## 3355                      Geography      PHD 1992 Univ of California Berkeley
    ## 3356            Integrative Biology            PHD 1985 University of Georgia
    ## 3357         Mechanical Engineering               PHD 1990 Cornell University
    ## 3358         Biomedical Engineering       MS 1986 Univ of California Berkeley
    ## 3359              Computer Sciences       PHD 2017 Massachusetts Inst Of Tech
    ## 3360     Curriculum And Instruction        PHD 1990 Univ of Wisconsin-Madison
    ## 3361     Department Of Neuroscience                 PHD 1983 Brown University
    ## 3362  Pathology&Laboratory Medicine               PHD 2014 University of Iowa
    ## 3363  Ed Leadership&Policy Analysis            PHD 1984 University of Florida
    ## 3364          Counseling Psychology               EDM 2013 Clemson University
    ## 3365  Ed Leadership&Policy Analysis        PHD 2012 Univ of Wisconsin-Madison
    ## 3366                   Soil Science      PHD 1989 U de Santiago de Compostela
    ## 3367                        History              PHD 2017 Columbia University
    ## 3368                        History      PHD 2007 Univ of California Berkeley
    ## 3369        School Of Human Ecology               PHD 2020 Cornell University
    ## 3370               Medical Sciences       DVM 1984 University of Saskatchewan
    ## 3371                    Social Work       MSSW 2007 Univ of Wisconsin-Madison
    ## 3372       Gender And Women Studies         MS 2008 Univ of Wisconsin-Madison
    ## 3373                    Mathematics     PHD 2004 Budapest Univ of Tech & Econ
    ## 3374                     Geoscience    PHD 1980 Univ of Michigan at Ann Arbor
    ## 3375    Mead Witter School Of Music      MFA 1977 Conserv Nat Arts et Metiers
    ## 3376                Theatre & Drama                  MFA 2006 Yale University
    ## 3377              Surgical Sciences                                       DVM
    ## 3378             Information School       MLIS 1997 Univ of Wisconsin-Madison
    ## 3379        German, Nordic & Slavic         PHD 1996 Arizona State University
    ## 3380      Forest & Wildlife Ecology        PHD 1995 Michigan State University
    ## 3381     Electrical & Computer Engr              PHD 1992 Stanford University
    ## 3382                 Anesthesiology         MD 2002 Univ of Wisconsin-Madison
    ## 3383                    Kinesiology         PHD 1984 Univ of California Davis
    ## 3384     Chemical & Biological Engr       PHD 2014 Massachusetts Inst Of Tech
    ## 3385                        Nursing                  MSN 2014 Duke University
    ## 3386              Computer Sciences            PHD 1999 University of Chicago
    ## 3387      Animal And Dairy Sciences         PHD 2015 Univ of California Davis
    ## 3388                   Food Science                   PHD 2007 Ireland (Eire)
    ## 3389 Agricultural&Applied Economics        PHD 2018 Univ of Wisconsin-Madison
    ## 3390                     Psychology         JD 1990 Univ of Wisconsin-Madison
    ## 3391                     Law School         JD 2006 Univ of Wisconsin-Madison
    ## 3392             Communication Arts   PHD 1998 Univ of IL at Urbana-Champaign
    ## 3393                     Law School              JD 2007 University of Oregon
    ## 3394  Classic & Ancient Near E Stds        PHD 1988 Univ of Wisconsin-Madison
    ## 3395                        Physics      PHD 2009 Univ of California Berkeley
    ## 3396            Integrative Biology                PHD 1999 McGill University
    ## 3397                      Astronomy               PHD 2017 Harvard University
    ## 3398               Academic Affairs                       PHD Rush University
    ## 3399     Electrical & Computer Engr      PHD 1986 Univ of Colorado at Boulder
    ## 3400    Mead Witter School Of Music                   MM 1977 Yale University
    ## 3401                        English        PHD 2011 Rutgers State Univ-Newark
    ## 3402                      Neurology      PHD 2006 Universidad de La Republica
    ## 3403         Lat Amer Carib Iber St        PHD 1998 Univ of Wisconsin-Madison
    ## 3404                Medical Physics           PHD 1995 University of Kentucky
    ## 3405                     Law School                   JD 2018 Yale University
    ## 3406             French And Italian            PHD 2004 University of Chicago
    ## 3407  Ed Leadership&Policy Analysis         JD 1999 Univ of Wisconsin-Madison
    ## 3408                        Physics               PHD 2001 Cornell University
    ## 3409      Industrial & Systems Engr                PHD 1991 Purdue University
    ## 3410  Communication Sci & Disorders               AUD 2009 Indiana University
    ## 3411                            Art        MFA 2000 Univ of Wisconsin-Madison
    ## 3412  Biostatistics&Med Informatics         PHD 2009 University Of New Mexico
    ## 3413           Neurological Surgery          PHD 1991 University of Hyderabad
    ## 3414              Computer Sciences      PHD 2017 Univ of California Berkeley
    ## 3415     Electrical & Computer Engr        PHD 1992 Univ of Wisconsin-Madison
    ## 3416                   Soil Science        PHD 1989 Univ of Wisconsin-Madison
    ## 3417                   Biochemistry     PHD 2013 California Institute of Tech
    ## 3418 Ms In Biotechnology Degree Prg          MBA Univ of Wisconsin-Whitewater
    ## 3419               Medical Sciences        DVM 2003 Univ of Wisconsin-Madison
    ## 3420                       Genetics    PHD 2013 Univ of Minnesota-Twin Cities
    ## 3421                      Chemistry          PHD 1967 Northwestern University
    ## 3422        Comparative Biosciences                  PHD 2003 SUNY at Buffalo
    ## 3423 Ms In Biotechnology Degree Prg        MBA 2017 Univ of Wisconsin-Madison
    ## 3424     Curriculum And Instruction        PHD 2010 Univ of Wisconsin-Madison
    ## 3425             French And Italian         PHD 1990 Johns Hopkins University
    ## 3426 Chicana/O And Latina/O Studies    PHD 2019 University of Texas at Austin
    ## 3427 Atmospheric & Oceanic Sciences         PHD 2002 University of Washington
    ## 3428                     Law School         JD 1978 Univ of Wisconsin-Madison
    ## 3429                Family Medicine         MS 1986 Univ of Wisconsin-Madison
    ## 3430                       Pharmacy   PHARMD 1995 Univ of Illinois at Chicago
    ## 3431               Medical Sciences        DVM 2003 Univ of Wisconsin-Madison
    ## 3432         Educational Psychology   PHD 2012 Univ of California Los Angeles
    ## 3433                        Nursing        MSN 2000 Univ of Wisconsin-Madison
    ## 3434                        Surgery           PHD 2001 University of Kentucky
    ## 3435                     Law School               JD 1995 Brooklyn Law School
    ## 3436                     Law School             JD 1994 Valparaiso University
    ## 3437  Materials Science&Engineering   PHD 2001 Univ of IL at Urbana-Champaign
    ## 3438                     Philosophy    PHD 2001 Univ of Michigan at Ann Arbor
    ## 3439  Vp Diversity And Climate Prog      MS 2010 Univ of Wisconsin-Whitewater
    ## 3440     Civil & Environmental Engr                                    M.ARCH
    ## 3441       Gender And Women Studies               PHD 2016 Indiana University
    ## 3442                    Mathematics           PHD 2019 University of Oklahoma
    ## 3443 Human Development&Family Study         PHD 2018 Univ of California Davis
    ## 3444  Ed Leadership&Policy Analysis        PHD 2020 Univ of Wisconsin-Madison
    ## 3445  Journalism&Mass Communication               PHD 2006 Indiana University
    ## 3446         Mechanical Engineering         PHD 2017 Colorado School of Mines
    ## 3447                Theatre & Drama    MFA 1994 University of Texas at Austin
    ## 3448    Life Sciences Communication         BA 2013 Univ of Wisconsin-Madison
    ## 3449               Academic Affairs     PHARMD 2016 Univ of Wisconsin-Madison
    ## 3450 Atmospheric & Oceanic Sciences        PHD 2011 Univ of Wisconsin-Madison
    ## 3451                       Medicine               MD 2011 Aga Khan University
    ## 3452                Medical Physics   PHD 1987 Univ of IL at Urbana-Champaign
    ## 3453                      Astronomy          PHD 1990 University of Groningen
    ## 3454                     Psychiatry           MD 1997 Northwestern University
    ## 3455                       Pharmacy     PHARMD 1993 Univ of Wisconsin-Madison
    ## 3456                        History                  PHD 2016 Yale University
    ## 3457                    Mathematics              PHD 2014 Columbia University
    ## 3458                    Mathematics       PHD 1989 Massachusetts Inst Of Tech
    ## 3459                          Dance        MFA 2004 SUNY College at Brockport
    ## 3460                      Economics            PHD 1986 University of Chicago
    ## 3461               Medical Sciences        DVM 2008 Michigan State University
    ## 3462                        Physics             PHD 1988 Princeton University
    ## 3463 Lafollette Sch Of Publ Affairs          PHD 1999 Northwestern University
    ## 3464                        Nursing          DNP 2012 Univ of Wisconsin-Stout
    ## 3465              Surgical Sciences        DVM 2007 Univ of Wisconsin-Madison
    ## 3466            Administration-Vmth         MS 2007 Univ of Wisconsin-Madison
    ## 3467    Mead Witter School Of Music              PHD 2010 New York University
    ## 3468          Counseling Psychology            MS Western Illinois University
    ## 3469   Wisconsin School Of Business         JD 1975 Univ of Wisconsin-Madison
    ## 3470  Real Estate & Urgan Land Econ         MS 1992 Univ of Wisconsin-Madison
    ## 3471                     Psychology   PHD 2011 University of Nebraska-Lincoln
    ## 3472               Academic Affairs       DRPH 2010 Univ of Wisconsin-Madison
    ## 3473                    Social Work    PHD 2013 Univ of Michigan at Ann Arbor
    ## 3474        German, Nordic & Slavic        PHD 2002 Univ of Wisconsin-Madison
    ## 3475                        History    PHD 1985 Univ of Michigan at Ann Arbor
    ## 3476                    Mathematics                PHD 2012 Purdue University
    ## 3477     Civil & Environmental Engr                                  PHD 2012
    ## 3478  Biostatistics&Med Informatics                  PHD 2015 Yale University
    ## 3479            Integrative Biology      PHD 2013 Univ of Southern California
    ## 3480             Communication Arts        PHD 2006 Univ of Wisconsin-Madison
    ## 3481                   Bacteriology    PHD 2002 U of California San Francisco
    ## 3482                        English     MA 1995 University of Hawaii at Manoa
    ## 3483                     Statistics            PHD 2014 University of Chicago
    ## 3484                      Chemistry                  PHD 2015 Yale University
    ## 3485      Industrial & Systems Engr   PHD 2015 Univ of IL at Urbana-Champaign
    ## 3486  Materials Science&Engineering       PHD 2005 Georgia Inst of Technology
    ## 3487  Ed Leadership&Policy Analysis            PHD 2008 Ohio State University
    ## 3488 Lafollette Sch Of Publ Affairs                  PHD 2009 Duke University
    ## 3489                     Statistics      PHD 1992 Univ of California Berkeley
    ## 3490                   Horticulture        PHD 2012 Univ of Wisconsin-Madison
    ## 3491     Electrical & Computer Engr           PHD Univ of California Berkeley
    ## 3492             Accting & Info Sys          MPA Univ of Wisconsin-Whitewater
    ## 3493             Accting & Info Sys                                  PHD 2011
    ## 3494                        English   PHD 1997 Padagogische Hochsch Gottingen
    ## 3495   Wisconsin School Of Business        PHD 1999 Univ of Wisconsin-Madison
    ## 3496                        Nursing        PHD 2002 Univ of Wisconsin-Madison
    ## 3497                     Psychology                  PHD 2016 Yale University
    ## 3498     Curriculum And Instruction         PHD 2014 University of Pittsburgh
    ## 3499             Accting & Info Sys               PHD 1989 University of Iowa
    ## 3500                     Pediatrics         MD 1985 Univ of Wisconsin-Madison
    ## 3501                        History        PHD 2017 Univ of Wisconsin-Madison
    ## 3502     Population Health Sciences        PHD 2013 Univ of Wisconsin-Madison
    ## 3503                       Genetics                  PHD 1992 Yale University
    ## 3504                   Bacteriology                  PHD 1992 Yale University
    ## 3505 Orthopedics And Rehabilitation     MD 2010 Univ Of TX Med Branch-Galvest
    ## 3506        Comparative Biosciences         PHD 1997 University of Washington
    ## 3507      Animal And Dairy Sciences        PHD 1990 Univ of Wisconsin-Madison
    ## 3508   Wisconsin School Of Business        PHD 2020 Univ of Missouri-Columbia
    ## 3509                Theatre & Drama              MFA 2008 University of Idaho
    ## 3510  Cell And Regenerative Biology     PHD 2003 Univ of California San Diego
    ## 3511                      Chemistry      DS 2005 California Institute of Tech
    ## 3512            Integrative Biology               PHD 2012 Harvard University
    ## 3513                         Botany        PHD 2016 Univ of Wisconsin-Madison
    ## 3514                   Biochemistry      PHD 2013 Univ of California Berkeley
    ## 3515              Political Science              PHD 2009 Stanford University
    ## 3516     Civil & Environmental Engr                                       PHD
    ## 3517                      Radiology    PHD 1985 Univ of Michigan at Ann Arbor
    ## 3518      Animal And Dairy Sciences        PHD 1992 Univ of Wisconsin-Madison
    ## 3519                     Law School     JD 1983 University of Texas at Austin
    ## 3520 Lafollette Sch Of Publ Affairs      PHD 1978 Univ of California Berkeley
    ## 3521                      Marketing              PHD 2013 Columbia University
    ## 3522                      Chemistry      PHD 1979 Univ of California Berkeley
    ## 3523                      Chemistry      PHD 2005 Univ of California Berkeley
    ## 3524           Medical Microbiology    PHD 1979 VA Commonwealth Univ-Hlth Sci
    ## 3525                        Surgery        PHD 2006 Univ of Wisconsin-Madison
    ## 3526  Cell And Regenerative Biology        PHD 1996 Univ of Wisconsin-Madison
    ## 3527                        English      PHD 2009 Univ of California Berkeley
    ## 3528  Ed Leadership&Policy Analysis    PHD 2011 University of Texas at Austin
    ## 3529  Operations & Information Mgmt                 PHD 1978 Lunds University
    ## 3530                   Anthropology    PHD 1994 Univ of Massachusetts Amherst
    ## 3531     Electrical & Computer Engr      PHD 1988 Univ of California Berkeley
    ## 3532                      Chemistry        PHD 1999 Univ of Wisconsin-Madison
    ## 3533                   Horticulture           PHD 1998 Texas A & M University
    ## 3534                Family Medicine        PHD 2016 Univ of Wisconsin-Madison
    ## 3535                       Pharmacy            PHD 2015 Vanderbilt University
    ## 3536                      Economics                  PHD 2006 Yale University
    ## 3537                       Agronomy   PHD 2016 University of Nebraska-Lincoln
    ## 3538                       Genetics   PHD 2014 Univ of California Los Angeles
    ## 3539          Afro-American Studies   PHD 1979 Univ of IL at Urbana-Champaign
    ## 3540      Industrial & Systems Engr          PHD 2014 George Mason University
    ## 3541  Engr Professional Development        MBA 1969 Univ of Wisconsin-Madison
    ## 3542  Engr Professional Development         EDD 2017 Univ of Minnesota-Duluth
    ## 3543                      Economics       PHD 1983 Massachusetts Inst Of Tech
    ## 3544                       Medicine         PHD 2013 Johns Hopkins University
    ## 3545                   Biochemistry                PHD 1980 Purdue University
    ## 3546                      Neurology               PHD 1995 Notre Dame College
    ## 3547                 Human Oncology        PHD 2004 Univ of Wisconsin-Madison
    ## 3548               Consumer Science             PHD 2004 University of Oxford
    ## 3549      Animal And Dairy Sciences                PHD 2010 Purdue University
    ## 3550              Academic Programs      PHD 1998 Western Michigan University
    ## 3551              Surgical Sciences           DVM 2017 Texas A & M University
    ## 3552                        History               PHD 2015 Harvard University
    ## 3553                   Soil Science               PHD 2014 Cornell University
    ## 3554          Afro-American Studies    PHD 2000 Univ of Michigan at Ann Arbor
    ## 3555                        Nursing      DNS 2017 Univ of Wisconsin-Milwaukee
    ## 3556                     Philosophy             PHD 2005 University of Oxford
    ## 3557                      Chemistry     PHD 2015 California Institute of Tech
    ## 3558                      Chemistry     PHD 2005 California Institute of Tech
    ## 3559             Acad&Prg-Noncredit          MFA 2013 George Mason University
    ## 3560                Medical Physics        PHD 2002 Univ of Wisconsin-Madison
    ## 3561          Counseling Psychology            MS Univ of Wisconsin-Milwaukee
    ## 3562      Industrial & Systems Engr       PHD 1992 Texas Christian University
    ## 3563  Rehab Psychology & Special Ed        PHD 1993 Univ of Wisconsin-Madison
    ## 3564    Mead Witter School Of Music         MM 2018 Manhattan School Of Music
    ## 3565                     Law School       JD 1992 Washington & Lee University
    ## 3566             Information School        MA 2016 University Of South Dakota
    ## 3567                      Astronomy         PHD 1992 University of Washington
    ## 3568             Accting & Info Sys        PHD 1983 Univ of Wisconsin-Madison
    ## 3569                   Biochemistry              PHD 2005 Columbia University
    ## 3570             Information School         MA 2008 Univ of Wisconsin-Madison
    ## 3571  Rehab Psychology & Special Ed         PHD 1997 University of Washington
    ## 3572            Integrative Biology           PHD 2015 University of Virginia
    ## 3573     Curriculum And Instruction  MSED 2019 Concordia University Wisconsin
    ## 3574         Biomedical Engineering        DPT 2015 Univ of Wisconsin-Madison
    ## 3575         Educational Psychology        PHD 2017 Univ of Wisconsin-Madison
    ## 3576             Information School             PHD 2002 University of London
    ## 3577                      Geography                 PHD 1999 Brown University
    ## 3578                      Wiscience     PHD 2016 Univ of California San Diego
    ## 3579              Computer Sciences      PHD 2014 Univ of Wisconsin-Milwaukee
    ## 3580         Biomedical Engineering         PHD 2001 Arizona State University
    ## 3581        Obstetrics & Gynecology           MD 2004 Meharry Medical College
    ## 3582   Management & Human Resources    MA 2005 Walsh Col Accountant & Bus Adm
    ## 3583                      Economics            PHD 2001 University of Chicago
    ## 3584            Engineering Physics         MS 2000 Univ of Wisconsin-Madison
    ## 3585                     Law School             JD 1975 Georgetown University
    ## 3586             Communication Arts   PHD 2019 Univ of IL at Urbana-Champaign
    ## 3587               Academic Affairs                                  MMS 2007
    ## 3588                        History    PHD 2020 Univ of Michigan at Ann Arbor
    ## 3589                    Social Work                  MSW 2005 Simmons College
    ## 3590                 Anesthesiology         MD 1997 Univ of Wisconsin-Madison
    ## 3591                     Law School         JD 2017 Univ of Wisconsin-Madison
    ## 3592            Engineering Physics        PHD 1999 Univ of Wisconsin-Madison
    ## 3593      Animal And Dairy Sciences    PHD 1987 Univ of Michigan at Ann Arbor
    ## 3594                        Nursing                MSN 2013 Walden University
    ## 3595                      Marketing     MBA 2011 Univ of Wisconsin-Eau Claire
    ## 3596  Ed Leadership&Policy Analysis               PHD 2006 Indiana University
    ## 3597                     Psychology        PHD 1990 Univ of Wisconsin-Madison
    ## 3598                    Kinesiology        PHD 1994 Univ of Wisconsin-Madison
    ## 3599                      Economics   PHD 2005 Univ of California Los Angeles
    ## 3600         Biomedical Engineering                                       PHD
    ## 3601  Ed Leadership&Policy Analysis        PHD 2011 Univ of Wisconsin-Madison
    ## 3602                    Amer Ind St            LLM 1997 Georgetown University
    ## 3603        German, Nordic & Slavic            PHD 2015 University of Toronto
    ## 3604        German, Nordic & Slavic             PHD 1987 University of London
    ## 3605                      Astronomy    PHD 2005 University of Texas at Austin
    ## 3606             Accting & Info Sys       MACC 2020 Univ of Wisconsin-Madison
    ## 3607         Educational Psychology        PHD 1996 Univ of Wisconsin-Madison
    ## 3608         Educational Psychology        PHD 2000 Univ of Wisconsin-Madison
    ## 3609        School Of Human Ecology    PHD 1996 Univ of Michigan at Ann Arbor
    ## 3610                        English        PHD 2009 Univ Of NC At Chapel Hill
    ## 3611               Medical Sciences        PHD 2010 North Carolina State Univ
    ## 3612           Medical Microbiology        PHD 1989 Univ Of NC At Chapel Hill
    ## 3613                      Chemistry               PHD 1965 Harvard University
    ## 3614                         Botany        PHD 2005 Univ of Wisconsin-Madison
    ## 3615                      Geography            PHD 2007 University of Arizona
    ## 3616 Ms In Biotechnology Degree Prg         MS 2004 Univ of Wisconsin-Madison
    ## 3617     Civil & Environmental Engr             PHD 2013 Princeton University
    ## 3618                   Biochemistry                 PHD 2002 Emory University
    ## 3619                      Chemistry         PHD 1970 Johns Hopkins University
    ## 3620                        Finance    PHD 1986 Univ of Minnesota-Twin Cities
    ## 3621              Computer Sciences         PHD 1984 University of Queensland
    ## 3622                     Law School             JD 2006 Washington University
    ## 3623          Counseling Psychology               EDD 2006 Harvard University
    ## 3624                     Statistics         MS 2020 Univ of Wisconsin-Madison
    ## 3625                    Mathematics               PHD 2016 Cornell University
    ## 3626     Civil & Environmental Engr       PHD 1999 Massachusetts Inst Of Tech
    ## 3627                     Law School    JD 2009 Univ of California Los Angeles
    ## 3628                        Physics               PHD 1970 Harvard University
    ## 3629               Academic Affairs           MS 2000 University of Edinburgh
    ## 3630    Life Sciences Communication         PHD 2005 University of Washington
    ## 3631                       Oncology        PHD 1997 Rutgers State Univ-Newark
    ## 3632                    Social Work   PHD 2013 Univ of California Los Angeles
    ## 3633                     Geoscience         PHD 1993 Johns Hopkins University
    ## 3634      Industrial & Systems Engr       PHD 2015 Georgia Inst of Technology
    ## 3635                       Oncology               PHD 1999 University of Iowa
    ## 3636         Mechanical Engineering      PHD 2014 Chinese Academy of Sciences
    ## 3637                     Law School                   JD 2006 Yale University
    ## 3638                     Law School        PHD 2006 Univ Of NC At Chapel Hill
    ## 3639 Lafollette Sch Of Publ Affairs        PHD 2003 Univ Of NC At Chapel Hill
    ## 3640            Integrative Biology        PHD 2016 Univ of Wisconsin-Madison
    ## 3641                     Statistics      PHD 1981 Univ of California Berkeley
    ## 3642                     Statistics       PHD 2006 Case Western Reserve Univ.
    ## 3643  Journalism&Mass Communication            PHD University of Pennsylvania
    ## 3644                    Mathematics    PHD 1995 Univ of Maryland College Park
    ## 3645                      Chemistry                  PHD 2016 Duke University
    ## 3646    Engineering Research Center             PHD Univ of Wisconsin-Madison
    ## 3647  Real Estate & Urgan Land Econ               PHD 1991 University of Iowa
    ## 3648                        Physics              PHD 2003 Stanford University
    ## 3649           Nutritional Sciences        PHD 2000 Univ Of NC At Chapel Hill
    ## 3650         Biomedical Engineering         PHD Univ of Maryland College Park
    ## 3651                      Chemistry        PHD 1991 North Carolina State Univ
    ## 3652                       Genetics        PHD 1986 Univ of Wisconsin-Madison
    ## 3653     Chemical & Biological Engr      PHD 1988 Univ of California Berkeley
    ## 3654     Department Of Neuroscience    PHD 1973 Univ of Michigan at Ann Arbor
    ## 3655                      Chemistry     PHD 2002 California Institute of Tech
    ## 3656             Information School       MLIS 2008 Univ of Wisconsin-Madison
    ## 3657                     Entomology        PHD 1981 Michigan State University
    ## 3658                        History              PHD 1993 Columbia University
    ## 3659                     Law School         JD 2005 Univ of Wisconsin-Madison
    ## 3660                        English    PHD 1997 Univ of Michigan at Ann Arbor
    ## 3661                        English       PHD 1989 University of Pennsylvania
    ## 3662                      Geography         PHD 2010 University of Washington
    ## 3663                   Bacteriology        PHD 1995 Univ of Wisconsin-Madison
    ## 3664                          Dance                PHD 1994 Temple University
    ## 3665                      Radiology   PHD 2006 Univ of IL at Urbana-Champaign
    ## 3666                       Pharmacy            PHD 1991 Ohio State University
    ## 3667  Biostatistics&Med Informatics    PHD 2003 Univ of Michigan at Ann Arbor
    ## 3668                        English              PHD 2005 Stanford University
    ## 3669              Computer Sciences       PHD 2017 Massachusetts Inst Of Tech
    ## 3670     Electrical & Computer Engr              PHD 2009 Stanford University
    ## 3671        German, Nordic & Slavic               PHD 2015 Harvard University
    ## 3672  Engr Professional Development            PHD Massachusetts Inst Of Tech
    ## 3673                  Naval Science         MS 1998 Naval Postgraduate School
    ## 3674                     Geoscience              PHD 2018 Stanford University
    ## 3675                       Medicine         MD 1990 Univ of Wisconsin-Madison
    ## 3676                   Horticulture        PHD 2005 Univ of Wisconsin-Madison
    ## 3677       Pathobiological Sciences    PHD 2011 Iowa State Univ of Sci & Tech
    ## 3678                  Asian Studies      MA 1999 Northern Illinois University
    ## 3679                      Chemistry      PHD 1999 Univ of California Berkeley
    ## 3680                     Pediatrics         MD 2013 Univ of Wisconsin-Madison
    ## 3681                        Surgery     MD 1996 Univ of Alabama at Birmingham
    ## 3682     Chemical & Biological Engr       PHD 2008 Carnegie-Mellon University
    ## 3683      Industrial & Systems Engr               PHD 2015 Cornell University
    ## 3684 Orthopedics And Rehabilitation                  MD 1982 Tufts University
    ## 3685              Academic Programs        PHD 1968 Univ of Wisconsin-Madison
    ## 3686             Accting & Info Sys        PHD 1996 University of Connecticut
    ## 3687                       Medicine        PHD 2015 Univ of Wisconsin-Madison
    ## 3688                      Chemistry        PHD 1999 Univ of Wisconsin-Madison
    ## 3689                    Mathematics       PHD 2015 Massachusetts Inst Of Tech
    ## 3690                          Dance     PHD 2015 Univ of California Riverside
    ## 3691                     Statistics        PHD 2000 Univ Of NC At Chapel Hill
    ## 3692  Pathology&Laboratory Medicine    PHD 2007 Texas A & M Univ At Galveston
    ## 3693                     Statistics       PHD 2015 University of Pennsylvania
    ## 3694  Real Estate & Urgan Land Econ      PHD 2020 Univ of California Berkeley
    ## 3695     Asian Languages & Cultures     PHD 1992 Univ of California San Diego
    ## 3696                     Law School         PHD 2014 Macau Univ of Sci & Tech
    ## 3697                       Oncology       PHD 2001 University of Pennsylvania
    ## 3698                      Astronomy     PHD 2015 California Institute of Tech
    ## 3699     Asian Languages & Cultures                    PHD University of Iowa
    ## 3700          Counseling Psychology              MS Univ of Wisconsin-Madison
    ## 3701        School Of Human Ecology       PHD 2014 University of Pennsylvania
    ## 3702            Engineering Physics           PHD 2009 Polytechnic University
    ## 3703                     Statistics        PHD 2002 Univ Of NC At Chapel Hill
    ## 3704 Biological Systems Engineering                PHD 2017 Purdue University
    ## 3705        Comparative Biosciences            PHD 2014 University of Georgia
    ## 3706  Biostatistics&Med Informatics             PHD Univ of Wisconsin-Madison
    ## 3707     Department Of Neuroscience         PHD 1997 University of Washington
    ## 3708              Computer Sciences               PHD 2020 Cornell University
    ## 3709        Obstetrics & Gynecology    PHD 1995 North Dakota State University
    ## 3710                       Genetics            PHD 2007 Ohio State University
    ## 3711              Computer Sciences        PHD 2008 Univ Of Missouri-St Louis
    ## 3712      Industrial & Systems Engr    PHD 2000 Univ of Michigan at Ann Arbor
    ## 3713                   Anthropology                  PHD 1997 Duke University
    ## 3714                      Geography            PHD 1994 University of Toronto
    ## 3715              Computer Sciences       PHD 2005 Carnegie-Mellon University
    ## 3716                     Statistics    PHD 2000 Iowa State Univ of Sci & Tech
    ## 3717     Asian Languages & Cultures            PHD 2010 University of Florida
    ## 3718     Civil & Environmental Engr                                       PHD
    ## 3719                            Art        BFA 1993 Univ of Wisconsin-Oshkosh
    ## 3720        German, Nordic & Slavic              PHD 2016 Stanford University
    ## 3721                    Mathematics    PHD 2014 Univ of Michigan at Ann Arbor
    ## 3722                        English      PHD 2000 Univ of California Berkeley
    ## 3723          Counseling Psychology      MSA 2015 Univ of Wisconsin-Milwaukee
    ## 3724         Mechanical Engineering              PHD 2005 Stanford University
    ## 3725       Pathobiological Sciences                                  DVM 2013
    ## 3726                     Geoscience    PHD 2012 Pennsylvania State University
    ## 3727                        Nursing                 EDD 2017 Edgewood College
    ## 3728      Forest & Wildlife Ecology    PHD 2008 SUNY Col Environ Sci & Forest
    ## 3729                    Social Work        MSW 2006 Univ of Wisconsin-Madison
    ## 3730                        Nursing        PHD 2016 Univ of Wisconsin-Madison
    ## 3731              Political Science    PHD 2000 Univ of Minnesota-Twin Cities
    ## 3732                       Genetics    PHD 2013 Univ of Minnesota-Twin Cities
    ## 3733                    Kinesiology      MS 2010 Univ of Wisconsin-Whitewater
    ## 3734          Counseling Psychology      MS 1996 Univ of Wisconsin-Whitewater
    ## 3735                        English                  PHD 2010 Yale University
    ## 3736                      Astronomy             PHD 1977 Princeton University
