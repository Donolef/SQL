1.  Combien la base de données contient-elle de sociétés offshores différentes dont la source est "Panama Papers" ?

Requête SQL

    SELECT COUNT ( * ) FROM entity 
    WHERE source = "Panama Papers"

Réponse obtenue

    213634

2.  Quel intermédiaire a créé le plus de sociétés offshores ? A-t-on son adresse et son pays ?

Requête SQL (construction)

    SELECT  
      intermediary.name,
      intermediary.id, 
      assoc_inter_entity.inter,
      intermediary.id_address,
      address.id_address,
      address.address,
      address.country_codes,
      count(*)
    FROM intermediary, address, assoc_inter_entity
    WHERE 
      intermediary.id_address = address.id_address and
      assoc_inter_entity.inter = intermediary.id
    GROUP BY intermediary.id
    ORDER BY COUNT (*) DESC LIMIT 1.

Requête SQL (condensée)

    SELECT  
      intermediary.name,
      address.address,
      address.country_codes,
      count(*)
    FROM intermediary, address, assoc_inter_entity
    WHERE 
      intermediary.id_address = address.id_address and
      assoc_inter_entity.inter = intermediary.id
    GROUP BY intermediary.id
    ORDER BY COUNT (*) DESC LIMIT 1.

Réponse obtenue

    ORION HOUSE SERVICES (HK) LIMITED ORION HOUSE SERVICES (HK) LIMITED ROOM 1401; 14/F.; WORLD COMMERCE  CENTRE;[...] TSUI; KOWLOON; HONG KONG Hong Kong ; 7016

3.  Combien la base contient-elle de bénéficiaires avec un nom unique ? Quel est le bénéficiaire dont le nom revient le plus souvent ?

Requête SQL (1)

    SELECT COUNT(DISTINCT name) FROM officer 

Réponse obtenue (1)

     122590 

Requête SQL (2)

    SELECT name FROM officer GROUP BY name ORDER BY COUNT( * ) DESC LIMIT 1;

Réponse obtenue (2)

    THE BEARER

4.  Donner la liste des juridictions avec le nombre d'entreprises offshores enregistrées sur chaque territoire, triée par ordre décroissant.

Requête SQL
    
    SELECT entity.jurisdiction_description, count(*)
    FROM entity
    GROUP BY entity.jurisdiction_description
    ORDER BY COUNT (entity.jurisdiction_description) DESC

Réponse obtenue
    
    British Virgin Islands  114849
    Panama  48870
    Bahamas 16082
    Seychelles  15341
    Niue  9711
    Samoa 5361
    British Anguilla  3286
    Nevada  1273
    Hong Kong 457
    United Kingdom  151
    Belize  133
    Costa Rica  81
    Cyprus  78
    Uruguay 54
    New Zealand 49
    Jersey  41
    Wyoming 39
    Malta 29
    Isle Of Man 8
    Ras Al Khaimah  2
    Singapore 1

5.  Regrouper les sociétés offshores par statut, et trier la liste par ordre décroissant.

Requête SQL
    
    SELECT entity.status, count(*)
    FROM entity
    GROUP BY entity.status
    ORDER BY COUNT (entity.status) DESC

Réponse obtenue
    
    Defaulted 100090
    Active  57990
    Dissolved 22377
    Changed agent 16043
    Inactivated 7640
    Resigned as agent 3174
    Shelf company 2576
    Dissolved shelf company 1573
    Bad debt account  1416
    Trash company 878
    In transition 776
    Relocated in new jurisdiction 672
    Discontinued  423
    Shelf company not possible to sell  201
    In liquidation  40
    Change in administration pending  21
    Resigned as agent of shelf company  3
    NULL 3

6.  Trouver la liste des bénéficiaires dont le nom contient "BNP" et ajouter, pour chaque bénéficiaire, le nom des sociétés offshores.

Requête SQL (construction)
    
    SELECT 
      officer.name,
      officer.id,
      assoc_officer_entity.officer,
      assoc_officer_entity.entity,
      entity.id,
      entity.name
    FROM officer, assoc_officer_entity, entity
    WHERE 
      officer.name LIKE '%BNP%'  and
      officer.id = assoc_officer_entity.officer and
      assoc_officer_entity.entity = entity.id

Requête SQL (condensée)
    
    SELECT 
      officer.name,
      entity.name
    FROM officer, assoc_officer_entity, entity
    WHERE 
      officer.name LIKE '%BNP%'  and
      officer.id = assoc_officer_entity.officer and
      assoc_officer_entity.entity = entity.id

Réponse obtenue
    
    BNP PARIBAS JERSEY NOMINEES COMPANY LIMITED MAJESTIC FINANCE CORP.
    BNP PARIBAS JERSEY NOMINEE COMPANY LIMITED  MAJESTIC FINANCE CORP.
    BNP Paribas Jersey Nominee Company Limited  LOWDER INVESTMENTS LTD.
    BNP JERSEY NOMINEE COMPANY  THOR INVESTMENTS LIMITED
    BNP PARIBAS JERSEY TRUST  THOR INVESTMENTS LIMITED
    BNP jersey Nominee Company Ltd. EDGARS LIMITED
    BNP Jersey Nominee Company Limited  SAKI FINANCE LIMITED
    BNP JERSEY NOMINEE COMPANY LIMITED  TURF OVERSEAS LIMITED
    BNP Jersey Nominees Company SALLY'S SUNSHINE LTD.
    BNP Paribas Jersey Trust  SALLY'S SUNSHINE LTD.
    BNP Paribas Jersey Nominee Limited  BETHESDA INVESTMENTS S. DE R.L.
    BNP JERSEY TRUST CORPORATION LIMITED  KARLINGTON LIMITED
    BNP JERSEY TRUST CORPORATION LIMITED  TATRON LIMITED
    BNP Paribas (Suisse) SA (which acquired FORTIS BANQUE SUISSE SA by way  ACROSTAK CORPORATION
    BNP PARIBAS JERSEY NOMINEE COMPANY LIMITED  DRAGON STRATEGIC INVESTMENT INC.
    BNP PARIBAS JERSEY NOMINEE COMPANY LIMITED  DRAGON STRATEGIC INVESTMENT INC.
    BNP PARIBAS JERSEY TRUST CORPORATION LIMITED  DRAGON STRATEGIC INVESTMENT INC.
    BGL BNP PARIBAS SOCIETE ANONYME IN THE NOMINEE OF FORTIS LUXEMBOURG VI  DIARIO ASSETS S.A.
    BNP PARIBAS JERSEY TRUST CORPORATION LIMITED  SALCOM ESTATE LTD.
    BNP Paribas Jersey Nominee Company Limited  VELRAY HOLDINGS LIMITED
    BNP Paribas Jersey Nominee Company Limited  ESSVIN STRATEGIC HOLDING CO. LTD.
    BNP Paribas Jersey Nominee Company Limited  DRAGON 228 OVERSEAS CORPORATION
    BNP Paribas Jersey Nominee Company Limited  MANSION HOUSE HOLDINGS LIMITED
    BNP Paribas Jersey Nominee Company Limited  REDWOOD STRATEGIC HOLDINGS LIMITED
    BNP Paribas Jersey Trust Corporation Limited  ESSVIN STRATEGIC HOLDING CO. LTD.
    BNP Paribas Jersey Trust Corporation Limited  DRAGON 228 OVERSEAS CORPORATION
    BNP Paribas Jersey Trust Corporation Limited  MANSION HOUSE HOLDINGS LIMITED
    BNP JERSEY NOMINEE COMPANY LIMITED  TEMPLEMEAD LIMITED
    BNP PARIBAS JERSEY NOMINEE COMPANY LIMITED  SOUND OF LIGHT LIMITED
    BNP PARIBAS JERSEY NOMINEE COMPANY LIMITED  VELVET CREST LIMITED
    BNP Paribas Jersey Nonminees Limited  KINRANDA LIMITED
    BNP Paribas Jersey Nominess Limited KINRANDA LIMITED
    BNP JERSEY NOMINEE CO. LTD  KARLINGTON LIMITED
    BNP JERSEY NOMINEE CO. LTD  TATRON LIMITED
    BNP Paribas Jersey Trust Corporation Limited  TREGARD INTERNATIONAL LTD.
    BNP Paribas Jersey Nominees Limited TREGARD INTERNATIONAL LTD.
    BNP Jersey Trust Corporation Limited  SAKI FINANCE LIMITED
    BNP PARIBAS JERSEY NOMINE COMPANY LIMITED MOLDESTAD HOLDING LIMITED
    BNP Paribas Jersey Trsut Corporation Limited  REDWOOD STRATEGIC HOLDINGS LIMITED
    BNP Paribas Jersey Nominee Company Limited  HALEX INTERNATIONAL LIMITED

7.  Trouver la liste des sociétés dont la juridiction est "France", "Monaco" ou "Réunion".

Requête SQL
    
    .

Réponse obtenue
    
    Aucune d'après question 4 + vérification en filtrant la base de donnée - erreur sur la question ?

8.  Trouver la liste des sociétés dont le pays de l'adresse et le pays de la juridiction sont différents.

Requête SQL
    
    SELECT 
      entity.name,
      entity.jurisdiction,
      address.countries
    FROM entity, address
    WHERE 
      entity.id_address=address.id_address and
      entity.jurisdiction!=address.countries

Réponse obtenue
    
    Big Data Crunchers Ltd. BAH FRA
    TIANSHENG INDUSTRY AND TRADING CO., LTD.  SAM HKG
    NINGBO SUNRISE ENTERPRISES UNITED CO., LTD. SAM HKG
    HOTFOCUS CO., LTD.  SAM HKG
    SKY-BLUE GIFTS & TOYS CO., LTD. SAM HKG
    FORTUNEMAKER INVESTMENTS CORPORATION  SAM HKG
    8808 HOLDING LIMITED  SAM HKG
    KENT DEVELOPMENT LIMITED  SAM HKG
    BONUS TRADE LIMITED SAM HKG
    AMARANDAN LTD.  SAM HKG
    ...    
    ##212821 résultats sur 213570 sans la restriction de différence

9.  Trouver la liste des bénéficiaires qui ont des sociétés au même nom et enregistrée à la même date, trier la liste par odre décroissant.

Requête SQL
    
    SELECT
      officer.name,
      count (*)
    FROM officer, assoc_officer_entity, entity, assoc_entities
    WHERE
      officer.id = assoc_officer_entity.officer and
      assoc_officer_entity.entity = entity.id and
      entity.id = assoc_entities.entity1
    GROUP BY officer.name
    ORDER BY COUNT(officer.name) DESC    

Réponse obtenue
    
    THE BEARER  705
    EL PORTADOR 205
    CHARITABLE AND GOODWILL FOUNDATION  145
    MFM FOUNDATION  60
    ATC ADMINISTRATORS INC. 31
    BROTHERHOOD FOUNDATION  29
    MANSFIELD NOMINEES LIMITED  18
    BLUE SPRUCE FOUNDATION  18
    ATC FOUNDATION  18
    Rosa María Campollo de García 16
    ...
    1204 lignes

10. Donner la liste des intermédiaires qui ont aussi été bénéficiaires, en ajoutant leur nom de bénéficiaire et leur adresse.

Requête SQL (construction)
    
    SELECT
      intermediary.name
      officer.name,
      officer.id,
      assoc_inter_offi.officer,
      assoc_inter_offi.inter,
      intermediary.id,
      intermediary.id_address,
      address.id_address,
      address.address
    FROM officer, assoc_inter_offi, intermediary, address
    WHERE
      officer.id = assoc_inter_offi.officer and
      assoc_inter_offi.inter = intermediary.id and
      intermediary.id_address = address.id_address

Requête SQL (compactée)

    SELECT
      intermediary.name,  
      officer.name,
      address.address
    FROM officer, assoc_inter_offi, intermediary, address
    WHERE
      officer.id = assoc_inter_offi.officer and
      assoc_inter_offi.inter = intermediary.id and
      intermediary.id_address = address.id_address

Réponse obtenue
    
    AFSI  AFSI  AFSI CENTRE DE NEGOCI AVENIDA FITER I ROSELL; 4 BIS ESCALDES-ENGORDANY; ANDORRA
    WEI LAN WEI LAN WEI LAN FLAT D; 37/F.; METRO HARBOUR VIEW; NO. 8 FUK LEE STREET; TAI KOK TSUI; KOWLOON; HONG KONG.
    WANG MIN  WANG MIN  WANG MIN UNIT D; 16/F.; CHEUK NANG PLAZA; 250 HENNESSY ROAD; WANCHAI HONG KONG
    YEN AH KAM EDITH  YEN AH KAM, EDITH YEN AH KAM EDITH ROOM 1202 PACIFIC TRADE CENTRE; 2 KAI HING ROAD; KOWLOON B[...]KOWLOON; HONG KONG S.A.R.
    ZHU BEN FU  ZHU BEN FU  ZHU BEN FU  UNIT #7-606; GUOXINGJIAYUAN; NO. 20  SOUTH CAPITAL GYMNASIUM  ROAD 100044 BEIJING CHINA
    ZHANG NING  ZHANG NING  ROOM 901-902 CITIGROUP TOWER 33 HUA YUAN SHI QIAO ROAD PUDONG NEW AREA  SHANGHAI 200120, CHINA
    WALID MOHAMAD ISSA FATTAH WALID MOHAMAD ISSA FATTAH WALID ISSA FATTAH POLAMAR CALLE VELASQUEZ ENTRE CALLE DIAZ Y SAN RAFAEL 630[...] ISLA MARGARITA VENEZUELA
    WALID MOHAMAD ISSA FATTAH WALID MOHAMAD ISSA FATTAH WALID ISSA FATTAH POLAMAR CALLE VELASQUEZ ENTRE CALLE DIAZ Y SAN RAFAEL 630[...] ISLA MARGARITA VENEZUELA
    ZHANG WEI ZHANG WEI ZHANG WEI 23 BEGONIA PATH; MONTEREY PALM SPRINGS; YUEN LONG; N.T. HK
    TAN KIM WAH TAN KIM WAH TAN KIM WAH 2 LORONG BUKIT PANTAI 4; BUKIT PANTAI; 59100 KUALA LUMPUR; MALAYSIA
    ANGLORE S.A.R.L.  ANGLORE S.A.R.L.  ANGLORE S.A.R.L. RUELLE WILLIAM-MAYOR 2, 3RD FLOOR 2000 NEUCHATEL SWITZERLAND
    BAY TRUST INTERNATIONAL LIMITED BAY TRUST INTERNATIONAL LIMITED BAY TRUST INTERNATIONAL LIMITED P.O. BOX 2130 THE MATALON BUSINESS CENTER 5[...] DRIVE BELIZE CITY BELIZE
    JAMES TURIAN  JAMES TURIAN  JAMES TURIAN NOBLE HOUSE LES BAISSIERES GY1 2UE ST PETER PORT, GUERNSEY UNITED KINGDOM
    JAMES TURIAN  JAMES TURIAN  JAMES TURIAN NOBLE HOUSE LES BAISSIERES GY1 2UE ST PETER PORT, GUERNSEY UNITED KINGDOM

11. Donner le top 10 des bénéficiaires qui ont le plus d'identités différentes (similar name and address) et le nombre d'identités correspondant.

Requête SQL
    
    SELECT
    officer.name,
    count(*)    
    FROM assoc_officers, officer
    WHERE
      assoc_officers.assoc_type = "similar name and address as" and
      assoc_officers.officer1 = officer.id
    GROUP BY assoc_officers.officer1
    ORDER BY COUNT (*) DESC LIMIT 10.

Réponse obtenue
    
    Cannon Asset Management Limited re D001 63
    Cannon Asset Management Limited re V002 61
    Cannon Asset Management Limited re G005 61
    Cannon Asset Management Limited re V008 59
    Cannon Asset Management Limited re S060 58
    Cannon Asset Management Limited re T003 57
    Cannon Asset Management Limited re S014 56
    Cannon Asset Management Limited re I008 56
    Cannon Asset Management  Limited re W003  54
    Cannon Asset Management Limited re F034 54

12. Donner le top 10 des bénéficiaires qui ont le plus de parts toujours valides dans des entreprises offshores (dont la date de fin n'est pas encore passée).

Requête SQL
    
    SELECT
      officer.name,
      count(*)  
    FROM entity, officer, assoc_officer_entity
    WHERE
      officer.id = assoc_officer_entity.officer and
      assoc_officer_entity.entity = entity.id and
      entity.status = "Active"
    GROUP BY officer.id
    ORDER BY COUNT (*) DESC LIMIT 10.

Réponse obtenue

    MOSSFON SUBSCRIBERS LTD.  2111
    BOS NOMINEES (JERSEY) LIMITED 294
    BOS SECRETARIES (JERSEY) LIMITED  284
    MOSTALINA INVESTMENTS S.A 113
    BROCK NOMINEES LIMITED  96
    Dorchester International Inc  95
    Cannon Nominees Limited 93
    INTERCON LIMITED  87
    MAYTREE OVERSEAS S.A. 87
    TENBY NOMINEES LIMITED  82
    

13. Question bonus : réussir à retrouver dans la base au moins 3 personnalités que tu connais

Requête SQL
    
    .

Réponse obtenue
    
    .

